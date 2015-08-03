# Order

This is order API and it  will help you to create new order on application database and ethor also , apart from creation of new order we also have api to push food items , quantity and its item modifiers in existing order .

## New Order Api

```json
{
  "access_token":                       "sample_api_access_token"
  "food_items[16][quantity]"            "8"
  "food_items[16][item_modifiers][]"    "380"
  "food_items[16][item_modifiers][]"    "381"
}


```

```ruby
require 'unirest'

response = Unirest.post "http://192.34.57.207/api/v1/add_food_items?access_token=sample_api_access_token", headers:{ "Accept" => "application/json" }, parameters: {"food_items"=>{"16"=>{"quantity"=>"5", "item_modifiers"=>["380", "381"]} } }



response.raw_body
```
> The above command returns JSON structured like this:

```json
{
    "order_id": 300,
    "pos_id": "ZZGDI0F01K",
    "order_type": "dine_in",
    "order_status": "STAGED",
    "order_date": "2015-08-03T07:30:57.520Z",
    "restaurant": {
        "restaurant_id": 9,
        "name": "subway"
    },
    "order_items": [
        {
            "order_item": {
                "food_item_id": 16,
                "quantity": 5,
                "pos_variant_name": "default",
                "pos_variant_id": "UUP6RY8HM2",
                "total": 55,
                "modifiers": [
                    {
                        "modifier_id": "UD3XRKVR1E",
                        "modifier_name": "sprite"
                    },
                    {
                        "modifier_id": "IBYFR10BAQ",
                        "modifier_name": "tomato"
                    }
                ]
            }
        }
    ]
}

```


```ruby
{
    "order_id": 300,
    "pos_id": "ZZGDI0F01K",
    "order_type": "dine_in",
    "order_status": "STAGED",
    "order_date": "2015-08-03T07:30:57.520Z",
    "restaurant": {
        "restaurant_id": 9,
        "name": "subway"
    },
    "order_items": [
        {
            "order_item": {
                "food_item_id": 16,
                "quantity": 5,
                "pos_variant_name": "default",
                "pos_variant_id": "UUP6RY8HM2",
                "total": 55,
                "modifiers": [
                    {
                        "modifier_id": "UD3XRKVR1E",
                        "modifier_name": "sprite"
                    },
                    {
                        "modifier_id": "IBYFR10BAQ",
                        "modifier_name": "tomato"
                    }
                ]
            }
        }
    ]
}
```

This endpoint create a fresh order on application database and ethor as well . It will create a new order with food items and book a table for that customer .

|---- Steps ----|

1.  Create a new order on application as well as on ethor  (we have to send parameters to create new order like food items ,
    quantity , item modifiers)

2.  Book a table .

3.  It will only book a table whose availability is true .


### HTTP Request

`POST  http://192.34.57.207/api/v1/orders?access_token=sample_api_access_token`

### Query Parameters

Parameter | Description
--------- | -----------
food_item_id | Make sure it's does not empty  .
quantity | Make sure it's does not empty .
item modifier | Make sure it may or may not be empty  .



<aside class="success">
Order is created and its associated  food items is also added on application database and ethor .
</aside>
