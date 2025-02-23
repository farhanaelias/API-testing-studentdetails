# Rest API Testing with Postman Newman

This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API.

### **Features**

- Tests for GET and POST requests
- Collection of tests for different API endpoints
- Easy environment switching setup
- Pre-request scripts for setting up data
- Test scripts for checking results and validations

  ### **Technology used:**
- Postman
- Newman

  ### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

  ## **Testing**

  ## _**1. Get Student**_

### Request URL:  https://thetestingworldapi.com/api/studentsDetails

### Request Method: Get

 ## _Response body_

 [
{
"id": 526717,

"first_name": "Anna",

"middle_name": "Banana",

"last_name": null,

"date_of_birth":"12/23/1990"

},

{

"id": 526716,

"first_name": "sample ",

"middle_name": "sample ",

"last_name": "sample ",

"date_of_birth": "sample "

},

{

"id": 526715,

"first_name": "Anna",

"middle_name": "Banana", 

last_name=Uzumaki",

"last_name": null,

"date_of_birth": "12/23/1990"
} ,

..............................................................

]

## _**2. Create Student**_

### Request URL:  https://thetestingworldapi.com/api/studentsDetails

### Request Method: Post

### Pre Request Script

//firstname

var firstName = pm.variables.replaceIn("{{$randomFirstName}}")

console.log(firstName)

pm.environment.set("firstName", firstName)

//middlename

var middleName = Math.random().toString(36).substring(2, 8);

middleName = middleName.replace(/[0-9]/g, '');

pm.environment.set("middleName", middleName);

console.log("Generated Middle Name:", middleName);

//lastname

var lastName = pm.variables.replaceIn("{{$randomLastName}}")

console.log(lastName)

pm.environment.set("lastName", lastName)

//date of birth

var today = new Date();

var randomAge = Math.floor(Math.random() * (40 - 18 + 1)) + 18;

today.setFullYear(today.getFullYear() - randomAge);

var dateofBirth = today.toISOString().split('T')[0];

pm.environment.set("dateofBirth", dateofBirth);

console.log("Generated Date of Birth: ", dateofBirth); 


## Body

{ 
"first_name": "{{firstName}}", 

"middle_name": "{{middleName}}", 

"last_name": "{{lastName}}",

"date_of_birth": "{{dateofBirth}}" 

}

## Response

{
     
     "id": 10520667,
    
    "first_name": "Tanner",
    
    "middle_name": "juyhf",
    
    "last_name": "Veum",
    
    "date_of_birth": "2003-02-23"

}

## _**3. Get Specific Student**_

### Request URL:  https://thetestingworldapi.com/api/studentsDetails/id

### Request Method: Get

## Response

{
    
     "status": "true",
    
     "data": {
    
        "id": 10520667,
        
        "first_name": "Tanner",
        
        "middle_name": "juyhf",
        
        "last_name": "Veum",
        
        "date_of_birth": "2003-02-23"
   
    }

}

## _**4. Create Technical Skills**_

### Request URL:  https://thetestingworldapi.com/api/technicalskills

### Request Method: Post

## Pre-request script

// Generate a random ID

let dynamicId = Math.floor(Math.random() * 1000); 

pm.environment.set("dynamicId", dynamicId);


// Generate dynamic language array

let languages = [

  `Language ${Math.floor(Math.random() * 10) + 1}`, 
  
  `Language ${Math.floor(Math.random() * 10) + 1}` 
  
];

pm.environment.set("dynamicLanguages", JSON.stringify(languages));


// Generate a random years of experience 

let dynamicYearExp = new Date().getFullYear() - Math.floor(Math.random() * 5) + ' years'; 

pm.environment.set("dynamicYearExp", dynamicYearExp);

// Generate a random "last used" string

let dynamicLastUsed = `Language ${Math.floor(Math.random() * 10) + 1}`; 

pm.environment.set("dynamicLastUsed", dynamicLastUsed);

## Body

