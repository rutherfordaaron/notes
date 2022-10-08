MySQL
	• To interact with MySQL inside Node, swe need to use the mysql2 package
		
		npm i --save mysql2
		
	• Then, we need to connect our application to our database by creating a connections pool
		○ Every time we make a query to the database, we create a connection then close it at the end of the query
		○ We could do this by creating individual connections and closing them, but that is cumbersome
		○ Instead, we can create a connection pool that handles a pool of connections that are always available
		
		// database.js util file
		const mysql = require("mysql2");
		
		const pool = mysql.creatPool({
		  host: "localhost",
		  user: "root",
		  databse: "my-schema"
		  password: "1234"
		});
		
		mosule.exports = pool.promise();
		
		○ As you can see, the createPool() method takes a JavaScript object as an argument, and in that object we need 4 things defined
			§ The host where our database is served from
				□ localhost for a local instance
			§ The user, which defaulted to "root" when we set up our local SQL server
			§ The database
				□ One server can have many databases, so we can create a new Schema in our MySQL workbench and connect to it via its name
			§ The password
				□ Whatever passwrd we setup for our database server
		○ We export the pool in a way that allows us to use promises with it, so that we can create asynchronous code whe making queries to our database
		○ From here we can import our pool to other places and access our database;

Basic SQL Use
	• Now that we have create our db variable that allows us to access our database, we can use the execute() method to pass SQL syntax as a string and make requests
		
		db.execute("SELECT * FROM products")
		  .then(result => {
		    console.log(result[0]);
		  })
		  .catch(err => console.log(err));
		
		○ Since our db was exported with a promise attached to it, we can treat it like a promise and chain .then() and .catch() to it
			§ Each takes an anonymous callback. The first runs on a success and can use the result of the promise, the second catches the error if an error occurs and lets you use the error
	• To reach into the database and get data, we use SELECT and FROM
		
		execute("SELECT fields, to, select FROM table")
		
		○ This will return an array that contains two arrays
			§ The first is the data you want, the second is meta data
	• To insert data into the database, we use INSERT INTO and VALUE
		
		execute(
		      "INSERT INTO products (title, price, imageUrl, description) VALUE (?, ?, ?, ?)",
		      [this.title, this.price, this.imageUrl, this.description]
		    );
		
		○ Here, we specify the table we are inserting into what values will be inserted
			§ These must match the field defined in the schema
		○ Then, we use VALUE to pass the value, but to prevent attacks, we use ? placeholders
		○ Then, we provide an array of the values
			§ SQL will escape the value into text to prevent attacks if we do it this way
	• To retrieve a specific item from a table, we can reuse SELECT and FROM, but also use WHERE to specifiy a field that must match to get a specific item
		
		execute("SELECT * FROM table WHERE item.field = ?", [value])
		
		○ This selects everything from a tables row if the items field matches the provided value
	• Remember to access the first (0th) index of the return value. The second (1st) index is metadata
	• Up until now, this has been us addin in our own hand-written queries. This is fine, but with more complex apps, this can get incredibly difficult
		○ So, we can use a package to simplify this process and not have to write SQL queries by hand
