# dcc (Description based Client Conditioning)
A JSON based, Descriptive, Client Conditioning framework which conditions back-end clients according to needs described by the front end. The flexibility to describe the nature of information required, helps the data-asking-developer to get major control over the type of data it needs.

# Where does concept of dcc apply?
[visio diagram]

# How to do CRUD operations using dcc?
  The main object is simply called "data". We will start with Read(or Inquire) operation.
  
  # READ Operation
  
  "data": {
	  "request": {
      "type": "read",
      "operation":{
        "name": "getCustomerID",		
        "config": {
          "arguments": {
            "account": 6499570182344576
          },
          "required": {
            "all": false,           //set it to true if all fields are required
            "fields": [
            {
              "fname":"customerID",
              "extractFrom:": "/custIDRetrieval",
              "fieldFrom":"custID"  //the value is the field name in the above service's respnse
              "dataTypeRequested":"String"
            },
            {
              "fname: "relationshipID",
              "extractFrom:": "/acctrelship",
              "fieldFrom":"relID"					//default data type is string
            }
            {
              "fname: "creditLimit",
              "inputValue": 15600,
              "extractFrom:": "/creditLimitRetrieval",
              "fieldFrom":"creditLimit"					
            }
          ]
          }
        }		
      }
	}
 }
