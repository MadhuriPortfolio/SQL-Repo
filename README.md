# SQL-Repo
This SQL repository contains a collection of scripts and queries designed for data manipulation, analysis, and database management

Project 1: This is work that I did in MySQL during my Data Technician Skills Bootcamp.
This work used the world_db dataset embedded in this SQL file: world_db.sql   
* **Count cities in USA**    
![image](https://github.com/user-attachments/assets/3d5bfaa3-9e35-4e93-b531-6e9381dbc555)

* **Country with Highest Life Expectancy**    
![image](https://github.com/user-attachments/assets/3923b402-d40d-404c-b97c-e8367bbba5d6)

* **New Year Promotion: Featuring Cities**    
![image](https://github.com/user-attachments/assets/e3005169-5f3b-4548-a195-86d8b840d303)

* Display Columns with Limit (First 10 Row**     
![image](https://github.com/user-attachments/assets/fc5d3f98-3c36-4baf-a7ef-f8c73e12cb92)

* **Cities with Population Larger than 2,000,000**    
![image](https://github.com/user-attachments/assets/0fc6efb7-07bd-447a-a0c4-b868a8ddad0d)

* **Cities with Population Between 500,000-1,000,000**   
![image](https://github.com/user-attachments/assets/f2c69d7a-d1a8-4cab-9098-36aec174ce91)  

* **Most Populated City**    
![image](https://github.com/user-attachments/assets/4b829c69-09bc-4a3e-a867-3c218428e914)  

***Project2:*** 
Other Data set examples i worked with are Pizza details from the data sets :  Pizza_order_details.csv    Pizza_orders.csv     Pizza_types.csv    pizzas.csv 
*	**Query The Total Number Of Orders Placed?**   
SELECT COUNT(order_id) AS total_orders FROM pizza_orders;
<img src="https://github.com/user-attachments/assets/a206f0c5-c1a0-4c36-96c9-fd84492c4898" alt="Description of the Image" width="700" height="300" />
 
* **Query The Total Number Of Pizza Id Types?**    
SELECT COUNT(pizza_id) AS total_pizza_types FROM pizzas;
<img src="https://github.com/user-attachments/assets/8dcd15a3-148e-45ca-95ec-baa80e14b225" alt="Description of the Image" width="700" height="300" />
 
* **Query The Total Number Of Pizza Types?** 
SELECT COUNT(DISTINCT pizza_type_id) AS total_pizza_types FROM pizza_types;
<img src="https://github.com/user-attachments/assets/50d473fd-2bca-4696-ad5f-86a26026863b" alt="Description of the Image" width="700" height="300" />
 
* **Query Total Order Quantity Placed?**  
SELECT SUM(quantity) AS total_order_quantity FROM pizza_order_details;
<img src="https://github.com/user-attachments/assets/5186f996-e449-4f76-83e5-eace66722a8e" alt="Description of the Image" width="700" height="300" />

* **Query The First Date Of Transaction And Last Date Of Transaction?**  
SELECT MIN(date) AS first_transaction_date, MAX(date) AS last_transaction_date FROM pizza_orders;  
<img src="https://github.com/user-attachments/assets/215cb0b3-8834-446d-87d6-97f127ed770e" alt="Description of the Image" width="700" height="300" />

 * **Query The Total Revenue Generated ?**    
  SELECT SUM(POD.quantity * PIZ.price) AS total_revenue FROM pizza_order_details POD JOIN pizzas PIZ ON POD.pizza_id =  PIZ.pizza_id;
<img src="https://github.com/user-attachments/assets/1928b4e5-a791-406b-83d3-c3fcfdd7ec9a" alt="Description of the Image" width="700" height="300" />

* **Query The Lowest Priced Pizza? (Display Pizza Name, Price)**     
      SELECT PT.name AS pizza_name, PIZ.price FROM pizzas PIZ  
      JOIN pizza_types PT ON PIZ.pizza_type_id = PT.pizza_type_id  
      ORDER BY PIZ.price ASC  
      LIMIT 1;
<img src="https://github.com/user-attachments/assets/5e104263-0cfe-45c7-99de-0ef573b137b8" alt="Description of the Image" width="700" height="300" />

* **Query The Pizza Ordered Qty By Size?**    
      SELECT PIZ.size, SUM(POD.quantity) AS total_quantity FROM pizza_order_details POD  
      JOIN pizzas PIZ ON POD.pizza_id = PIZ.pizza_id  
      GROUP BY PIZ.size;
<img src="https://github.com/user-attachments/assets/89100a59-172f-4763-8278-ce6a9cf14ca5" alt="Description of the Image" width="700" height="300" />

 * Q**uery The Pizza Ordered Qty By Category?**      
      SELECT PT.category, SUM(POD.quantity) AS total_quantity FROM pizza_order_details POD  
      JOIN pizzas PIZ ON POD.pizza_id = PIZ.pizza_id  
      JOIN pizza_types PT ON PIZ.pizza_type_id = PT.pizza_type_id  
      GROUP BY PT.category;
<img src="https://github.com/user-attachments/assets/16a41bae-3d27-4978-abee-3e8bc5921ba9" alt="Description of the Image" width="700" height="300" />

* **Query The Pizza Ordered Qty By Pizza Name?**  
      SELECT PT.name AS pizza_name, SUM(POD.quantity) AS total_quantity FROM pizza_order_details POD  
      JOIN pizzas PIZ ON POD.pizza_id = PIZ.pizza_id  
      JOIN pizza_types PT ON PIZ.pizza_type_id = PT.pizza_type_id  
      GROUP BY PT.name;
<img src="https://github.com/user-attachments/assets/feb9599a-dc84-4b65-a23e-36e355ea192a" alt="Description of the Image" width="700" height="300" />

 
* **Query The Top 7 Types Based Orders Qty? Display Pizza Name, Order Qty?**    
SELECT PT.name AS pizza_name, SUM(POD.quantity) AS total_quantity FROM pizza_order_details POD
JOIN pizzas PIZ ON POD.pizza_id = PIZ.pizza_id
JOIN pizza_types PT ON PIZ.pizza_type_id = PT.pizza_type_id
GROUP BY PT.name
ORDER BY total_quantity DESC
<img src="https://github.com/user-attachments/assets/6c9dcae4-f159-48b1-967e-6b1563ce48c6" alt="Description of the Image" width="700" height="300" />

* **Query The Distribution Of Orders By Hour Of Day?**     
SELECT HOUR(time) AS hour_of_day, COUNT(order_id) AS total_orders FROM pizza_orders  
GROUP BY HOUR(time)  
ORDER BY hour_of_day;
<img src="https://github.com/user-attachments/assets/b7bed8e9-78ff-40d4-a85d-1ec4232e9dfb" alt="Description of the Image" width="700" height="300" />

* **Query The Pizza Order Qty By Date And Calculate The Average Numbers Of Pizzas Ordered Per Day?**     
SELECT date, SUM(POD.quantity) AS total_order_qty,AVG(SUM(POD.quantity)) OVER () AS avg_order_qty_per_day FROM 
pizza_order_details POD
JOIN pizza_orders PO ON POD.order_id = PO.order_id
GROUP BY date;
<img src="https://github.com/user-attachments/assets/bb61bb02-5fca-466e-ac6d-b6f94ebc2d42" alt="Description of the Image" width="700" height="300" />
 
* **Query The Top 7 Pizza Names By Revenue? #Display Pizza Name, Revenue , Orderqty ?**    
SELECT PT.name AS pizza_name,  SUM(POD.quantity * PIZ.price) AS revenue, SUM(POD.quantity) AS order_qty FROM 
pizza_order_details POD
JOIN pizzas PIZ ON POD.pizza_id = PIZ.pizza_id
JOIN pizza_types PT ON PIZ.pizza_type_id = PT.pizza_type_id
GROUP BY PT.name
ORDER BY revenue DESC
LIMIT 7;
<img src="https://github.com/user-attachments/assets/ea0a6a8e-75b0-4958-b959-1d4c08b8e4cc" alt="Description of the Image" width="700" height="300" />

 * **Query The Percentage Contribution Of Each Pizza Category To Total Revenue?**     
    SELECT PT.category,
   	(SUM(POD1.quantity * PI.price) /
        (SELECT SUM(POD.quantity * PIZ.price)
         FROM pizza_order_details POD
         JOIN pizzas PIZ ON POD.pizza_id = PIZ.pizza_id)) * 100 AS revenue_percentage
    FROM pizza_order_details POD1
    JOIN pizzas PI ON POD1.pizza_id = PI.pizza_id
    JOIN pizza_types PT ON PI.pizza_type_id = PT.pizza_type_id  GROUP BY PT.category;
<img src="https://github.com/user-attachments/assets/a1f1b320-7ec4-4629-9b60-9ff37a53fbcd" alt="Description of the Image" width="700" height="300" />



