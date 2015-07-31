# Customers

## Registration

```json
{
  "access_token": "sample_api_access_token",
  "customer": {
    "email": "dinesh_tasty@tastytab.com",
    "password": "password",
    "first_name": "princi",
    "last_name":  "narula",
    "password_confirmation": "password",
    "phone_Area_code": "101",
    "phone_number": "99901990",
    "birth_date": "1989-08-26"
  }
}
```

```ruby
require 'unirest'

response = Unirest.post "http://192.34.57.207/api/v1/customers/registrations?access_token=sample_api_access_token", headers:{ "Accept" => "application/json" }, parameters: {customer: {first_name: "princi", last_name: "narula", email: "android_tastytab@tester.com", password: "password", birth_date: " 26/08/1989" , phone_area_code: "101" , phone_number: "99901990" , password_confirmation: "password"}}

response.raw_body
```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "auth_token": "d4xdUCP31qV-JY_FsmYo"
}
```

```ruby
{
    "status": "success",
    "auth_token": "d4xdUCP31qV-JY_FsmYo"
}
```

We have an API to  register a customer on the application.

|--------- Important points to create new customers ----------|

1 . First there are two ways to import customer in the application


      i)  Import customer while syncing from eThor .

      ii) User has a facility to register themself as a customer .

      iii)  When user register on application , they are required to fill the various fields such as : first name , last name , birth date , email address , password ,phone code , phone number ,password_confirmation .

      iv) Email address , password , phone code , phone number are the mandatory fields

      v) If customer with particular details are not present on the eThor , then it will also create the customer on eThor also .

      vi) Every customer has unique customer id on eThor , whenever a customer registration is done ,customer is also create on the eThor on background and once the customer is created on ethor , it will return the customer ID as (pos_customer_id) and save this ID in customer table .

      vi) In case customer register themself on application , and if customer is already present on the eThor , then it will return their unique customer id and save in the application's database .

      vii) Every customer can be associated with one or more restaurant at a time ,



### HTTP Request

POST http://192.34.57.207/api/v1/customers/registrations?access_token=sample_api_access_token

### POSTMAN Request :

http://192.34.57.207/api/v1/customers/registrations?access_token=sample_api_access_token

customer[first_name]              :   dinesh

customer[last_name]               :  singh

customer[birth_date]              :  26/08/1989

customer[password]                :  password

customer[email]                   :  dinesh_tasty@tastytab.com

customer[phone_area_code]         :  101

customer[phone_number]            :  99901990

customer[password_confirmation]   : password

### Query Parameters

Parameter | Description
--------- | -----------
customer[email] | Make sure it doesn’t already exists.
customer[first_name] | It should contain the first name of customer , it cannot be blank.
customer[last_name] | It should contain the last name of customer , it cannot be blank.
customer[birth_date] | It should contain the birth date of customer.
customer[password] | Password must be atleast 6 characters long.
customer[phone_area_code] | It cannot be blank.
customer[phone_number] | It cannot be blank.
customer[password_confirmation]  | it should be same as password .

<aside class="success">
Customer has been registered for a particular restaurant (restaurant is based on access token ).
</aside>

## Create a new session

```json
{
  "access_token": "sample_api_access_token",
  "customer":{
    "email": "ghanshyamanand1989@gmail.com",
    "password": "password"
  }
}
```

```ruby
require 'unirest'

response = Unirest.post "http://192.34.57.207/api/v1/customers/sessions?access_token=sample_api_access_token", headers:{ "Accept" => "application/json" }, parameters: {customer: {email: "ghanshyamanand1989@gmail.com", password: "password"}}
response.raw_body
```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "auth_token": "G9wSKUF87nafWigpfKSY"
}
```

```ruby
{
    "status": "success",
    "auth_token": "G9wSKUF87nafWigpfKSY"
}
```


This is login api , this endpoint return the unique auth_token of customer , which should be used to make all future customer related requests and apart from access_token it also return the status that can be success or failure .



### HTTP Request

`http://192.34.57.207/api/v1/customers/sessions?access_token=sample_api_access_token`

### URL Parameters

Parameter | Description
--------- | -----------
customer[email] | Registered email id of the customer
customer[password] | Associated password

## Change Password



```ruby
require 'unirest'

response = Unirest.post "http://192.34.57.207/api/v1/customers/customers/password", headers:{ "Accept" => "application/json" }, parameters: {customer: {email: "ssuser@example.com"}}

response.raw_body

```

> NO JSON IS RETURNED:



```ruby
this endpoint will not return any json , It will only send mail from where customer can change their password
```


This endpoint is use to reset the password of the customer , Customer has a facility to reset his password if he forgots the password .

To change the password , customer has to click on the forgort password link and then he has to enter his email address and submit

Email is sent to the customer with a link , customer can change his password by clicking on that link .

<aside class="warning">only registered customer can change their password</aside>

### HTTP Request

`http://192.34.57.207/api/v1/customers/customers/password`

### POSTMAN Request :

http://192.34.57.207/api/v1/customers/customers/password

customer[email]              :   android_tastytab@tester.com


### URL Parameters

Parameter | Description
--------- | -----------
customer[email] | Registered email id of the customer

## Login Via Facebook & Gmail

```json
{
  "access_token": "sample_api_access_token",
  "customer":{
    "provider": "facebook / gmail",
    "uid": "101",
    "email": "ghanshyamanand1989@gmail.com",
    "name": "Full Name"
  }
}
```

```ruby
require 'unirest'

response = Unirest.post "http://192.34.57.207/api/v1/social_auth?access_token=sample_api_access_token", headers:{ "Accept" => "application/json" }, parameters: {customer: {name: "princi narula", email: "princi_android_tastytab@tester.com", provider: "gmail" , uid: "10101"}}

response.raw_body
```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "auth_token": "d4xdUCP31qV-JY_FsmYo"
}
```

```ruby
{
    "status": "success",
    "auth_token": "d4xdUCP31qV-JY_FsmYo"
}
```

This api is used to login from customer's facebook and gmail account in this case customer can login into application by his facebook or gmail account ,
first customer will click on the button or link "login by facebook" or "login by gmail" and it will redirect to social site login page where he has to enter his credentials

then it must return some data in json format to android app and then that data is posted on the following URL and then it would create customer on database and it will direct login into the application .




### HTTP Request

POST http://192.34.57.207/api/v1/social_auth?access_token=sample_api_access_token

### POSTMAN Request :

POST http://192.34.57.207/api/v1/customers/registrations?access_token=sample_api_access_token

### URL Parameters

Parameter | Description
--------- | -----------
customer[provider]    | It could be "facebook" or "gmail"
customer[uid]         | Customer unique ID on social site account
customer[email]       | Registered email id of the customer
customer[name]        | Full name of customer on social site




<aside class="success">
This json data is use to create customer , it will return status as 'success' and customer's unique auth_token .
</aside>
