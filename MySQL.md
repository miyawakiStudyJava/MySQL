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

//データの更新
update ec_site set price = 100 where item_id=1;


```


デフォルト値の設定
```SQL
create table items(
item_id INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
name VARCHAR(255) DEFAULT NULL,
price INT DEFAULT 0
)ENGINE=MyISAM;
```

AUTO_INCREMENT 自動で数値が増える
NOT NULL
PRIMARY KEY

バルクインサート
```SQL
INSERT INTO sales(item_id, customer_id, num, insert_datetime) VALUES(2,3,1,'2019-05-01 10:00:00'),
(1,3,1,'2019-05-01 10:00:00'),
(2,3,1,'2019-05-01 10:00:00'),
(3,1,1,'2019-05-01 10:00:00'),
(1,3,4,'2019-05-01 10:00:00'),
(2,1,1,'2019-05-01 10:00:00');
```

パターンマッチング（LIKE演算子）
