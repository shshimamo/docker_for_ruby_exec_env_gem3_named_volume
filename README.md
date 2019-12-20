# docker_for_ruby_exec_env_gem3_named_volume
The third way to manage gems with Docker(named volume)

volumesにbundlerでインストールされるgemを格納することでgemを共有できる

(確認方法)
まずイメージを作成
```
docker-compose build
```

コンテナ上でbashを起動し
```
docker-compose run --rm app bash
```
gemを追加する
```
bundle add sinatra-contrib --version '~> 2.0.5'
```

ホストに戻り再度bashを起動する
```
docker-compose run --rm app bash
```
ここで足りないgemに対してbundle installが実行される

別のターミナルで以下を実行するとbundle installが実行されず
他のコンテナとgemを共有できていることがわかる
```
docker-compose run --rm app bash
```
