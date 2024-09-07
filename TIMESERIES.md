# TIME SERIES
# Time Series Data

- A sequence of data points measured at regular time intervals
- Examples: sensor readings, stock prices, weather data

# MongoDB Time Series Features

- Time Series Collections: optimized for storing and querying time series data
- Time Series Indexes: improves query performance for time-based queries
- Auto-Generation of Timestamps: automatically generates timestamps for inserted documents

# Creating a Time Series Collection

- db.createCollection("time_series_data", { timeseries: { timeField: "timestamp" } })
- timeField specifies the field containing the timestamp

# Inserting Time Series Data

- db.time_series_data.insertOne({ timestamp: ISODate(), value: 10 })
- ISODate() generates a timestamp

# Querying Time Series Data

- db.time_series_data.find({ timestamp: { $gte: ISODate("2022-01-01") } })
- Retrieves documents with timestamps greater than or equal to January 1, 2022

# Aggregation Pipeline

- $match stage: filters documents by timestamp range
- $group stage: groups documents by time interval (e.g., hourly, daily)
- $sort stage: sorts documents by timestamp

# Time Series Aggregation Example

- db.time_series_data.aggregate([ { $match: { timestamp: { $gte: ISODate("2004-01-01") } } }, { $group: { _id: { $dateTrunc: { date: "$timestamp", unit: "hour" } }, value: { $avg: "$value" } } }, { $sort: { _id: 1 } } ])

- Retrieves hourly averages for documents with timestamps greater than or equal to January 1, 2004

