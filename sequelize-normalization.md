[Back to main page ](README.md)

## Sequelize 

Sequelize is a dynamic and powerful JavaScript library. It is a promise-based ORM (Object Relational Mapping) that deals with the management versions of the database primarily SQL database. It can also support other databases like PostgreSQL, MySQL, SQLite, and MSSQL. It is also popularly known as Object-Relation Mapper because it maps object syntax into a database schema 

Sequelize supports the standard associations: One-To-One, One-To-Many and Many-To-Many.

###  Sequelize provide four methods of association : 
hasOne – 1:1
belongsTo – 1:1

hasMany – 1:many
belongsToMany – 1:many

belongsToMany - m:n

1. One To One relation "hasOne" + "belongsTo":
When a row of a table corresponds to a specific row of another table and vice versa, we have a One-To-One relation between the 2 tables.

For example – each “Student” in the students’ table has a corresponding “Profile” in the profiles table.
[one to one](https://i0.wp.com/strapengine.com/wp-content/uploads/2022/01/sequelize-one-to-one-association.jpeg?w=560&ssl=1)

2. One To Many relation "hasMany" + "belongsTo"
When one row of a table corresponds to multiple rows of another table it means we can have a One-To-Many relation.

For example: for each “Student” in the students’ table we will have multiple “Attendance” records(rows) in the attendance table.
[one to many](https://i0.wp.com/strapengine.com/wp-content/uploads/2022/01/sequelize-one-to-many-association.jpeg?w=494&ssl=1)
[see](https://i0.wp.com/strapengine.com/wp-content/uploads/2022/01/sequelize-many-to-many-association-idea.png?w=693&ssl=1)

3.Many To Many relation "belongsToMany"
When multiple rows of a table correspond to multiple rows of another table we can have a Many-To-Many relation.

For example: – for each “Student” in the students’ table, we can have multiple rows in the courses table as a “Student” can apply for more than 1 course. Similarly for each “Course” in the courses table, we can have more than 1 “Student” attending the “Course”.
[](https://i0.wp.com/strapengine.com/wp-content/uploads/2022/01/sequelize-many-to-many-association.jpeg?resize=768%2C176&ssl=1)


## Options for Each way :
1- one to one
onDelete and onUpdate
ex
```js
Foo.hasOne(Bar, {
  onDelete: 'RESTRICT',
  onUpdate: 'RESTRICT'
});
Bar.belongsTo(Foo);
```
possible choices are : RESTRICT, CASCADE, NO ACTION, SET DEFAULT and SET NULL.
default is SET NULL for ON DELETE and CASCADE for ON UPDATE.

2-one to Many : Like One-To-One relationships, ON DELETE defaults to SET NULL and ON UPDATE defaults to CASCADE.
ex : 
```js
Team.hasMany(Player, {
  foreignKey: 'clubId'
});
Player.belongsTo(Team);
```
3- many to many : Unlike One-To-One and One-To-Many relationships, the defaults for both ON UPDATE and ON DELETE are CASCADE for Many-To-Many relationships.
Belongs-To-Many creates a unique key on through model. This unique key name can be overridden using uniqueKey option. To prevent creating this unique key, use the unique: false option

ex: 

```js
Project.belongsToMany(User, { through: UserProjects, uniqueKey: 'my_custom_unique' })
```

## Association Aliases & Custom Foreign Keys

There are three ways to specify a different name for the foreign key:

1- providing the foreign key name directly : The foreign key name can be provided directly with an option in the association definition, as follows:

```js
Ship.belongsTo(Captain, { foreignKey: 'bossId' }); // This creates the `bossId` foreign key in Ship.

// Eager Loading is done by passing the model to `include`:
console.log((await Ship.findAll({ include: Captain })).toJSON());
// Or by providing the associated model name:
console.log((await Ship.findAll({ include: 'Captain' })).toJSON());

// Also, instances obtain a `getCaptain()` method for Lazy Loading:
const ship = Ship.findOne();
console.log((await ship.getCaptain()).toJSON());
```
2-defining an Alias :Defining an Alias is more powerful than simply specifying a custom name for the foreign key. This is better understood with an example:

```js
Ship.belongsTo(Captain, { as: 'leader' }); // This creates the `leaderId` foreign key in Ship.

// Eager Loading no longer works by passing the model to `include`:
console.log((await Ship.findAll({ include: Captain })).toJSON()); // Throws an error
// Instead, you have to pass the alias:
console.log((await Ship.findAll({ include: 'leader' })).toJSON());
// Or you can pass an object specifying the model and alias:
console.log((await Ship.findAll({
  include: {
    model: Captain,
    as: 'leader'
  }
})).toJSON());

// Also, instances obtain a `getLeader()` method for Lazy Loading:
const ship = Ship.findOne();
console.log((await ship.getLeader()).toJSON());
```
3-doing both things :We can define and alias and also directly define the foreign key

ex
```js
Ship.belongsTo(Captain, { as: 'leader', foreignKey: 'bossId' }); // This creates the `bossId` foreign key in Ship.

// Since an alias was defined, eager Loading doesn't work by simply passing the model to `include`:
console.log((await Ship.findAll({ include: Captain })).toJSON()); // Throws an error
// Instead, you have to pass the alias:
console.log((await Ship.findAll({ include: 'leader' })).toJSON());
// Or you can pass an object specifying the model and alias:
console.log((await Ship.findAll({
  include: {
    model: Captain,
    as: 'leader'
  }
})).toJSON());

// Also, instances obtain a `getLeader()` method for Lazy Loading:
const ship = Ship.findOne();
console.log((await ship.getLeader()).toJSON());
```

## Special methods/mixins added to instances: 

like if we have two models **Foo** and **Bar**, and they are associated, their instances will have the following methods/mixins available, depending on the association type:
1- Foo.hasOne(Bar)
2- fooInstance.getBar()
3- fooInstance.setBar()
4- fooInstance.createBar()

