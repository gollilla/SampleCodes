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

引数とは関数に渡す値のことです。  
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
- Integer 整数
- Float 浮動小数点数
- Boolean 論理型

等があります。  

Array 配列は複数の値をいっぺんに扱うときに使用します。  
配列の作り方は  
```php
<?php

$a = [1,2,4];
```
のように `[]` で囲むことで表現します。  
すこし古い表現ですが 
```php
<?php

$a = array(1,2,4,5);
```
としても同じです。  
配列のそれぞれの値にはキーと呼ばれるものを用いてアクセスします。  
キーは配列値に順番で で自分で指定しない限り 0 から自動で当てはめられます。  
上の例では `$a[0]` には 1 が  
`$a[1]` には 2 がという風にアクセスすることができます。

PHPでは連想配列といった キーに数字だけではなく、独自の名前を付けて値を対応させる配列を使うことができます。  
```php
<?php

$a = ["aa"=>123, "bbb"=>456];
```
のように `キー => 値 ` の形で表現します。

PMMPでの主な使われ方としてPlayerを管理するために配列が用いられています。  
またPvPなどのチーム機能を実現するために配列が使われることがあります。  
以下はチームの例です。  
```php
<?php
$team['red'] = []; //赤チーム
$team['red'][] = $player;
$team['blue'] = []; //青チーム
$team['blue'][] = $player2;
```
実際にはプラグインではクラス内で使うことが多いので配列はメンバー変数で扱われます。  


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
他にも文字列の ' や " を　’ や ”　にしてしまったりしているとエラーになります。

#### ケース3

```
PHP Fatal error:  Uncaught Error: Call to a member function function() on null in "/~/~/main" at line ○○
```
エラー原因 : Nullに対して関数を呼び出していた。
例として
```php
$player->getName();
//表向きはこうだが中身は実は
(NULL)->getName();
```
となっていた場合、NULLなのに関数呼び出せないよ!!!ということでエラーが出てしまいます。
