# App Sync


## Sync Restaurant Data

```json
{
  "access_token": "sample_api_access_token"
  "restaurant" {
    "id": 1
  }
}
```

```ruby
require 'unirest'

response = Unirest.get "http://localhost:3000/api/v1/24/app_sync.json?access_token=sample_api_access_token"

response.raw_body
```

> The above command returns JSON structured like this:

```json
{
  "id": 24,
  "name": "Burger King",
  "logo": {
    "logo": {
      "url": "/images/fallback/default.png",
      "thumb": {
        "url": "/images/fallback/thumb_default.png"
      }
    }
  }
  "Remove remaining hash for brevity.."
}
```

```ruby
{
  "id": 24,
  "name": "Burger King",
  "logo" {
    "logo" {
      "url": "/images/fallback/default.png",
      "thumb" {
        "url": "/images/fallback/thumb_default.png"
      }
    }
  }
  "Remove remaining hash for brevity.."
}
```


The App Sync API will return entire restaurant hash in a nested & easy to parse format. This hash includes restaurant menus, menu categories, foost


These hash may contain duplicate data, so remember to remove any redundant data.

### HTTP Request

`GET http://tastytab.com/api/v1/:id/app_sync?access_token=sample_api_access_token`


Replace `:id` with restaurant id. Also, remember to replace access_token with your own access_token.


Data will only be sent if it has changed since last sync. We continuously run sync task in background to make sure everything stays in sync.

To optimize things try to set sync interval & sync time in accounts setting, and make sync request accordingly.



## Sync Restaurant Data With Android

```json
{
{
 "access_token": "sample_api_access_token"
}
```

```ruby
require 'unirest'

response = Unirest.get "http://192.34.57.207/api/v1/restaurants/app_sync_with_android?access_token=sample_api_access_token"

response.raw_body
```
> The above command returns JSON structured like this:


```json
{
    "id": 2,
    "name": "sagar ratna",
    "logo": {
        "logo": {
            "url": "http://192.34.57.207/uploads/restaurant/logo/2/f2.jpg",
            "thumb": {
                "url": "http://192.34.57.207/uploads/restaurant/logo/2/thumb_f2.jpg"
            }
        }
    },
    "pos_sync_interval": "Daily",
    "android_app_sync_token": "1435148022",
    "Remove remaining hash for brevity.."
}

```

```ruby

{
    "id": 2,
    "name": "sagar ratna",
    "logo": {
        "logo": {
            "url": "http://192.34.57.207/uploads/restaurant/logo/2/f2.jpg",
            "thumb": {
                "url": "http://192.34.57.207/uploads/restaurant/logo/2/thumb_f2.jpg"
            }
        }
    },
    "pos_sync_interval": "Daily",
    "android_app_sync_token": "1435148022",
    "Remove remaining hash for brevity.."
}

```
The App Sync API will return entire restaurant hash in a nested & easy to parse format. This hash includes restaurant menus, menu categories, food, item modifier groups with item modifiers

These hash may contain duplicate data, so remember to remove any redundant data.

### HTTP Request

`GET http://192.34.57.207/api/v1/restaurants/app_sync_with_android?access_token=sample_api_access_token`

Data will only be sent if it has changed since last sync. To check this it has android app sync token in restaurant table which will be updated whenever some changes made to food item table or any other tables such as food image  , menus , categories , review , tables , item modifiers etc .

At the time of syncing the android developer has to enter android app sync token , if token matche with the token present in the database then there would no changes made , but if the token does not match or android developer does not provide any token then it will return entrie restaurant hash ..
