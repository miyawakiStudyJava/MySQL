はじめに
新規ユーザーを作成して権限を付与。

```Console
create user test@localhost identified by 'test';
grant all on test.* to kitsune@localhost;
ALTER USER 'test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'test';

//認証方式の確認
SELECT user, host, plugin FROM mysql.user;

//権限確認
show grants for@localhost¥G
```

javaと連携
```Java
package dbSample;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class DbConnectSampl01 {

	public static void main(String[] args) {
		//import java.sql.Connection;
		Connection con = null;
		Statement stmt = null;
		ResultSet rs = null;

		try {
			// 1. ドライバのクラスをJava上で読み込む
			Class.forName("com.mysql.jdbc.Driver");

			// 2. DBと接続する
			con = DriverManager.getConnection(
					"jdbc:mysql://localhost/world?useSSL=false",
					"test",
					"test");
			// 3. DBとやりとりする窓口（Statementオブジェクト）の作成
			stmt = con.createStatement();

			// 4, 5. Select文の実行と結果を格納／代入
			String sql = "select * from country limit 50";
			rs = stmt.executeQuery(sql);

			// 6. 結果を表示する
			while(rs.next()) {
				//Name列の値を取得
				String name = rs.getString("Name");
				System.out.println(name);
			}

		} catch (ClassNotFoundException e) {
			// TODO 自動生成された catch ブロック
			System.err.println("JDBCのドライバのロードに失敗しました。");
			e.printStackTrace();
		} catch (SQLException e) {
			System.err.println("データベースに異常が発生しました。");
			e.printStackTrace();
		} finally {
			// 7. 接続を閉じる
			if (rs != null) {
				try {
					rs.close();
				} catch (SQLException e) {
					System.err.println("データベース切断時にエラーが発生しました。");
					e.printStackTrace();
				}
			}
			if (stmt != null) {
				try {
					stmt.close();
				} catch (SQLException e) {
					System.err.println("データベース切断時にエラーが発生しました。");
					e.printStackTrace();
				}
			}
			if (con != null) {
				try {
					con.close();
				} catch (SQLException e) {
					System.err.println("データベース切断時にエラーが発生しました。");
					e.printStackTrace();
				}
			}
		}
	}

}

```






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
