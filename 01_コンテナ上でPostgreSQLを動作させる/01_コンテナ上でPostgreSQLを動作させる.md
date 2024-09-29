# PostgreSQLとは
リレーショナルデータベース (RDBMS)
ACID準拠のトランザクション処理、強力なSQLサポート、スキーマによるデータ整合性の維持、JSONデータ型のサポート
データの型を厳しく定義し堅牢性を高める点に強み
データの整合性を保つための機能が豊富


# 01_コンテナ上でPostgreSQLを動作させる
docker-compose up -d
docker exec -it postgres_db psql -U myuser -d mydb

# 以下でDBに入る
psql (17.0 (Debian 17.0-1.pgdg120+1))
Type "help" for help.

mydb=#

# データベースにデータを入れる
CREATE SCHEMA myschema;

CREATE TABLE myschema.mytable (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

INSERT INTO myschema.mytable (name, age) VALUES ('data base', 30);

# データを確認
SELECT * FROM myschema.mytable;

# 例：都道府県の分類
CREATE SCHEMA japan;

CREATE TABLE japan.prefectures (
    id SERIAL PRIMARY KEY,
    prefecture_name VARCHAR(50),
    region VARCHAR(50)
);

INSERT INTO japan.prefectures (prefecture_name, region) VALUES
('北海道', '北海道地方'),
('青森県', '東北地方'),
('岩手県', '東北地方'),
('宮城県', '東北地方'),
('秋田県', '東北地方'),
('山形県', '東北地方'),
('福島県', '東北地方'),
('茨城県', '関東地方'),
('栃木県', '関東地方'),
('群馬県', '関東地方'),
('埼玉県', '関東地方'),
('千葉県', '関東地方'),
('東京都', '関東地方'),
('神奈川県', '関東地方'),
('新潟県', '中部地方'),
('富山県', '中部地方'),
('石川県', '中部地方'),
('福井県', '中部地方'),
('山梨県', '中部地方'),
('長野県', '中部地方'),
('岐阜県', '中部地方'),
('静岡県', '中部地方'),
('愛知県', '中部地方'),
('三重県', '近畿地方'),
('滋賀県', '近畿地方'),
('京都府', '近畿地方'),
('大阪府', '近畿地方'),
('兵庫県', '近畿地方'),
('奈良県', '近畿地方'),
('和歌山県', '近畿地方'),
('鳥取県', '中国地方'),
('島根県', '中国地方'),
('岡山県', '中国地方'),
('広島県', '中国地方'),
('山口県', '中国地方'),
('徳島県', '四国地方'),
('香川県', '四国地方'),
('愛媛県', '四国地方'),
('高知県', '四国地方'),
('福岡県', '九州地方・沖縄地方'),
('佐賀県', '九州地方・沖縄地方'),
('長崎県', '九州地方・沖縄地方'),
('熊本県', '九州地方・沖縄地方'),
('大分県', '九州地方・沖縄地方'),
('宮崎県', '九州地方・沖縄地方'),
('鹿児島県', '九州地方・沖縄地方'),
('沖縄県', '九州地方・沖縄地方');


# データを確認
SELECT * FROM japan.prefectures;

SELECT * FROM japan.prefectures WHERE region = '東北地方';
