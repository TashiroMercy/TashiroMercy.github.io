# Maven
****
### Mavenとは

  Java用プロジェクト管理ツールで、Apache Antに代わるものとして作られた。Apacheライセンスにて配布されているオープンソースソフトウェアである。
****
### 主な機能

* プロジェクトの依存するライブラリの管理
* プロジェクトの作成やコンパイルなどの各タスクの支援
****
### EclipseからのMavenの利用

* プロジェクト作成

  1． 「File」→「New」→「Maven Project」
  ![01](image/01.png)

  1． ディフォルトのまま「Next」
  ![02](image/02.png)

  1． 「maven-archetype-webapp」を選択して「Next」
  ![03](image/03.png)

  1． 「Group Id」、「Artifact Id」を設定して「Next」
  ![04](image/04.png)

  1． プロジェクトのテンプレートが作成される
  ![05](image/05.png)
  ****
* warファイル作成

  1． プロジェクトのコンテキストメニュー→「Run As」→「Maven Install」
  ![06](image/06.png)

  1． 「target」ディレクトリにwarファイルが作成される
  ![07](image/07.png)
  ****
* プロジェクトをクリーン (生成したファイルを削除)

  1． プロジェクトのコンテキストメニュー→「Run As」→「Maven Clean」
  ![08](image/08.png)

  1． 「target」ディレクトリの生成したファイルが削除される
  ![09](image/09.png)
  ****
