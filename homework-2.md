g

CREATE INDEX idex_store_adress   
ON Stores(adress); 

if product price cardinality > date cardinality

CREATE INDEX idex_price_date   
ON Products (price, change_dt);  

# Constraints

price must be more than 0

CREATE TABLE "public.Prices" ( \
   "id" serial(8) NOT NULL, \
	"product_id" integer(8) NOT NULL, \
	"change_date" TIMESTAMP, \
	"price" DECIMAL check ( price > 0.0 ) , \
	CONSTRAINT "Prices_pk" PRIMARY KEY ("id") \
)




