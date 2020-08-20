# Azure uploading features

[Put Block List REST reference](https://docs.microsoft.com/en-us/rest/api/storageservices/Put-Block-List?redirectedfrom=MSDN)

[Understanding block blobs](https://docs.microsoft.com/en-us/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs?redirectedfrom=MSDN)

So I want to upload large blobs into Azure storage blobs with simultaneous multiblock uploads. Here's some notes:
* Apparently: "You can upload blocks in any order, and determine their sequence in the final block list commitment step."
* Use Put blocks to upload things
* Then commit with PutBlockList to give the uploaded blocks an order and commit them as a blob.
* "You can also upload a new block to replace an existing uncommitted block of the same block ID."
* "All uncommitted blocks are also discarded when a block list commitment operation occurs but does not include them."


"Block IDs are strings of equal length within a blob. Block client code usually uses base-64 encoding to normalize strings into equal lengths. When using base-64 encoding, the pre-encoded string must be 64 bytes or less. Block ID values can be duplicated in different blobs. A blob can have up to 100,000 uncommitted blocks, but their total size cannot exceed 200,000 MB."

"If you write a block for a blob that does not exist, a new block blob is created, with a length of zero bytes."

