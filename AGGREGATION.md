# Aggregation

- A pipeline-based framework for processing and transforming data
- Allows for complex data processing and analysis

# Aggregation Pipeline

- A series of stages that process data in a specific order
- Each stage transforms the data in some way

# Aggregation Stages

- $match: filters documents based on a condition
- $project: transforms and includes/excludes fields
- $group: groups documents by a specified field
- $sort: sorts documents by a specified field
- $limit: limits the number of documents
- $lookup: performs a left outer join with another collection
- $unwind: deconstructs an array field
- $out: writes the result to a new collection

# Aggregation Example

- db.collection.aggregate([
- { $match: { status: "active" } },
- { $group: { _id: "$department", total: { $sum: "$salary" } } },
- { $sort: { total: -1 } }
- ])

- Retrieves the total salary for each department, sorted in descending order

# Aggregation Operators

- $sum
- $avg
- $min
- $max
- $push
- $addToSet
- $first
- $last
