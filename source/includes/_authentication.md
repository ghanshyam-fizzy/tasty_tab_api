# Authentication

To interact with TastyTab's API you need to authenticate yourself by including provided `access_token` and `restaurant_token` via query string parameter.
Restaurant_token will be available in restaurant database.
Some sensitive requests also require `waiter_token` & `manager_token`.

### HTTP REQUEST
`GET http://www.tastytab.com/api/v1/cutomers?access_token=sample_api_access_token`


```json
{
  "access_token": "sample_api_access_token"
  "customer" {
    "name": "Rahul"
  }
}
```

```ruby
require 'httparty'

response = HTTParty.get('http://www.tastytab.com/api/v1/?access_token=sample_api_access_token&restaurant_token=..........')

response.body
```


> Make sure to replace sample access token `sample_api_access_token` with your API key and `restaurant token` according to restaurant because with every new restaurant restaurant token is generated.

```json
{
  "success": "Success"
}
```

```ruby
{
  "success": "Success"
}
```


TastyTab uses access token to allow access to the API. You can register a new TastyTab access token by contacting us.

TastyTab expects for the access_token to be included in all API requests to the server in a header that looks like the following:

`access_token: "sample_api_access_token"`

<aside class="notice">
You must replace <code>sample_api_access_token</code> with your personal access token.
</aside>
