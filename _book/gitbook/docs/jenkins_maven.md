# jenkinsジョブ設定
****
### MavenプロジェクトBuild

  1. 新規ジョブ作成

    ジョブ名を入力して「Mavenプロジェクトのビルド」を選択
    ![maven_build](image/maven_build.png)
  1. ソースコード管理

    対象のソース管理ツール設定を定義

  1. ビルド
    ![maven_build2](image/maven_build2.png)
    ゴールとオプションには対象のMavenコマンドとオプションを指定

  1. ビルド後の処理

    warファイルを保管する
    ![maven_build3](image/maven_build3.png)

  ****
### GradleプロジェクトBuild

1. 新規ジョブ作成

  ジョブ名を入力して「フリースタイルプロジェクトのビルド」を選択
  ![gradle_build](image/gradle_build.png)
1. ソースコード管理

  対象のソース管理ツール設定を定義

1. ビルド

  invoke Gradle scriptを選択
  ![gradle_build2](image/gradle_build2.png)
  Tasksに対象のGradleコマンドとオプションを指定

1. ビルド後の処理

  warファイルを保管する
