はじめに


```console
cd c:\Program Files\MySQL Server 8.0\bin
"mysql" -u root -p

Enter password:**** < test
```

```SQL
//データベース作成
create ec_site;

//データベースを表示
show tables;

//データベース削除のSQL文
drop database ec_site;

//選択
use database ec_site;

//テーブル作成
create table items(
  item_id INT,
  name VARCHAR(255),
  price INT
 );

//テーブルの構成確認
desc items;

//コメントも含めたテーブルの構成確認
desc full columns from items;
```


第1章　イントロダクション

第2章　SQLの基礎

第3章　構成の追加変更

第4章　もう一歩進んでみる

第5章　CSV操作しよう
