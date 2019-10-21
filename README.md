# dcc (Description based Client Conditioning)
A JSON based, Descriptive, Client Conditioning framework which conditions back-end clients according to needs described by the front end. The flexibility to describe the nature of information required, helps the data-asking-developer to get major control over the type of data it needs. This concept has similar goals GraphQL targets to achieve but without the overhead of a new language, using good old JSON!

# Where does concept of dcc apply?
[visio diagram]

# How to do CRUD operations using dcc?
  The main object is simply called "data". We will start with Read(or Inquire) operation.
  
  # READ Operation
  
 ``` 
 "data": {
	"request": {
		"type": "inquire",
		"operation": {
			"name": "getPartyId",		
			"config": {
				"arguments": {
					"account": "account_value"
				},
				"required": {
					"all": false,
					"fields": [					
					{
						"fname": ["partyId"],
						"extractFrom:": "backend_service",
						"fieldFrom":"custPartyID" //array if multiple											
						"dataTypeRequested":"String"
					},
					{
						"fname: "relationshipID",
						"extractFrom:": "/acctIds",
						"fieldFrom":"rshipID"					
					},
					{
						"fname: "creditLimit",
						"input": "credit_limit_service",
						"extractFrom:": "/climit",
						"fieldFrom":"credit_Limit"					
					},
					{
						"fname: "recordID",						
						"extractFrom:": "database",
						"query":{
							"type" : "stored_procedure",
							"name" : "get_UID",
							"parameters": [account_number]							
						}											
					}
				]
				}
			}		
		}
	}	
}
```
# Why use dcc?
	1. Frontend/UI controls what information is needed rather than middleware/backend 
	   specifying what information UI can receive.
	2. Moreover, the granularity ability can specify where to access data from 
	   i.e. which exact web service, which DB, which Stored Procedure, etc. 
	   You can also specify queries to run directly from the UI.
	3. No need to redeploy applications just because you need an additional 
	   parameter from the same web service you created before.
	4. Dcc majorly helps combine multiple endpoints to a very few 
	   for better re-organization and thinner architectures.
	5. Combine dcc with other JSON based DB (Mongo, CouchDB, etc) 
	   for seamless integration directly from the UI.
