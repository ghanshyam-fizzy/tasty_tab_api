# Order

This is order API and it  will help you to create new order on application database and ethor also , apart from creation of new order we also have api to push food items , quantity and its item modifiers in existing order .

## New Order Api

```json
{
  "access_token":                       "sample_api_access_token"
  "restaurant_token"                    "............"
  "food_items[16][quantity]"            "8"
  "food_items[16][item_modifiers][]"    "380"
  "food_items[16][item_modifiers][]"    "381"
}


```

```ruby
require 'unirest'

response = Unirest.post "http://192.34.57.207/api/v1/add_food_items?access_token=sample_api_access_token&restaurant_token=......", headers:{ "Accept" => "application/json" }, parameters: {"food_items"=>{"16"=>{"quantity"=>"5", "item_modifiers"=>["380", "381"]} } }



response.raw_body
```
> The above command returns JSON structured like this:

```json
{
    "order_id": 19,
    "status": "success"
}
```


```ruby
{
    "order_id": 19,
    "status": "success"
}
```



This endpoint create a fresh order on application database and ethor as well . It will create a new order with food items and book a table for that customer .

|---- Steps ----|

1.  Create a new order on application as well as on ethor  (we have to send parameters to create new order like food items ,
    quantity , item modifiers)

2.  Book a table .

3.  It will only book a table whose availability is true .


### HTTP Request

`POST  http://192.34.57.207/api/v1/add_food_items?access_token=sample_api_access_token&restaurant_token=..........`

### Query Parameters

Parameter | Description
--------- | -----------
food_item_id | Make sure it's does not empty  .
quantity | Make sure it's does not empty .
item modifier | Make sure it may or may not be empty  .



<aside class="success">
Order is created and its associated  food items is also added on application database and ethor .
</aside>

## Add food items to existing order

```json
{
  "access_token":                       "sample_api_access_token",
  "food_items[16][quantity]":            "8",
  "food_items[16][item_modifiers][]":    "380",
  "food_items[16][item_modifiers][]":    "381",
  "order_id":                            21
}

```

```ruby
require 'unirest'

response = Unirest.post "http://192.34.57.207/api/v1/add_food_items?access_token=sample_api_access_token", headers:{ "Accept" => "application/json" }, parameters: {"food_items"=>{"16"=>{"quantity"=>"5", "item_modifiers"=>["380", "381"]} ,"order_id"=>"21" } }

response.raw_body
```


> The above command returns JSON structured like this:

```json
{
    "order_id": 21,
    "status": "success"
}
```


```ruby
{
    "order_id": 21,
    "status": "success"
}
```



This API is used to add extra food item in existing order , request is same as we have in create new order Api only we have to add order id of order in which we want to add food items , first it will search that order in the database and if it is found then it will add the food items in that order or otherwise it will create the new order .

### HTTP Request

`POST  http://192.34.57.207/api/v1/orders?access_token=sample_api_access_token`

### Query Parameters

Parameter | Description
--------- | -----------
food_item_id | Make sure it's does not empty  .
quantity | Make sure it's does not empty .
item modifier | Make sure it may not be empty  .
order_id | It may or may not be empty  .

## Update existing food items in order


```json
{
  "access_token":                       "sample_api_access_token",
  "food_items[16][quantity]":            "8",
  "food_items[16][item_modifiers][]":    "380",
  "food_items[16][item_modifiers][]":    "381",
  "order_id":                            21
}

```

```ruby
require 'unirest'

response = Unirest.post "http://192.34.57.207/api/v1/add_food_items?access_token=sample_api_access_token", headers:{ "Accept" => "application/json" }, parameters: {"food_items"=>{"16"=>{"quantity"=>"5", "item_modifiers"=>["380", "381"]} ,"order_id"=>"21" } }

response.raw_body
```


> The above command returns JSON structured like this:

```json
{
    "order_id": 21,
    "status": "success"
}
```


```ruby
{
    "order_id": 21,
    "status": "success"
}
```


This API is used to update the existing food item in existing order , request is same as we have in create new order Api only we have to add order id of order in which we want to add food items , first it will search that order in the database and part from order id we also have to sent the the food item id , then it will search that food item in existing order and if food item is found it will update the food item .

### HTTP Request

`POST  http://192.34.57.207/api/v1/orders?access_token=sample_api_access_token`

### Query Parameters

Parameter | Description
--------- | -----------
food_item_id | Make sure it's does not empty  .
quantity | Make sure it's does not empty .
item modifier | Make sure it may not be empty  .
order_id | It may or may not be empty  .
