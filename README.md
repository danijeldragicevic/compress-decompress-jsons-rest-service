# Compress/Decompress JSONs API
Mule4 example app. Able to receive and produce compressed files.

Service is able to:
- receive JSON data, compress it to ZIP format and store in local file;
- receive zipped data, decompress it to JSON format and store in local file.

# Technology
- RAML 1.0
- Mule 4.4.0EE

# To run application: 
Checkout from this repository and import into Anypoint Studio 7.X.X.

# Exposed endpoints:
By default, service will run on **http://localhost:8081** </br>
Following endpoints will be exposed:
| Methods | Urls            | Action                                                  |
|---------|-----------------|---------------------------------------------------------|
| GET     | /console        | Gives access to the generated documentation for the API |
| POST    | /api/compress   | Compress payload and store to the local directory       |
| POST    | /api/decompress | Decompress payload and store to the local dir           |

# Examples
**Example 1:** GET http://localhost:8081/console/ </br>
Run in browser or REST client tool (e.g. Insomnia, Postman...) to open generated documentation for the API. </br>
It gives opportunity to interact with the API by setting the expected Contetn-Type and payload. </br>

![Screenshot 2023-02-16 at 11 51 07](https://user-images.githubusercontent.com/82412662/219344995-4ad77936-1ae7-4d62-b8a4-6dace286826f.png)

**Example 2:** POST http://localhost:8081/api/compress </br>
Setting of Content-Type is mandatory. In this case we have to set it to the "application/json" type. </br>
Request body:
```
[
  {
    "firstName": "Jane",
    "lastName": "Doe"
  },
  {
    "firstName": "Judy",
    "lastName": "Doe"
  },
  {
    "firstName": "John",
    "lastName": "Doe"
  },
  {
    "firstName": "James",
    "lastName": "Doe"
  }
]
```
Response: 200 OK. <br/>
Response body:
```
{
    "message": "Successfully processed"
}
```
As result, compressed file with the payload content will be created on the "src/main/resources/output" path. </br>

**Example 2:** POST http://localhost:8081/api/decompress </br>
Setting of Content-Type is mandatory. In this case we have to set it to the "application/zip" type. </br>
To place compressed file in the payload it is most convenient to use some REST client tool. </br> 

<img width="856" alt="Screenshot 2023-02-16 at 12 02 18" src="https://user-images.githubusercontent.com/82412662/219347558-c5b7e34f-1056-446e-9a31-7885788b5386.png">

Response: 200 OK. <br/>
Response body:
```
{
    "message": "Successfully processed"
}
```
As result, decompressed file with the payload content will be created on the "src/main/resources/output" path. </br>

# Licence
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
