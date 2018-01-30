# Getting started

The MessageMedia Lookups API provides a number of endpoints for validating the phone numbers you’re sending to by checking their validity, type and carrier records.

## How to Build


You must have Python ```2 >=2.7.9``` or Python ```3 >=3.4``` installed on your system to install and run this SDK. This SDK package depends on other Python packages like nose, jsonpickle etc. 
These dependencies are defined in the ```requirements.txt``` file that comes with the SDK.
To resolve these dependencies, you can use the PIP Dependency manager. Install it by following steps at [https://pip.pypa.io/en/stable/installing/](https://pip.pypa.io/en/stable/installing/).

Python and PIP executables should be defined in your PATH. Open command prompt and type ```pip --version```.
This should display the version of the PIP Dependency Manager installed if your installation was successful and the paths are properly defined.

* Using command line, navigate to the directory containing the generated files (including ```requirements.txt```) for the SDK.
* Run the command ```pip install -r requirements.txt```. This should install all the required dependencies.

![Building SDK - Step 1](https://apidocs.io/illustration/python?step=installDependencies&workspaceFolder=MessageMediaLookups-Python)


## How to Use

The following section explains how to use the MessageMediaLookups SDK package in a new project.

### 1. Open Project in an IDE

Open up a Python IDE like PyCharm. The basic workflow presented here is also applicable if you prefer using a different editor or IDE.

![Open project in PyCharm - Step 1](https://apidocs.io/illustration/python?step=pyCharm)

Click on ```Open``` in PyCharm to browse to your generated SDK directory and then click ```OK```.

![Open project in PyCharm - Step 2](https://apidocs.io/illustration/python?step=openProject0&workspaceFolder=MessageMediaLookups-Python)     

The project files will be displayed in the side bar as follows:

![Open project in PyCharm - Step 3](https://apidocs.io/illustration/python?step=openProject1&workspaceFolder=MessageMediaLookups-Python&projectName=message_media_lookups)     

### 2. Add a new Test Project

Create a new directory by right clicking on the solution name as shown below:

![Add a new project in PyCharm - Step 1](https://apidocs.io/illustration/python?step=createDirectory&workspaceFolder=MessageMediaLookups-Python&projectName=message_media_lookups)

Name the directory as "test"

![Add a new project in PyCharm - Step 2](https://apidocs.io/illustration/python?step=nameDirectory)
   
Add a python file to this project with the name "testsdk"

![Add a new project in PyCharm - Step 3](https://apidocs.io/illustration/python?step=createFile&workspaceFolder=MessageMediaLookups-Python&projectName=message_media_lookups)

Name it "testsdk"

![Add a new project in PyCharm - Step 4](https://apidocs.io/illustration/python?step=nameFile)

In your python file you will be required to import the generated python library using the following code lines

```Python
from message_media_lookups.message_media_lookups_client import MessageMediaLookupsClient
```

![Add a new project in PyCharm - Step 4](https://apidocs.io/illustration/python?step=projectFiles&workspaceFolder=MessageMediaLookups-Python&libraryName=message_media_lookups.message_media_lookups_client&projectName=message_media_lookups&className=MessageMediaLookupsClient)

After this you can write code to instantiate an API client object, get a controller object and  make API calls. Sample code is given in the subsequent sections.

### 3. Run the Test Project

To run the file within your test project, right click on your Python file inside your Test project and click on ```Run```

![Run Test Project - Step 1](https://apidocs.io/illustration/python?step=runProject&workspaceFolder=MessageMediaLookups-Python&libraryName=message_media_lookups.message_media_lookups_client&projectName=message_media_lookups&className=MessageMediaLookupsClient)


## How to Test

You can test the generated SDK and the server with automatically generated test
cases. unittest is used as the testing framework and nose is used as the test
runner. You can run the tests as follows:

  1. From terminal/cmd navigate to the root directory of the SDK.
  2. Invoke ```pip install -r test-requirements.txt```
  3. Invoke ```nosetests```

## Initialization

### Authentication
In order to setup authentication and initialization of the API client, you need the following information.

| Parameter | Description |
|-----------|-------------|
| basic_auth_user_name | The username to use with basic authentication |
| basic_auth_password | The password to use with basic authentication |



API client can be initialized as following.

```python
# Configuration parameters and credentials
basic_auth_user_name = 'basic_auth_user_name' # The username to use with basic authentication
basic_auth_password = 'basic_auth_password' # The password to use with basic authentication

client = MessageMediaLookupsClient(basic_auth_user_name, basic_auth_password)
```



# Class Reference

## <a name="list_of_controllers"></a>List of Controllers

* [LookupsController](#lookups_controller)

## <a name="lookups_controller"></a>![Class: ](https://apidocs.io/img/class.png ".LookupsController") LookupsController

### Get controller instance

An instance of the ``` LookupsController ``` class can be accessed from the API Client.

```python
 lookups_controller = client.lookups
```

### <a name="get_lookup_a_phone_number"></a>![Method: ](https://apidocs.io/img/method.png ".LookupsController.get_lookup_a_phone_number") get_lookup_a_phone_number

> Use the Lookups API to find information about a phone number.
> A request to the lookups API has the following format:
> ```/v1/lookups/phone/{phone_number}?options={carrier,type}```
> The `{phone_number}` parameter is a required field and should be set to the phone number to be looked up.
> The options query parameter can also be used to request additional information about the phone number.
> By default, a request will only return the `country_code` and `phone_number` properties in the response.
> To request details about the the carrier, include `carrier` as a value of the options parameter.
> To request details about the type, include `type` as a value of the options parameter. To pass multiple values
> to the options parameter, use a comma separated list, i.e. `carrier,type`.
> A successful request to the lookups endpoint will return a response body as follows:
> ```json
> {
>   "country_code": "AU",
>   "phone_number": "+61491570156",
>   "type": "mobile",
>   "carrier": {
>     "name": "Telstra"
>   }
> }
> ```
> Each property in the response body is defined as follows:
> - ```country_code``` ISO ALPHA 2 country code of the phone number
> - ```phone_number``` E.164 formatted phone number
> - ```type``` The type of number. This can be ```"mobile"``` or ```"landline"```
> - ```carrier``` Holds information about the specific carrier (if available)
>   - ```name``` The carrier's name as reported by the network

```python
def get_lookup_a_phone_number(self,
                                  phone_number,
                                  options=None)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| phoneNumber |  ``` Required ```  | The phone number to be looked up |
| options |  ``` Optional ```  | TODO: Add a parameter description |



#### Example Usage

```python
phone_number = '+61491570156'
options = 'carrier,type'

result = lookups_controller.get_lookup_a_phone_number(phone_number, options)

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 404 | Number was invalid |




[Back to List of Controllers](#list_of_controllers)



