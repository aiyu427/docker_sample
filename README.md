# docker_sample

https://qiita.com/at-946/items/08de3c9d7611f62b1894

1. docker準備
```
$ docker-compose build
```

2. Nuxt.js作成

cloneしてきた直後もやつ

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

作成するときに必要なだけでcloneしてきた場合には不要

```
$ docker-compose run --rm api rails new . -f -d postgresql --api
```

以下は必要

```
$ docker-compose build api
$ docker-compose run --rm api rails db:create
$ docker-compose run --rm api rails g scaffold user name:string
$ docker-compose run --rm api rails db:migrate
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