{

  "id": "{{dynamicId}}",
  
  "language": {{dynamicLanguages}},
  
  "yearexp": "{{dynamicYearExp}}",
  
  "lastused": "{{dynamicLastUsed}}",
  
  "st_id": "{{id}}"
  
}

## Response

{

     "status": "true",
    
      "msg": "Add  data success"

}

## _**5. Create Student Address**_

### Request URL:  https://thetestingworldapi.com/api/addresses

### Request Method: Post

## Pre-request script

// Generate a random house number between 1 and 100

let dynamicHouseNumber = Math.floor(Math.random() * 100) + 1; 

pm.environment.set("dynamicHouseNumber", dynamicHouseNumber);

// Generate a random city name (e.g., "City 3")

let dynamicCity = `City ${Math.floor(Math.random() * 10) + 1}`;

pm.environment.set("dynamicCity", dynamicCity);

// Generate a random state name (e.g., "State 2")

let dynamicState = `State ${Math.floor(Math.random() * 5) + 1}`;

pm.environment.set("dynamicState", dynamicState);

// Generate a random country name (e.g., "Country 1")

let dynamicCountry = `Country ${Math.floor(Math.random() * 3) + 1}`;

pm.environment.set("dynamicCountry", dynamicCountry);

// Generate random phone numbers (two entries)

    let dynamicPhoneNumbers = [

    {
    
        "Std_Code": `+${Math.floor(Math.random() * 100) + 1}`, 
        
        "Home": `Home ${Math.floor(Math.random() * 10) + 1}`,  
        
        "Mobile": `Mobile ${Math.floor(Math.random() * 10) + 1}` 
   
    },
    
    {
    
        "Std_Code": `+${Math.floor(Math.random() * 100) + 1}`,  
        
        "Home": `Home ${Math.floor(Math.random() * 10) + 1}`,    
        
        "Mobile": `Mobile ${Math.floor(Math.random() * 10) + 1}` 
    
    }

];

    pm.environment.set("dynamicPhoneNumbers", JSON.stringify(dynamicPhoneNumbers));



## Body

{

    "Permanent_Address": {
  
    "House_Number": "{{dynamicHouseNumber}}",
    
    "City": "{{dynamicCity}}",
    
    "State": "{{dynamicState}}",
    
    "Country": "{{dynamicCountry}}",
    
    "PhoneNumber": {{dynamicPhoneNumbers}}
    
  },
 
  
     "stId": "{{id}}"
  
}

## Response

{
   
    "status": "true",
    
    "msg": "Add  data success"
}

## _**6. Final Student details**_

### Request URL:  https://thetestingworldapi.com/api/FinalStudentDetails/id

### Request Method: Get

## Response

{
    
    "status": "true",
    
    "data": {
    
        "first_name": "Tanner",
        
        "middle_name": "juyhf",
        
        "last_name": "Veum",
        
        "date_of_birth": "2003-02-23",
        
        "TechnicalDetails": [
        
            {
                "id": 801159,
                
                "language": [
                
                    "Language 10",
                    
                    "Language 7"
                    
                ],
                "yearexp": "2025 years",
                
                "lastused": "Language 2",
                
                "st_id": "10520667"
                
            }
        
        ],
        
        "Address": [
        
            {
                "Permanent_Address": {
                
                    "House_Number": "60",
                    
                    "City": "City 8",
                    
                    "State": "State 4",
                    
                    "Country": "Country 3",
                    
                    "PhoneNumber": [
                    
                        {
                            "Std_Code": "+89",
                            
                            "Home": "Home 1",
                            
                            "Mobile": "Mobile 1"
                            
                        },
                       
                        {
                            "Std_Code": "+29",
                            
                            "Home": "Home 10",
                            
                            "Mobile": "Mobile 8"
                        }
                    ]
              
                },
                
                "Current_Address": null,
                
                "stId": "10520667"
            }
        ]
    }
}

## Test Cases

//status code validation

    pm.test("Status Code is 200", function () {

    pm.response.to.have.status(200);
    });


