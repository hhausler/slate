# Document Manager

The Document Manager service allows for uploading loan-related documents needed to service the loan. This allows for integration with third-party document retention systems to comply with document-retention requirements. 

To upload a document, first call `/POST /documents/upload` to create a document upload request. Use the URL returned in `data.url` in the response payload to upload the document to Velocity's servers.

To download a document, first call  `/GET /documents/borrower-documents/{borrowerId}` to get a list of document meta data.  Then to pull a specific document byte array, use `/GET/documents/document/{documentId}`.

To update the 'hidden' property of a document to true in order to no longer pull the document in the list, use `DELETE /documents/document/{documentId}`.

To update the 'read' property of a document, use `POST /documents/read-documents/{documentId}` to set the flag to true (i.e. it has been read) and use `DELETE /documents/read-documents/{documentID}` to set the flag to false (i.e. the document has been set to unread).
