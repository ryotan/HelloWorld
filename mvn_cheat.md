# Mavenチートシート的な何か

## ライフサイクル編
<!-- アーキタイプからmavenプロジェクトを作成
: `mvn archetype:generqate`

| パラメータ名 | 内容 |
|:-|:-|
| modelversion | POMのバージョン |
| groupId| プロジェクトのルートパッケージ名|
| artifactId|JARファイルの名前等に使用|
| version|バージョン情報|
| package|com.example(例)| -->

プロジェクトのコンパイル
: `mvn compile`

テスト用ファイルのコンパイル
: `mvn test-compile`

ユニットテストの実行
: `mvn test`

JARファイルの作成
: `mvn package`

パッケージの静的解析(checkstyle,findbugs等)
: `mvn verify`

他プロジェクトから成果物を参照可能にする
: `mvn install`

リモートリポジトリへデプロイ[^1]
: `mvn deploy`

targetディレクトリを削除[^2]
: `mvn clean`

## 開発編
アプリを実行する
: `mvn jetty:run`


## ドキュメント作成編
javadocの作成
: `mvn javadoc:javadoc`

## mavenの設定/確認編
ヘルプの表示
: `mvn -h`

<!-- 設定値の出力
： `mvn help:effective-pom`

ファイルに出力
: `mvn help:effective-pom -Doutput=***.xml` -->

依存関係を出力する
: `mvn dependency:tree`

システムプロパティを設定
: `mvn -D{key}={value}`

## IDE(Eclipse)連携編
Eclipse形式のフォルダ構成に変換
: `mvn eclipse:eclipse`

MavenプロジェクトをEclipseに取り込む
: `File -> Import -> Existing Maven project`

pom.xmlの変更を取り込む
: `プロジェクトを右クリック -> Maven -> Update Project`

## IDE(IntelliJ)連携編
IntelliJ形式のフォルダ構成に変換
: `mvn idea:idea`

## プロファイルの有効化・無効化編
プロファイルを有効にする
: `mvn -P {プロファイル名} {ゴール}`

プロファイルを無効にする
: `mvn -P !{プロファイル名} {ゴール}`

プロファイル指定なしで実行する
: `mvn antrun:run`

デフォルトで有効なプロファイルを設定する
:
```xml:pom.xml
<profiles>
  <profile>
    <id>en</id>
    <activation>
      <activeByDefault>true</activeByDefault>
    </activation>
    <properties>
      <プロパティ名>プロパティ値</プロパティ名>
    </properties>
  </profile>
</profiles>
```

有効なプロパティを確認する
: `mvn help:all-profiles`

## トラブルシューティング編
#### dependency関連のトラブル
ライブラリを最新のものに更新
: `mvn -U compile`

ローカルからjarを削除
: `rm ~/.m2/repository/junit/junit/3.8.1/*`

ローカルにmvn install [^3]
: `mvn install:install-file -Dfile=<ファイル>`

<!-- ## pom.xml編
以下の値を`${プロパティ名}`でpom.xml内に記述出来る

| プロパティ名| デフォルト値|
|:-|:-|
| project.build.directory|target|
| project.build.outputDirectory|target/classes|
| project.build.testOutputDirectory|target/test-classes|
| project.compileSourceRoots|src/main/java|
| project.testCompileSourceRoots|src/test/java|
| env.{環境変数名}|任意の環境変数|
[pom.xmlの各要素デフォルト値と変数置換について](http://qiita.com/kozy4324/items/9a5976d9d264be1ef90e)

ユーザ定義プロパティを設定する



```xml:pom.xml
<properties>
  <プロパティ名>プロパティ値</プロパティ名>
</properties>
```

他のpomを継承する

```xml:pom.xml
<parent>
  <groupId>グループID</groupId>
  <artifactId>アーティファクトID</artifactId>
  <version>バージョン</version>
  <relativePath>../parent/</relativePath>
</parent>
```

## マルチモジュール編
プロジェクトのモジュールを作成する
: `プロジェクトのルートディレクトリで新たにプロジェクトを作成` -->


[^1]: リモートリポジトリの情報はpom.xmlに記述
[^2]: 「compile」「test-compile」「test」「package」等を実行する前には実行する必要がある
[^3]: wgetでjarとpomをリモートから取得し、手動でインストール。その際は-DpomFile=***.pomも付け加える
