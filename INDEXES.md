# Indexes

- A data structure that improves query performance by providing quick access to data
- MongoDB supports various index types, including:
    - Single Field Index
    - Compound Index (multiple fields)
    - Multikey Index (arrays)
    - Geospatial Index (location-based data)
    - Text Index (text search)
    - Hashed Index (hashed values)

# Creating Indexes

- db.collection.createIndex({ field: 1 }) (ascending index)
- db.collection.createIndex({ field: -1 }) (descending index)
- db.collection.createIndex({ field1: 1, field2: 1 }) (compound index)


# Index Properties

- name: index name
- ns: namespace (collection name)
- key: index fields and directions
- v: index version
- unique: whether the index is unique
- sparse: whether the index is sparse

# Index Types

- Single Field Index: indexes a single field
- Compound Index: indexes multiple fields
- Multikey Index: indexes array fields
- Geospatial Index: indexes location-based data (2D and 3D)
- Text Index: indexes text data for text search
- Hashed Index: indexes hashed values for efficient queries