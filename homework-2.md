# 1.Exploring possible queries,search and reports

select c.name, p.purchase_dt, pr.name from Customers c \
left join Purchases p on c.id = p.customer_id \
left join Products pr on p.product_id = pr.id \
where c.name = "Sidorov"

select from products p \
inner join prices pr on p.id = pr.product_id  \
where pr.change_dt = "mm.dd.yyyy" and pr.price > 1000 

select s.adress, p.name ,dl.name from Delivers d \
left join Products p on d.product_id \
left join Stores s on d.store_id = s.id \
left join Dilers dl on d.id = d.diler_id = dl.id \
where p.name like "%paper%" and deliver_date = "dd.mm.yyyy" \
and s.adress like "%проспект%" 

# Cardinality

prices , product_name, deliver_date - high cardinality

# Indexes 

CREATE INDEX idex_customer \
ON Customers (name);  

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




