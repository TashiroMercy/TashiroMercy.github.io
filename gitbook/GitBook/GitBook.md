# GitBook
****
### GitBookとは
markdownで書いたドキュメントをhtmlやpdfなどで読みやすい形式に変換をかける機能を提供してくれるコマンドラインツールです。
****
### インストール
1. node.jsインストール

    GitBookインストールにはnpmを使用する必要がある為、[node.js](https://nodejs.org/en/)をインストール。

1. GitBookインストール

    以下コマンドを実行する

    ```MarkDown
    npm install -g gitbook-cli
    ```
****
### GitBookコマンド
<<<<<<< HEAD
1. 雛形ファイル生成   
雛形ファイルが生成される。
```MarkDown
gitbook init
```  
　  
2. ビルド   
MarkDownで記述したファイルがビルドされる。
```MarkDown
gitbook build
```
　  
3. ローカルサーバー起動   
ローカルサーバーが立ち上がります。
```MarkDown
gitbook serve
```
![01](../image/GitBook/01.png)
<BR>`http://localhost:4000`にて確認可能。    
![03](../image/GitBook/03.png)

4. PDF出力   
PDFファイルが生成される。   
※calibreをインストールする必要があります。
```MarkDown
gitbook pdf
```   
![04](../image/GitBook/04.png)
=======
1. gitbook init

   雛形ファイルが生成される。<Br>

2. gitbook build

   MarkDownで記述したファイルがビルドされる。<Br>
   ![01](../image/GitBook/01.png)

3. gitbook serve

    ローカルサーバーが立ち上がります。<Br>
    ![02](../image/GitBook/02.png)

    `http://localhost:4000`にて確認可能。<Br>
    ![03](../image/GitBook/03.png)
>>>>>>> 45a2832cf83cf2e032e2c7793519fdd7f9cee609
