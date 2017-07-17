###Test SOAP
1. In Postman, create a new POST request, and copy the WSDL URL to the request URL. In Headers, add add one key "text/xml" for *Content-Type*, and set another key "hostretrieveall" for *soapaction*. 

2. In Body, add this block of code, replace the sID with what you got from the authentication REST API, and the API with the API you want to use:    


        <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:Manager">
           <soapenv:Header/>
           <soapenv:Body>
              <urn:hostRetrieveAll>
                 <urn:sID>xxxxxxxxxxxxxxxxxxxxxxxxxx</urn:sID>
              </urn:hostRetrieveAll>
           </soapenv:Body>
        </soapenv:Envelope>
