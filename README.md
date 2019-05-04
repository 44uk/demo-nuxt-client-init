# demo-nuxt-client-init

* [potato4d/nuxt\-client\-init\-module: Provide client version of nuxtServerInit](https://github.com/potato4d/nuxt-client-init-module)

NuxtアプリケーションをSPAモードでのビルドに、こちらのモジュールを使わせてもらったところ`created`よりも前のタイミングでの初期化が実現出来なかった。

* [nuxt\-client\-init\-module/module\.plugin\.js at master · potato4d/nuxt\-client\-init\-module](https://github.com/potato4d/nuxt-client-init-module/blob/master/lib/module.plugin.js#L3)

モジュール内部の実装にて`setTimeout`で非同期実行されるため(?)、`mounted`より後のタイミングでの実行になっている様子。

この実装で正しいのかどうかまでが自分には判断できないが、`created`よりも前の時点での初期化という目的を達成するにはこの実装が不要だった。

このリポジトリはその実行順序の検証用です。

<img width="389" alt="demo-nuxt-client-init-log" src="https://user-images.githubusercontent.com/370508/57179771-54f8a880-6ebc-11e9-9254-cd30e4047644.png">

* [demo\-nuxt\-client\-init](https://44uk.github.io/demo-nuxt-client-init/)

必要があればデモサイトでコンソールを開いて確認できます。

