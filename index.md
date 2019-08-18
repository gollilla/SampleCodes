# PMMPのサンプルコード

- Authors  
  - [soradore](https://twitter.com/soradore_)
  - anyone
  - oneone

## <a name="tab-con"></a>目次
- [PHPの基本](#php-base)
- [PHPの応用](#php-app)
- [よくあるエラーと解決方法](#err-res)

---

### <a name="php-base"></a>PHPの基本  

phpファイルの始まりは  
```php
<?php
```
で開始します。  

反対に終了する際は  
```
?>
```
で終了します。  
一般的にはPMMPのプラグインのようなPHPしか(HTMLなどを)記述しない場合は省略することになっています。

変数とは何かを入れるための箱と置くことができます。  
PHPでの変数は  
```php
<?php
$hoge = 1;
$huga = "aaa";
```
のように $ マークを用いて表現されます。  

PHPでは関数を定義して使うことができます。  
関数の定義には function を利用します。  
```php
<?php
function 関数名($引数){
    $引数;
}

function hoge($a){
    echo $a;
}

hoge("hoge!!");
```
関数 hoge(); を実行すると引数に渡された値が表示されます。  

引数とは関数に渡す変数のことです。  
先ほど出てきた `"hoge!!"`　が引数に当たります。  
つまり関数 `hoge("hoge!!");`　を実行すると `hoge!!` と表示されるわけです。  
引数は複数渡すことができます。  
```php
<?php
function hoge2($a,$b){
    echo $a,$b;
}
hoge("hoge", "huga");
```  

<=[目次に戻る](#tab-con)  

### <a name="php-app"></a>PHPの応用  

ほかのプログラミング言語と同様にPHPにも型と呼ばれるものがあります。  
PHPの型は  

- Array 配列
- String 文字列
- Int 整数
- Float 浮動小数点数
- Boolean 論理型

等があります。  


### <a name="err-res"></a>よくあるエラーと解決方法  

#### ケース1

```
[Server thread/CRITICAL]: ParseError: "syntax error, unexpected end of file, expecting function (T_FUNCTION) or const (T_CONST)" (EXCEPTION) in "plugins/~/src/soradore/~/main" at line ○○
```
エラー原因 : }が閉じ忘れていた  

解決方法 :  
 {} のペアを確認する。  
 インデントを行う。  
 高機能テキストエディタを使うと自動でつけてくれるものもあるので、活用しましょう。

#### ケース2

文法的には間違っていないのになぜかエラーが出る!! というときには  
空白文字に全角スペースが入っているかもしれません。テキストエディタの検索で全角スペースを入力して検索してみましょう。  
メッセージなどで日本語を入力したあと半角に戻し忘れていることがあります。日本語入力の周りを注意してみましょう。  
またファイルを保存する際に文字コードの指定はBOMなしのUTF-8Nを選択しましょう。  
BOMありにしてしまうと、同様にエラーの原因になりえます。

#### ケース3

