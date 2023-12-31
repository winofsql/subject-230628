6# subject-230628

- ## 元となるソリューションを GitHub からダウンロード
  - [cs-form-mtn-012-vs2022](https://github.com/winofsql/cs-form-mtn-012-vs2022)
- ## 解凍するのみで、ソリューションは開かないでください
  - 中の定義ファイルとソースコードの **namespace** を pg学籍番号 に さくらエディタで変更します\
  ![image](https://github.com/winofsql/subject-230628/assets/1501327/ec4f5a8e-2935-4271-b9cd-8f90cad87bc6)\
  ![image](https://github.com/winofsql/subject-230628/assets/1501327/c3cf6cc5-02fd-413c-ad8f-3171c280adf8)

  ※ Winキー + V をうまく使う

- ## 定義ファイル名に含まれるソリューション名部分を pg学籍番号 に変更
  ![image](https://github.com/winofsql/subject-230628/assets/1501327/26630f4e-cb25-400d-b6c9-4712ff333a10)

- ## Visual Studio 2022 で開く( pg学籍番号.sln )
  - 入れ子の設定を WEB に変更\
  ![image](https://github.com/winofsql/subject-230628/assets/1501327/9b256a0e-9352-44e9-933a-7169d4aedfbb)\
  ![image](https://github.com/winofsql/subject-230628/assets/1501327/28efe936-6f16-4658-badc-5db4a343ae6e)

- ## XAMPP を起動して MySQL を動かしてください
  - 社員マスタで動く事を確認します
  - オリジナルマスタの Create 文でテーブルを作成
  - コンボボックス参照用のオリジナル名称マスタを Create 文を作成
  - 参照用のオリジナル名称マスタを登録\
  ![image](https://github.com/winofsql/subject-230628/assets/1501327/d06f9dac-6b8d-4466-8a64-dd88ca9b477a)

- ## プログラム内のコントロールの名前等をオリジナルマスタの内容に変更する
  - ラベルの表記の変更\
  ![image](https://github.com/winofsql/subject-230628/assets/1501327/1ab6e533-0158-43c7-9fc7-8a2acf73aa45)\
  - コントロールの名称変更
  - イベントメソッドの名称変更
  - Form1.Designer.cs 内のエラー部分の変更

- ## SQL の変更
  - select 文の変更
  - insert 文の変更
```cs
 strQuery = @$"insert into `アニメマスタ` (
	`アニメコード` 
	,`アニメ作品タイトル` 
    ,`アニメ分類`
	,`放映回数` 
	,`初回放映開始日` 
)
 values(
	'{this.アニメコード.Text}'
	,'{this.アニメ作品タイトル.Text}'
	,{((ComboData)this.アニメ分類.SelectedItem).Data}
	,{this.放映回数.Text}
	,'{this.初回放映開始日.Value:yyyy/MM/dd}'
)";
```

- ## 固定の分類をコンボボックスに入力
	- Form1_Load の内容を変更
```cs
this.アニメ分類.Items.Clear();
this.アニメ分類.Items.Add(new ComboData("SF", "0"));
this.アニメ分類.Items.Add(new ComboData("ファンタジー", "1"));
this.アニメ分類.Items.Add(new ComboData("ドラマ", "2"));
this.アニメ分類.SelectedIndex = 0;
```
