# Document Manager

The Document Manager service allows for uploading loan-related documents needed to service the loan. This allows for integration with third-party document retention systems to comply with document-retention requirements. 

To upload a document, first call `/POST /documents/upload` to create a document upload request. Use the URL returned in `data.url` in the response payload to upload the document to Velocity's servers.