This project is a simple Java Based application applying some Business conditions which as per the following logic:

- User can reverse the string.
- User can encrypt the input string in MD5 format
- User can use any combination of the above two operations using an operation field

Assumptions :
- url will have two new parameters operation and message
- The operations are applied in sequence, i.e. the output of the first rule will serve as the input of the second rule. The numbers can also be repeated, i.e. a rule of 11 would mean reversing the string twice, resulting in no change to the string.
- Operation can only have 2 allowed values 1(Reverse) and 2(MD5 encryption)
- If the input is not in expected format, 400 error will be thrown to the user

### API Details:

- 1.> The input request and response

	URL : localhost:8080/v2/reply/11-kbzw9ru
	METHOD : GET
	Response :
	{
	    "message": "kbzw9ru"
	}

- 2.> The input request and response

	URL : localhost:8080/v2/reply/12-kbzw9ru
	METHOD : GET
	Response :
	{
	    "message": "5a8973b3b1fafaeaadf10e195c6e1dd4"
	}

- 3.> The input request and response

	URL : localhost:8080/v2/reply/22-kbzw9ru
	METHOD : GET
	Response :
	{
	    "message": "e8501e64cf0a9fa45e3c25aa9e77ffd5"
	}

### Note-> 
1. Updated the existing "RestServiceApplicationTest" test class with all the new scenarios including the negative test cases as well like empty parameters or operation having characters other than 1 and 2.
2. Added the exception handling and a Controller Advice to handle all the probable exceptions.
3. Added the logging in code.
4. Added a common Constants file for common config data.
5. Added a util folder for common utilities like MD5Util.
6. Added some default configuration like port,context,db config, log level etc in application.properties file.

## Build project

To build the project, simply run
```
./gradlew build
```

## Start project

To start the project, simply run
```
./gradlew bootRun
```

Once the service started, the endpoint will be available at `localhost:8080`, so you can make request to the service endpoint

```json
GET localhost:8080/v2/reply/11-kbzw9ru

{
    message: "kbzw9ru"
}
