# PostmanNewmanDemo

**---------------------Correlation in postman**

**1. Create collection variable**

**2. In test case where you need extract the id type this:**

	const jsonData = pm.response.json()
	pm.collectionVariables.set('collectionVariableName', jsonData.data.responseId)

**3. to test the status code result**

	pm.test('testName',function()){
		pm.response.to.have.status(200)
	}

**4. to tests data in the response**

	pm.test(){
		pm.expect(jsonData.data.email)to.be.eq('Email@gmail.com')
	}
	
# Newman installation and cmd commands	

**5.A) Install newman and newman-allure-report**

**precondition:** need to install node.js first
	
**- install newman**

		npm install -g newman
**- install newman allure reporter-allure**

		npm install -g newman-reporter-allure

**5.B) Execute Postman collection with newman/jenkins**

	newman run demo-collection.postman_collection.json -e automation-environment.postman_environment.json
or
	"C:\Users\1\AppData\Roaming\npm\newman" run demo-collection.postman.collection.json -e automation-environment.postman_environment.json

**6. Execute Postman collection with newman/jenkins + allure report**

**--EXECUTE**

	newman run demo-collection.postman_collection.json -e automation-environment.postman_environment.json -r allure --reporter-allure-export C:\Users\1\Desktop\Postman\postman-demo\results

**--GENERATE REPORT**

**SERVE(generate temp file)**

	allure serve C:\Users\1\Desktop\Postman\postman-demo\results

**GENERATE HTML(generate html report in a file)**

	allure generate C:\Users\1\Desktop\Postman\postman-demo\results

**7. http-server install**

	npm install -g http-server
	
	D:\ExampleFolder\result http-server
