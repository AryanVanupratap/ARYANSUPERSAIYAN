Change Stream Operations

- watch() - starts a change stream on a collection or database
- pipe() - pipes the change stream to another collection or database
- resumeToken() - resumes a change stream from a specific token

Change Stream Event Types

- insert - a new document was inserted
- update - a document was updated
- delete - a document was deleted
- replace - a document was replaced
- drop - a collection or database was dropped
- rename - a collection or database was renamed

Change Stream Event Structure

- _id - the ID of the changed document
- operationType - the type of operation (insert, update, delete, etc.)
- fullDocument - the full document after the change
- ns - the namespace (collection or database) of the changed document
- to - the new namespace (collection or database) after a rename operation

Change Stream Options

- resumeAfter - resumes the change stream from a specific token
- startAfter - starts the change stream from a specific token
- fullDocument - includes the full document in the change stream events
- showExpandedEvents - includes expanded events for update operations