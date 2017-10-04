                                               # Target Interview - USA

## __Case Study:  myRetail RESTful service__

myRetail is a rapidly growing company with HQ in Richmond, VA and over 200 stores across the east coast. myRetail wants to make its internal data available to any number of client devices, from myRetail.com to native mobile apps. 
The goal for this exercise is to create an end-to-end Proof-of-Concept for a products API, which will aggregate product data from multiple sources and return it as JSON to the caller. 
Your goal is to create a RESTful service that can retrieve product and price details by ID. The URL structure is up to you to define, but try to follow some sort of logical convention.
Build an application that performs the following actions: 
Responds to an HTTP GET request at /products/{id} and delivers product data as JSON (where {id} will be a number. 
Example product IDs: 15117729, 16483589, 16696652, 16752456, 15643793) 
Example response: {"id":13860428,"name":"The Big Lebowski (Blu-ray) (Widescreen)","current_price":{"value": 13.49,"currency_code":"USD"}}
Performs an HTTP GET to retrieve the product name from an external API. (For this exercise the data will come from redsky.target.com, but let’s just pretend this is an internal resource hosted by myRetail) 

Example: http://redsky.target.com/v2/pdp/tcin/13860428?excludes=taxonomy,price,promotion,bulk_ship,rating_and_review_reviews,rating_and_review_statistics,question_answer_statistics

Reads pricing information from a NoSQL data store and combines it with the product id and name from the HTTP request into a single response. 

BONUS: Accepts an HTTP PUT request at the same path (/products/{id}), containing a JSON request body similar to the GET response, and updates the product’s price in the data store. 

*********************************************************************************************************************************
# __Solution:__

## __MyRetail API Solution provides the ability to:__

<ol>
  <li>Retrieve product and price information by Product Id.</li>
  <li>Update the price information in the database.</li>
</ol>

__Method__  __Request__
GET    /products/{id}
PUT    /products/{id}

###### __Technology Stack:__

Spring Boot : 
	https://start.spring.io/
	https://spring.io/guides/gs/serving-web-content/ 
Feign:
Declarative REST Client: Feign creates a dynamic implementation of an interface decorated with JAX-RS or Spring MVC annotations.
	https://cloud.spring.io/spring-cloud-netflix/ 
MongoDB:
	https://www.mongodb.com/what-is-mongodb 

Maven:
	https://maven.apache.org/ 
Mokito/Junit:
	http://site.mockito.org/ 
Postman: 
	https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?hl=en 

###### __Setup instructions:__

1. Java 1.7
2. Eclipse  Mars: http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/mars2
3. Install Mongo DB: https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/
4. Install Maven: https://www.mkyong.com/maven/how-to-install-maven-in-windows/ 
5. Github:
Download project from the following git repository
https://github.com/rohitdec01/myRetail 

a) Download as a ZIP file   OR
b) Clone the git project from git-bash or command prompt (You must have git setup)

6. Import the project into eclipse –   File->import


###### __Test the project:__

Test cases are present on the following directory. I have written some test cases for controller class and service  class using mokito. I am using mokitoformockdata.

C:\WORK_ENV\workspace\myRetail\src\test\java

To run the test  Go to project folder and trigger following command on the command prompt ( or gitbash). 
mvn test.

###### __To run the application:__

Run mongo DB from the command prompt.  And test  ---  http://localhost:27017/  (default port)
Go to the project folder and trigger the command:

mvn spring-boot:run 

###### __Check the http Request:__

GET:  With Valid product ID  (http://localhost:8080/products/13860428)
![getvalidproduct](https://user-images.githubusercontent.com/12552208/31157764-3cd0c088-a88b-11e7-9f0a-5c84f0d191a8.png)


GET:  With  invalid product ID  (http://localhost:8080/products/138604281)
![getinvalidproduct](https://user-images.githubusercontent.com/12552208/31157806-901a2676-a88b-11e7-92b1-7fbcdffa4ca6.png)




PUT Request: With Valid product Id  (http://localhost:8080/products/13860428)
![putvalidproduct](https://user-images.githubusercontent.com/12552208/31157845-d4e7a5bc-a88b-11e7-938e-616a23447775.png)


PUT Request: With Invalid product Id  (http://localhost:8080/products/138604281)
![putinvalidproduct](https://user-images.githubusercontent.com/12552208/31157878-0b1f975c-a88c-11e7-8c5a-b242315ca8c8.png)



