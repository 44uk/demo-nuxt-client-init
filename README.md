# demo-nuxt-client-init

* [potato4d/nuxt\-client\-init\-module: Provide client version of nuxtServerInit](https://github.com/potato4d/nuxt-client-init-module)

NuxtアプリケーションをSPAモードでのビルドに、こちらのモジュールを使わせてもらったところ`created`よりも前のタイミングでの初期化が実現出来なかった。

* [nuxt\-client\-init\-module/module\.plugin\.js at master · potato4d/nuxt\-client\-init\-module](https://github.com/potato4d/nuxt-client-init-module/blob/master/lib/module.plugin.js#L3)

モジュール内部の実装にて`setTimeout`で非同期実行されるため(?)、`mounted`より後のタイミングでの実行になっている様子。

* [Delay exec nuxtClientInit · potato4d/nuxt\-client\-init\-module@59989ef](https://github.com/potato4d/nuxt-client-init-module/commit/59989ef37176586aa7ffec0ede0c64cf5aacb8fa#diff-e5071b7e59a73723f3f847f15c430645)

コミットを遡ると途中でこの修正が施された様子でした。

この実装で正しいのかは自分には判断できませんでしたが、
`created`よりも前の時点での初期化という目的を達成するにはこの実装が不要でした。

このリポジトリはその実行順序の検証用です。

<img width="389" alt="demo-nuxt-client-init-log" src="https://user-images.githubusercontent.com/370508/57179771-54f8a880-6ebc-11e9-9254-cd30e4047644.png">

* [demo\-nuxt\-client\-init](https://44uk.github.io/demo-nuxt-client-init/)

必要があればデモサイトでコンソールを開いて確認できます。

