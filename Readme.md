Problem Statement(Group-4)-


1. Create anypoint platform account using the inveniolsi email address.
2. Create a RAML having the GET and POST operations.
3. Have the vendorName as the header in GET operation - this will be used in the mule flow.

GET request sample:
{

  "uniqueId" : "InvenioLSI - 591dda7d-8c10-4e1e-886b-87b571526af4",
  "currentDate": "04-12-2022 12:52 PM",
  "status": "Success"

}



POST request XML sample:

<?xml version='1.0' encoding='UTF-8'?>
<orders>
  <orderId>AB123</orderId>
  <processingDate>061222</processingDate>
  <processingTime>1237</processingTime>
  <noOfRecords>2</noOfRecords>
  <records>
    <name>xyz</name>
    <contactNo>9876543210</contactNo>
    <emailId>test@inveniolsi.com</emailId>
  </records>
  <records>
    <name>abc</name>
    <contactNo>9876543211</contactNo>
    <emailId>test123@inveniolsi.com</emailId>
  </records>
</orders>


4. Publish the RAML to the Anypoint Exchange.

Create a new project in Anypoint Studio and achieve the below requirement:
1. Make use of RAML created and generate the GET and POST flows.
2. Have the loggers to capture the details of each transaction.

For GET operation:
3. when the user tries to use the GET operation, below is the expected JSON payload:
{

  "uniqueId" : "InvenioLSI - 591dda7d-8c10-4e1e-886b-87b571526af4",
  "currentDate": "04-12-2022 12:52 PM",
  "status": "Success"

}
- uniqueId should be dynamic for each request appended with the header value - vendorName coming from the headers.
- currentDate should populate the current date and time stamp.

For POST operation:
3. Read the input XML/JSON and perform the below validations:
   - If the orderId is already processed then throw an error - Make use of object store concept(Group 4)
Error message sample:
{

  "errorMessage" : "record with orderId=AB123 is already processed",
  "status": "Failed"

}

4. Once the validation check is completed then proceed with the further transformation logic.
5. Convert input XML/JSON to below expected XML/JSON/CSV formats:


Expected output JSON sample:
[

  {

    "order-id": "AB123",
    "user-name": "XYZ",
    "phone-number": "+91 9876543210",
    "mail": test@inveniolsi.com

  },

  {

    "order-id": "AB123",
    "user-name": "ABC",
    "phone-number": "+91 9876543211",
    "mail": test123@inveniolsi.com

  }

]

6. Deploy the changes to cloud hub and test the application using the postman. 
GitHub:
- Create a repo intern-mule-poc, the dev branch on top of main branch and commit the code changes in dev branch and share the pull request URL and cloud hub URL
Expectation:
- Proper naming conventions.
- Application execution with the expected output.
- Error handling with the relevant JSON error message.
- Deployment of application to the cloud hub.
