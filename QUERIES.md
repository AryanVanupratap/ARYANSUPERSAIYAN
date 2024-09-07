# Query Basics

- Queries are used to retrieve specific data from a MongoDB collection
- Queries are written in JSON-like format

# Query Operators

- $eq : equal to
- $ne : not equal to
- $gt : greater than
- $lt : less than
- $gte : greater than or equal to
- $lte : less than or equal to
- $in : in an array
- $nin : not in an array

# Query Methods

- find() : retrieves all documents that match the query
- findOne() : retrieves the first document that matches the query
- updateOne() : updates the first document that matches the query
- updateMany() : updates all documents that match the query
- deleteOne() : deletes the first document that matches the query
- deleteMany() : deletes all documents that match the query

# Query Filters

- _id : filters by document ID
- name : filters by field name
- email : filters by field email

# Query Projection

- Specifies which fields to include or exclude in the query results
- Uses the projection option

# Query Sorting

- Specifies the order of the query results
- Uses the sort option

# Query Limiting

- Specifies the maximum number of documents to return
- Uses the limit option

# Query Skipping

- Specifies the number of documents to skip before returning results
- Uses the skip option