// language field validation

    pm.test("Language field values are correct", function () {

    let jsonData = pm.response.json();
    
    let expectedLanguage = JSON.parse(pm.environment.get("dynamicLanguages"));
    
    pm.expect(jsonData.data.TechnicalDetails[0].language).to.eql(expectedLanguage);
    });


//Year of experience field value validation

    pm.test("Year of Experience field value is correct", function () {

    let jsonData = pm.response.json();
    
    let expectedYearExp = pm.environment.get("dynamicYearExp");
    
    pm.expect(jsonData.data.TechnicalDetails[0].yearexp).to.eql(expectedYearExp);
    });


//house number field value validation

    pm.test("House Number field value is correct", function () {

    let jsonData = pm.response.json();
    
    let expectedHouseNumber = pm.environment.get("dynamicHouseNumber").toString(); // Convert to string
    
    pm.expect(jsonData.data.Address[0].Permanent_Address.House_Number).to.eql(expectedHouseNumber);
    });


//city field value validation

    pm.test("City field value is correct", function () {

    let jsonData = pm.response.json();
    
    let expectedCity = pm.environment.get("dynamicCity");
    
    pm.expect(jsonData.data.Address[0].Permanent_Address.City).to.eql(expectedCity);
    });


//country field value validation

    pm.test("Country field value is correct", function () {

    let jsonData = pm.response.json();
    
    let expectedCountry = pm.environment.get("dynamicCountry");
    
    pm.expect(jsonData.data.Address[0].Permanent_Address.Country).to.eql(expectedCountry);
    });


//mobile field value validation

    pm.test("Mobile field value is correct", function () {

    let jsonData = pm.response.json();
    
    let expectedPhoneNumbers = JSON.parse(pm.environment.get("dynamicPhoneNumbers"));
    
    let expectedMobile = expectedPhoneNumbers[0].Mobile;
    
    let actualMobile = jsonData.data.Address[0].Permanent_Address.PhoneNumber[0].Mobile;
    
    pm.expect(actualMobile).to.eql(expectedMobile);
    });


//current address field value validation

    pm.test("Current Address field value is correct", function () {

    let jsonData = pm.response.json();
    
    pm.expect(jsonData.data.Address[0].Current_Address).to.be.null;
    });


//state field value validation

    pm.test("State field value is correct", function () {

    let jsonData = pm.response.json();
    
    let expectedState = pm.environment.get("dynamicState");
    
    pm.expect(jsonData.data.Address[0].Permanent_Address.State).to.eql(expectedState);
    });


//std_code field value validation

    pm.test("Std_Code field value is correct", function () {

    let jsonData = pm.response.json();
    
    let expectedPhoneNumbers = JSON.parse(pm.environment.get("dynamicPhoneNumbers"));
    
    let expectedStdCode = expectedPhoneNumbers[0].Std_Code;
    
    let actualStdCode = jsonData.data.Address[0].Permanent_Address.PhoneNumber[0].Std_Code;
    
    pm.expect(actualStdCode).to.eql(expectedStdCode);
    });


//home field value validation

    pm.test("Home field value is correct", function () {

    let jsonData = pm.response.json();
    
    let expectedPhoneNumbers = JSON.parse(pm.environment.get("dynamicPhoneNumbers"));
    
    let expectedHome = expectedPhoneNumbers[0].Home;
    
    let actualHome = jsonData.data.Address[0].Permanent_Address.PhoneNumber[0].Home;
    
    pm.expect(actualHome).to.eql(expectedHome);
    });


//current_address field value validation

    pm.test("Current Address field value is correct", function () {

    let jsonData = pm.response.json();
    
    pm.expect(jsonData.data.Address[0].Current_Address).to.be.null;
    });


## Run Command:  

- Run Command for Console: 
```console 
newman run API_student.postman_collection.json -e API_student.postman_environment.json
```
- Run Command for Report: 
```console 
newman run API_student.postman_collection.json -e API_student.postman_environment.json -r cli,htmlextra
```

## Newman Report Summary:

![image](https://github.com/user-attachments/assets/f45cbba3-45c9-4e13-8f2d-4b929e69ac6c)










