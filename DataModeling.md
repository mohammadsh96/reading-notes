# SQL vs NoSQL Database Differences
-**SQL** 
-**NoSQL** .
| SQL                                      | NoSQL                                                  | 
|------------------------------------------|--------------------------------------------------------|
| databases are primarily called           |database are primarily called as non-relational or distributed database|
|as Relational Databases                   | 
|------------------------------------------|----------------------------------------------------------| 
|  databases are table based databases  |databases are document based, key-value pairs, graph databases or wide-column stores  | databases have predefined schema| databases have dynamic schema for unstructured data|databases are vertically scalable|databases are horizontally scalable|databases are scaled by increasing he horse-power of the hardware| databases are scaled by increasing the databases servers in the pool of resources to reduce the load.| databases uses SQL ( structured query language ) for defining and manipulating the data, which is very powerful| queries are focused on collection of documents. Sometimes it is also called as UnQL (Unstructured Query Language)|are good fit for the complex query intensive environment |databases are not good fit for complex queries. On a high-level,|databases are not best fit for hierarchical data storage.|fits better for the hierarchical data storage as it follows the key-value pair way of storing data similar to JSON data.|QL databases are vertically scalable. You can manage increasing load by increasing the CPU, RAM, SSD, etc, on a single server|databases are horizontally scalable. You can just add few more servers easily in your NoSQL database infrastructure to handle the large traffic.| databases are best fit for heavy duty transactional type applications, as it is more stable and promises the atomicity as well as integrity of the data|you can use NoSQL for transactions purpose, it is still not comparable and sable enough in high load and for complex transactional applications.|Excellent support are available for all SQL database from their vendors. There are also lot of independent consultations who can help you with SQL database for a very large scale deployments|database you still have to rely on community support, and only limited outside experts are available for you to setup and deploy your large scale NoSQL deployments.|emphasizes on ACID properties ( Atomicity, Consistency|database follows the Brewers CAP theorem|


### SQL Database Examples :
1-MySQL Community Edition
2-MS-SQL Server Express Edition
3-Oracle Express Edition

### NoSQL Database Examples :
1- MongoDB
2-CouchDB
3-Redis

## Data Modeling – Table Elements 
 ![relational database](https://www.essentialsql.com/wp-content/uploads/2021/11/Database-Table-Data-Modeling.png)

 ## Data Modeling – Table Relationships
 ![one-to-many relationship](https://www.essentialsql.com/wp-content/uploads/2014/06/DataModel-Relations1.png)


### Sequelize v6 :

Sequelize is a promise-based Node.js ORM tool for Postgres, MySQL, MariaDB, SQLite, Microsoft SQL Server, Amazon Redshift and Snowflake’s Data Cloud. It features solid transaction support, relations, eager and lazy loading, read replication and more.


#### **example**

```js
const { Sequelize, Model, DataTypes } = require('sequelize');
const sequelize = new Sequelize('sqlite::memory:');

class User extends Model {}
User.init({
  username: DataTypes.STRING,
  birthday: DataTypes.DATE
}, { sequelize, modelName: 'user' });

(async () => {
  await sequelize.sync();
  const jane = await User.create({
    username: 'janedoe',
    birthday: new Date(1980, 6, 20)
  });
  console.log(jane.toJSON());
})();
```