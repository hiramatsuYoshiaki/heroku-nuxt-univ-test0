# heroku-nuxt-univ-test0

> My majestic Nuxt.js project

## Nuxtアプリを作成

``` bash
# install dependencies
$ npx create-nuxt-app heroku-nuxt-univ-test0
? Project name heroku-nuxt-univ-test0
? Project description My majestic Nuxt.js project
? Use a custom server framework express
? Choose features to install Axios
? Use a custom UI framework none
? Use a custom test framework none
? Choose rendering mode Universal
? Author name hiramatsu
? Choose a package manager npm
$ cd heroku-nuxt-univ-test0
# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, checkout [Nuxt.js docs](https://nuxtjs.org).

## herokuアプリを作成
1.Herokuでアプリケーションを作成します。 
 
これは、Herokuがソースコードを受け取る準備をするためのものです。 
アプリを作成すると、git remote（と呼ばれるheroku）も作成され、 
ローカルのgitリポジトリに関連付けられます。 
```
$ cd heroku-nuxt-univ-test0
$ heroku create heroku-nuxt-univ-test0
Creating heroku-nuxt-univ-test0... done, stack is heroku-18
http://heroku-nuxt-univ-test0.herokuapp.com/ | https://git.heroku.com/heroku-nuxt-univ-test0.git
Git remote heroku added
```
2. npm run build を実行できるようにするために、Heroku にプロジェクトの devDependencies をインストールすることを伝える必要があります 

```
$ heroku config:set NPM_CONFIG_PRODUCTION=false
```

3. アプリケーションにホスト 0.0.0.0 を listen させプロダクションモードで起動します 
```
$ heroku config:set HOST=0.0.0.0
$ heroku config:set NODE_ENV=production
```

4. package.json 内の heroku-postbuild スクリプトを使って、Heroku に npm run build を実行するよう伝えます
```
"scripts": {
  "dev": "nuxt",
  "build": "nuxt build",
  "start": "nuxt start",
  "heroku-postbuild": "npm run build"//追記
}
```

5. ルートディレクトリにProcfile (ファイル拡張子を付けずにファイル名を Procfile という名前にします）を新規作成し、procfileに、Herokuで使われるアプリの dyno によってアプリケーションを起動するために実行するコマンドを記入します。

```
web: npm run start
```

4. Heroku に git push します
```
$ git add .
$ git commit
$ git push heroku master
```

5. Heroku でホストされていることを確認　
```
$ heroku open
```


## Node.jsを使ってHerokuを始めよう 
https://devcenter.heroku.com/articles/getting-started-with-nodejs

## url
https://dashboard.heroku.com/apps/heroku-nuxt-univ-test0
