Choosing A Database
	• There are 2 types of databses: SQL and NoSQL
		○ Which do we use?
	• The goal of a database is to store data and make it easily accessible
		○ Significantly more efficient than storing information in files
SQL
	• SQL works in tables
		○ In each table we have field (columns)
		○ Then, we fill in records (data) down the columns
		○ SQL can also relate other tables together
	• SQL Characteristics
		○ Data Schema
			§ How the data should look; all data inputs per table look the same and fits into the same table
		○ Data Relations
			§ One to one
			§ one to many
			§ many to many
			§ i.e. a data Field from table A can also be sed in table B
	• SQL: Structured Query Language
		○ Query example: SELECT * FROM users WHERE age > 28
			§ The all caps wors are SQL keyword/syntax
			§ The symbols and lowercase words are parameters and data values
NoSQL
	• In NoSQL, tables are collections
		○ In collections, we find documents that look a bit like Objects
		○ Collections aren't strict, so documents of the same collection can vary in the data that they hold
		○ There are also to relations, so information that would overlap over different collections would have to duplicated instead of referenced to
			§ If we retrieve data, we don't have to join tables
			§ It just reads the data available instead of spending time joining tables
			§ This makes it much faster than SQL
Comparing SQL and NoSQL
	• Horizontal vs Vertical Scaling
		○ Databases need to be scaled as the program and user base grow
		○ Horizontal Scaling: buying new servers and manage data in one database 
			§ Can always get bigger
		○ Verticle Scaling: Make our existing server strong by upgrading our hardware 
			§ Can only get so big
		○ SQL has data schemas and relations and data is distributed across tables
			§ This makes horizontal scaling difficult and sometimes impossible
			§ Verticle is the best way to scale an SQL database
			§ Limitations for lots (thousands) of read and write queries per second
		○ NoSQL has no schema, no (or very few) relations, and data is typically merged or nested in a few collections
			§ Horizontal and Vertical scaling are much more possible
			§ Great performance for mass read and write requests
		○ SQL is great for information that doesn't change very often, but relations matter (users)
		○ NoSQL is great for information that changes all the time (e-commerce orders)
		○ It mostly matters on what data you're storing and how you want to store it
