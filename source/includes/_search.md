# Full Text Search
This if full text search API and it  will help you to search food items available in database .

There are different case by which a user can search a food items in a particular restaurant .

A user can search a paticular food item in a restaurant or user also has facility to search all food items of particular food category .

## Search Particular Food Item

```json
{
  "access_token":   "sample_api_access_token"
  "restaurant_token": "......."
  "search_value":   "FRIED ZUCCHINI"
}


```

```ruby
require 'unirest'

response = Unirest.get "http://localhost:3000/api/v1/restaurants/2/search", headers:{ "Accept" => "application/json" }, parameters: {search_value: "FRIED ZUCCHINI" , access_token: "sample_api_access_token", restaurant_token: ".........."}

response.raw_body
```
> The above command returns JSON structured like this:

```json
[
    {
        "id": 12,
        "name": "FRIED ZUCCHINI",
        "pos_name": "Fried Zucchini",
        "price": 6.95,
        "description": null,
        "is_out_of_stock": false,
        "item_modifiers": [],
        "food_images": [
            {
                "food_image": {
                    "id": 1,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/1/f1.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/1/thumb_f1.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 2,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/2/f2.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/2/thumb_f2.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 3,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/3/f3.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/3/thumb_f3.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 4,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/4/f4.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/4/thumb_f4.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 5,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/5/f5.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/5/thumb_f5.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 6,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/6/f6.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/6/thumb_f6.jpg"
                            }
                        }
                    }
                }
            }
        ]
    }
]
```


```ruby
[
    {
        "id": 12,
        "name": "FRIED ZUCCHINI",
        "pos_name": "Fried Zucchini",
        "price": 6.95,
        "description": null,
        "is_out_of_stock": false,
        "item_modifiers": [],
        "food_images": [
            {
                "food_image": {
                    "id": 1,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/1/f1.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/1/thumb_f1.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 2,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/2/f2.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/2/thumb_f2.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 3,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/3/f3.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/3/thumb_f3.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 4,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/4/f4.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/4/thumb_f4.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 5,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/5/f5.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/5/thumb_f5.jpg"
                            }
                        }
                    }
                }
            },
            {
                "food_image": {
                    "id": 6,
                    "image": {
                        "image": {
                            "url": "/uploads/food_image/image/6/f6.jpg",
                            "thumb": {
                                "url": "/uploads/food_image/image/6/thumb_f6.jpg"
                            }
                        }
                    }
                }
            }
        ]
    }
]
  ```

This endpoint search particular food item in a particular restaurant.

### HTTP Request

`GET  http://tastytab.com/api/v1/restaurants/2/search?access_token=sample_api_access_token&restaurant_token=......&search_value=FRIED ZUCCHINI`

### Query Parameters

Parameter | Description
--------- | -----------
search_value      | Make sure it's does not empty and it should be valid food item name .
restaurant_token  | Make sure it's not empty and it will be available in database of restaurant .

<aside class="success">
A particular food item and its complete details is fetched from database .
</aside>

## Get all food items of particular category

```json
{
  "access_token":   "sample_api_access_token"
  "restaurant_token": "..........."
  "search_value":   "Sides"
}

```

```ruby
require 'unirest'

response = Unirest.get "http://localhost:3000/api/v1/restaurants/2/search", headers:{ "Accept" => "application/json" }, parameters: {search_value: "Sides" , access_token: "sample_api_access_token" , restaurant_token: "......."}

response.raw_body
```
> The above command returns JSON structured like this:


```json

{
    "food_items": [
        {
            "food_item": {
                "id": 12,
                "name": "FRIED ZUCCHINI",
                "pos_name": "Fried Zucchini",
                "price": 6.95,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": [
                    {
                        "food_image": {
                            "id": 1,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/1/f1.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/1/thumb_f1.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 2,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/2/f2.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/2/thumb_f2.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 3,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/3/f3.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/3/thumb_f3.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 4,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/4/f4.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/4/thumb_f4.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 5,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/5/f5.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/5/thumb_f5.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 6,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/6/f6.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/6/thumb_f6.jpg"
                                    }
                                }
                            }
                        }
                    }
                ]
            }
        },
        {
            "food_item": {
                "id": 13,
                "name": "POTATO SKINS",
                "pos_name": "Potato Skins",
                "price": 7.99,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": []
            }
        },
        {
            "food_item": {
                "id": 14,
                "name": "GARLIC BREAD",
                "pos_name": "Garlic Bread",
                "price": 3.49,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": []
            }
        },
        {
            "food_item": {
                "id": 15,
                "name": "BBQ WINGS",
                "pos_name": "BBQ Wings",
                "price": 6.99,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [
                    {
                        "item_modifier": {
                            "id": 94,
                            "pos_name": "Bleu Cheese",
                            "price": null
                        }
                    },
                    {
                        "item_modifier": {
                            "id": 95,
                            "pos_name": "No Dressing",
                            "price": null
                        }
                    },
                    {
                        "item_modifier": {
                            "id": 96,
                            "pos_name": "Ranch",
                            "price": null
                        }
                    }
                ],
                "food_images": []
            }
        }
    ]
}

```

```ruby
{
    "food_items": [
        {
            "food_item": {
                "id": 12,
                "name": "FRIED ZUCCHINI",
                "pos_name": "Fried Zucchini",
                "price": 6.95,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": [
                    {
                        "food_image": {
                            "id": 1,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/1/f1.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/1/thumb_f1.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 2,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/2/f2.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/2/thumb_f2.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 3,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/3/f3.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/3/thumb_f3.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 4,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/4/f4.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/4/thumb_f4.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 5,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/5/f5.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/5/thumb_f5.jpg"
                                    }
                                }
                            }
                        }
                    },
                    {
                        "food_image": {
                            "id": 6,
                            "image": {
                                "image": {
                                    "url": "/uploads/food_image/image/6/f6.jpg",
                                    "thumb": {
                                        "url": "/uploads/food_image/image/6/thumb_f6.jpg"
                                    }
                                }
                            }
                        }
                    }
                ]
            }
        },
        {
            "food_item": {
                "id": 13,
                "name": "POTATO SKINS",
                "pos_name": "Potato Skins",
                "price": 7.99,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": []
            }
        },
        {
            "food_item": {
                "id": 14,
                "name": "GARLIC BREAD",
                "pos_name": "Garlic Bread",
                "price": 3.49,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [],
                "food_images": []
            }
        },
        {
            "food_item": {
                "id": 15,
                "name": "BBQ WINGS",
                "pos_name": "BBQ Wings",
                "price": 6.99,
                "description": null,
                "is_out_of_stock": false,
                "item_modifiers": [
                    {
                        "item_modifier": {
                            "id": 94,
                            "pos_name": "Bleu Cheese",
                            "price": null
                        }
                    },
                    {
                        "item_modifier": {
                            "id": 95,
                            "pos_name": "No Dressing",
                            "price": null
                        }
                    },
                    {
                        "item_modifier": {
                            "id": 96,
                            "pos_name": "Ranch",
                            "price": null
                        }
                    }
                ],
                "food_images": []
            }
        }
    ]
}

```


This endpoint search all food items of particular category in a particular restaurant.
### HTTP Request

`GET http://localhost:3000/api/v1/restaurants/2/search?access_token=sample_api_access_token&restaurant_token=........&search_value=Sides`

### URL Parameters

Parameter | Description
--------- | -----------
search_value | It should be valid food item name or valid category name
restaurant_token  | Make sure it's not empty and it will be available in database of restaurant .

<aside class="success">
All food items and their details of particular category is fetched from database .
</aside>
