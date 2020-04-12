# docker_sample

https://qiita.com/at-946/items/08de3c9d7611f62b1894

1. docker準備
```
$ docker-compose build
```

2. Nuxt.js作成
```
docker-compose run --rm front npx create-nuxt-app

? Choose the package manager     --> Npm
? Choose Nuxt.js modules         --> Axios
? Choose rendering mode          --> Universal (SSR)
```
Axiosを選択するのを忘れずに
```
$ docker-compose up front
```

3. Railsの準備

```
$ docker-compose run --rm api rails new . -f -d postgresql --api
```

```
$ docker-compose build back
$ docker-compose run --rm back rails db:create
$ docker-compose run --rm back rails g scaffold user name:string
$ docker-compose run --rm back rails db:migrate
```

```
$ docker-compose up -d api
```

4. NuxtとRails合体

docker-compose.ymlから
・apiのportsを消す
・frontのdepends_onを追加

```
$ docker-compose up
```

# docker_sample
