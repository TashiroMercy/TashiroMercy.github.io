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

    1．「File」→「New」→「Maven Project」
    ![01](../image/01.png)

    2．「New Maven Project」ポップアップよりロケーションを選択して「Next」
    ![02](../image/02.png)

    3．archetypeを選択して「Next」
    ![03](../image/03.png)

    4．「Group Id」、「Artifact Id」を設定して「Next」
    ![04](../image/04.png)

    5． プロジェクトのテンプレートが作成される
    ![05](../image/05.png)
  
  ****
* warファイル作成

    1． プロジェクトのコンテキストメニュー→「Run As」→「Maven Install」
    ![06](../image/06.png)

    2． 「target」ディレクトリにwarファイルが作成される
    ![07](../image/07.png)
  ****
* プロジェクトをクリーン (生成したファイルを削除)

    1． プロジェクトのコンテキストメニュー→「Run As」→「Maven Clean」
    ![08](../image/08.png)

    2． 「target」ディレクトリの生成したファイルが削除される
    ![09](../image/09.png)
  ****
* ライブラリの追加

  ※例として「Spring Boot Web Starter」の追加を行います

    1． Pacage Explorerより「Maven Dependencies」を確認
    ![10](../image/10.png)
    デフォルトでjunitのjarが設定されている

    2． プロジェクト直下のpom.xmlを編集する
    ![11](../image/11.png)
    ※入力内容は[Mavenリポジトリ](https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-web/1.4.0.RELEASE)よりコピーする

    3． 追加されたライブラリの確認
    ![12](../image/12.png)
    「Spring Boot Web Starter」に依存関係があるライブラリが追加されている

  ****

