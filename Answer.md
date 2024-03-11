<1> The "Product" entity has a field called "category_id," which acts as a foreign key to the table "Product_catagory". This means it references the "Product_Category" entity. In simpler terms, each product is assigned to a category, and this connection is established through the "category_id" field, which points to the corresponding category in the "Product_Category" entity. So, a product belongs to a specific category, and this relationship is maintained through the foreign key.


<2>each product in the "Product" table has a valid category assigned to it by setting up a foreign key constraint between the "category_id" column in the "Product" table and the primary key column in the "Category" table. This constraint will ensure that any value entered into the "category_id" column of the "Product" table must exist in the "id" column of the "Category" table.

SELECT category_id
FROM Product
WHERE category_id IN (SELECT id FROM Category);
