# Mongoose Basics

- Mongoose is a MongoDB ORM (Object Relational Mapping) library for Node.js
- It provides a schema-based solution for modeling data in MongoDB
- Install Mongoose using npm: npm install mongoose

# Connecting to MongoDB

- Connect to MongoDB using mongoose.connect(): mongoose.connect('mongodb://localhost:27017/mydatabase', { useNewUrlParser: true, useUnifiedTopology: true });
- Options:
    - useNewUrlParser: enables the new URL parser
    - useUnifiedTopology: enables the new topology engine

# Defining a Schema

- Define a schema using mongoose.Schema(): const userSchema = new mongoose.Schema({ name: String, email: String });
- Schema types:
    - String
    - Number
    - Boolean
    - Array
    - Date
    - ObjectId

# Creating a Model

- Create a model using mongoose.model(): const User = mongoose.model('User', userSchema);

# Creating a Document

- Create a document using new Model(): const user = new User({ name: 'John Doe', email: 'john.doe@example.com' });

# Saving a Document

- Save a document using save(): user.save((err, user) => { console.log(user); });

# Finding Documents

- Find documents using find(): User.find((err, users) => { console.log(users); });
- Options:
    - filter: filter documents by a query
    - projection: specify fields to include or exclude
    - sort: sort documents by a field
    - limit: limit the number of documents returned
    - skip: skip a number of documents

# Updating a Document

- Update a document using updateOne(), updateMany(), or findByIdAndUpdate(): User.findByIdAndUpdate('1234567890', { name: 'Jane Doe' }, (err, user) => { console.log(user); });

# Deleting a Document

- Delete a document using deleteOne(), deleteMany(), or findByIdAndRemove(): User.findByIdAndRemove('1234567890', (err, user) => { console.log(user); });

# Validating Data

- Validate data using schema validation: const userSchema = new mongoose.Schema({ name: { type: String, required: true }, email: { type: String, required: true, unique: true } });
- Validation options:
    - required: requires a field to be present
    - unique: requires a field to be unique
    - min, max: specifies a minimum or maximum value for a field
    - enum: specifies an array of allowed values for a field

# Populating Documents

- Populate documents using populate(): const userSchema = new mongoose.Schema({ name: String, email: String, posts: [{ type: mongoose.Schema.Types.ObjectId, ref: 'Post' }] });
- Populate options:
    - path: specifies the field to populate
    - model: specifies the model to use for population
    - select: specifies fields to include or exclude

# Mongoose Hooks

- Use hooks to execute custom logic before or after a document is saved, updated, or deleted: userSchema.pre('save', function(next) { console.log('Before save'); next(); });

# Mongoose Plugins

- Use plugins to extend Mongoose functionality: mongoose.plugin(require('mongoose-paginate'));

# CONNECTIONS

# Connection Options

- uri: the MongoDB connection string
- useNewUrlParser: enables the new URL parser
- useUnifiedTopology: enables the new topology engine
- poolSize: specifies the number of connections in the pool
- bufferMaxEntries: specifies the maximum number of buffered operations

# Connection States

- disconnected: the connection is closed
- connected: the connection is established
- connecting: the connection is being established
- disconnecting: the connection is being closed

# Connection Events

- connected: emitted when the connection is established
- disconnected: emitted when the connection is closed
- error: emitted when an error occurs

# Connecting to MongoDB

- mongoose.connect('mongodb://localhost:27017/mydatabase', { useNewUrlParser: true, useUnifiedTopology: true });

# Closing a Connection

- mongoose.disconnect();

# Checking Connection Status

- mongoose.connection.readyState;

# QUERY

Mongoose models provide several static helper functions for CRUD operations. Each of these functions returns a mongoose Query object.

Model.deleteMany()
Model.deleteOne()
Model.find()
Model.findById()
Model.findByIdAndDelete()
Model.findByIdAndRemove()
Model.findByIdAndUpdate()
Model.findOne()
Model.findOneAndDelete()
Model.findOneAndReplace()
Model.findOneAndUpdate()
Model.replaceOne()
Model.updateMany()
Model.updateOne()

# MIDDLEWARE

# Mongoose Middleware

- Middleware functions that run before or after a Mongoose operation
- Used for tasks such as validation, sanitization, and logging

# Type of Middleware

- pre: runs before the operation
- post: runs after the operation

# Examples of Middleware

- Validation middleware: checks if data is valid before saving
- Sanitization middleware: removes unnecessary data before saving
- Logging middleware: logs information about the operation

# Defining Middleware

- Use the pre or post method to define middleware
- Pass a function that takes the next parameter to continue the operation

# Example of Defining Middleware

- userSchema.pre('save', function(next) { console.log('Before save'); next(); });

# Chaining Middleware

- Multiple middleware functions can be chained together
- Each middleware function calls the next parameter to continue the operation

# Error Handling in Middleware

- Use try/catch blocks to handle errors in middleware
- Call next(err) to pass the error to the next middleware or operation

# Asynchronous Middleware

- Use async/await or promises to handle asynchronous operations in middleware

# DISCRIMINATORS

# Defining a Discriminator

- Use the discriminator option when creating a model
- Pass a string or a function that returns a string to determine the discriminator value

# Example of Defining a Discriminator

- const userSchema = new mongoose.Schema({ name: String, email: String });
- const user = mongoose.model('User', userSchema);
- const admin = user.discriminator('Admin', new mongoose.Schema({ role: String }));

# Example of Using a Discriminator

- const adminDoc = new admin({ name: 'John Doe', email: 'john.doe@example.com', role: 'admin' }); 

# TIMESTAMPING

# Mongoose Time Stamping

- Mongoose provides a built-in feature for time stamping documents
- Time stamping automatically sets the createdAt and updatedAt fields when a document is created or updated

# Enabling Time Stamping

- Enable time stamping by setting the timestamps option to true in the schema: const userSchema = new mongoose.Schema({ name: String, email: String }, { timestamps: true });

# Time Stamping Fields

- createdAt: automatically set to the current date and time when a document is created
- updatedAt: automatically set to the current date and time when a document is updated

# Customizing Time Stamping

- Customize the time stamping fields by setting the createdAt and updatedAt options in the schema: const userSchema = new mongoose.Schema({ name: String, email: String }, { timestamps: { createdAt: 'created_at', updatedAt: 'updated_at' } });

# Disabling Time Stamping

- Disable time stamping by setting the timestamps option to false in the schema: const userSchema = new mongoose.Schema({ name: String, email: String }, { timestamps: false });

# Time Stamping in Subdocuments

- Time stamping also works in subdocuments: const userSchema = new mongoose.Schema({ name: String, email: String, address: { street: String, city: String } }, { timestamps: true });

# TRANSACTIONS

# Starting a Transaction

- Start a transaction using the startSession() method: const session = await mongoose.startSession();
- Begin the transaction using the startTransaction() method: await session.startTransaction();

# Performing Operations

- Perform operations within the transaction using the session object: await User.create([{ name: 'John Doe' }], { session });

# Committing a Transaction

- Commit the transaction using the commitTransaction() method: await session.commitTransaction();

# Aborting a Transaction

- Abort the transaction using the abortTransaction() method: await session.abortTransaction();

# Using Transactions with Models

- Use transactions with models by passing the session object to the model methods: await User.create([{ name: 'John Doe' }], { session });

# Transaction Options

- readConcern: specifies the read concern for the transaction
- writeConcern: specifies the write concern for the transaction
- readPreference: specifies the read preference for the transaction

# Transaction Errors

- TransactionError: thrown when a transaction fails
- AbortError: thrown when a transaction is aborted





