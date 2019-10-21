# dcc (Description based Client Conditioning)
A JSON based, Descriptive, Client Conditioning framework which conditions back-end clients according to needs described by the front end. The flexibility to describe the nature of information required, helps the data-asking-developer to get major control over the type of data it needs. This concept has similar goals GraphQL targets to achieve but without the overhead of a new language, using good old JSON!

# Where does concept of dcc apply?
[visio diagram]

# How to do CRUD operations using dcc?
  The main object is simply called "data". We will start with Read(or Inquire) operation.
  
  # READ Operation
  
 ``` "data": {
	"request": {
		"type": "inquire",
		operation:{
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
	"create": {
		"operation": {
			"name": "payment",
			"requestParams": ["acctNumber",etc],
			"flow": [{
				"stepId" : 1,
				"serviceName": "token",
				"outputTo": "acctToken",
				"outputParams": ["access_token"]
			},
			{
				"acctKeys"
			},
			{
				"serviceName": "connectSP"
				"SPName" : "stored_procedure_name"
			}];
			"required": [{
				"partyId": "actual_field_name",
				"resultMessage": "successful operation"
			}]
		}
		"creator": "id",
		"role": "admin"
	}
}
```
