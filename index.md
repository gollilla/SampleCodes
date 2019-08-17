# PMMPのサンプルコード

- Authors  
  - [soradore](https://twitter.com/soradore_)
  - anyone
  - oneone

## 目次
- [PHPの基本](#php-base)
- [PHPの応用](#php-app)
---

### <a name="php-base"></a>PHPの基本  

phpファイルの始まりは  
```PHP
<?php
```
で開始します  

反対に終了する際は  
```
?>
```
で終了します。  
一般的にはPMMPのプラグインのようなPHPしか(HTMLなどを)記述しない場合は省略することになっています

変数とは何かを入れるための箱と置くことができます。  
PHPでの変数は  
```PHP
<?php
$hoge = 1;
$huga = "aaa";
```
のように $ マークを用いて表現されます。
