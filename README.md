**Введение**
----
Для выполнения запроса к сервису обязательно необходимо передавать заголовок `Accept: application/json`. 
Для авторизованного пользователя необходимо также в заголовках передавать его access token. Формат передачи:
`Authorization: Bearer accesstoken`

**Аутентификация**
----
* **URL**
  
  /oauth/token

* **Метод**
  
  `POST`

* **Тело запроса**
  
  ```
  {
        "grant_type": "password",
        "client_id": id,
        "client_secret": "соответствующее значение",
        "username": "email@email.ru",
        "password": "pass",
        "scope": "*"
  }
  ```

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
  ```json
  {
      "token_type": "Bearer",
      "expires_in": 31536000,
      "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiIxMSIsImp0aSI6ImIyMzQ2MTc0YTBkY2Y4ZGI1ZDE4NjFlMTRlM2FmNzZmMmFmZjZkMDYzMjNmMzdiY2IyNjhiZTZhOGViZjk0NDMzMDdmOTJkYmZiODkyMzgyIiwiaWF0IjoxNTgzMTI5NTI3LCJuYmYiOjE1ODMxMjk1MjcsImV4cCI6MTYxNDY2NTUyNywic3ViIjoiMTIiLCJzY29wZXMiOlsiKiJdfQ.gYJlgBsC5c29VYOZiXe4BjvEC9twsFaCPl5dx5GzthG4V7pBS-J7-ICfxYgk6ubaJbPsGqsojObWpvNgb_xLuMyBrHlnkSSzIUZVcqU-jK1gDI9ylMJKBTh-3voSg5p9hh9LFEznPyXidDgJBPp4FcnRtYe_5Os2W2qxzUMy50tW1RcDvXv62FkKwPv2G-MEE8TogqkPQ0ULnk-0fKdPt9zDlcTHqyqLB7GaAGWpbsPUR8YKuujBQShiQrKzcopFoqyhNxq9OU3-DkwXvslgVVFqWScc25_7rd7-CE8GE6uERhfI-WvWqDND31LgPk6lSWCgUHlaayt2lSmSLNgX97Hbs_jfth6lKs1fLI35NW5Sf5VQ1r5voezYXyr3gy-SO3tEU_IejhCtWQ9pd7eGIGb5T-Vq3R1nzGeBh7FPZ3CqntDsIXsGK_j4Ny9vCS0cGRJlDFEntPvUa-_SkeXud7QKkRbAdGITo9nwoJsxZyVrwllSpyJgg6wb1rnNif3O9hft9WBtxTJuQeSnTH1SzwVn1NSH1LgQ6lipl7Ea7guHT2jS4-gCMFgbfGrCrrgGKDFM3FUA-gztMwRnIzpVFxkIFinpc-FV8VtIUcwXWG6gpwJqHW7hZX7xL4Rx0YzIzixi2R9mQoSZSjMPhLur5I39Dy_Or3HjMAfow8hMH6o",
      "refresh_token": "def50200b9cc5e675eab4557dde948314ad5d0922d747613a7111640e449f5620f08ab442ab1ec0f362d1754f65803cb1488c1c6f8a5e0d5f4bc4bf5a99f00466e84ee224ae26dbebb74780f28e7acbbfe002885d36f21beb79982b26717c00dc164fb76daa6c0d78a726f07235a20ed111752a00cf90f46666585c106509e68f8439469180bcbf19c8d4bb1b39443c9d4a8b35d666d218a5b9ac65b3074de129db1e724d8dfdb10641073f5861371888383496315266d466f6440eb6e3970b5152ea95440049484069f67319c143e8ebe5460576fcccd2123c8613d83e47f5547fc716e58fc48969054f12855dd6bc19efaa813229aea132341fa6ab5eb69c6d7cced34808c6c39e6a5a695db12da4ed253894a8c98d35a1e64554195304e6c333c0d60263ec785193d169f4bbc57ab6811ddf57249b0666f2f552bb03d77285376eb66c53c28f95c709a2f4505fa5547a345075023f814c9ea0874c7ac790e61d11d0b1d93"
  }
  ```

**Обновление access-token(зачем нужен refresh token)**
----
Refresh-token необходим для обновления access-токена до того момента, как истечет срок действия последнего

* **URL**
  
  /ouauth/token

* **Метод**
  
  `POST`

* **Тело запроса**
  
  ```
  {
        "grant_type": "refresh_token",
        "client_id": id,
        "client_secret": "соответствующее значение",
        "refresh_token": "здесь указать полученный при регистрации refresh_token",
        "scope": "*"
  }
  ```

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
  ```json
  {
      "token_type": "Bearer",
      "expires_in": 31536000,
      "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiIxMSIsImp0aSI6ImIyMzQ2MTc0YTBkY2Y4ZGI1ZDE4NjFlMTRlM2FmNzZmMmFmZjZkMDYzMjNmMzdiY2IyNjhiZTZhOGViZjk0NDMzMDdmOTJkYmZiODkyMzgyIiwiaWF0IjoxNTgzMTI5NTI3LCJuYmYiOjE1ODMxMjk1MjcsImV4cCI6MTYxNDY2NTUyNywic3ViIjoiMTIiLCJzY29wZXMiOlsiKiJdfQ.gYJlgBsC5c29VYOZiXe4BjvEC9twsFaCPl5dx5GzthG4V7pBS-J7-ICfxYgk6ubaJbPsGqsojObWpvNgb_xLuMyBrHlnkSSzIUZVcqU-jK1gDI9ylMJKBTh-3voSg5p9hh9LFEznPyXidDgJBPp4FcnRtYe_5Os2W2qxzUMy50tW1RcDvXv62FkKwPv2G-MEE8TogqkPQ0ULnk-0fKdPt9zDlcTHqyqLB7GaAGWpbsPUR8YKuujBQShiQrKzcopFoqyhNxq9OU3-DkwXvslgVVFqWScc25_7rd7-CE8GE6uERhfI-WvWqDND31LgPk6lSWCgUHlaayt2lSmSLNgX97Hbs_jfth6lKs1fLI35NW5Sf5VQ1r5voezYXyr3gy-SO3tEU_IejhCtWQ9pd7eGIGb5T-Vq3R1nzGeBh7FPZ3CqntDsIXsGK_j4Ny9vCS0cGRJlDFEntPvUa-_SkeXud7QKkRbAdGITo9nwoJsxZyVrwllSpyJgg6wb1rnNif3O9hft9WBtxTJuQeSnTH1SzwVn1NSH1LgQ6lipl7Ea7guHT2jS4-gCMFgbfGrCrrgGKDFM3FUA-gztMwRnIzpVFxkIFinpc-FV8VtIUcwXWG6gpwJqHW7hZX7xL4Rx0YzIzixi2R9mQoSZSjMPhLur5I39Dy_Or3HjMAfow8hMH6o",
      "refresh_token": "def50200b9cc5e675eab4557dde948314ad5d0922d747613a7111640e449f5620f08ab442ab1ec0f362d1754f65803cb1488c1c6f8a5e0d5f4bc4bf5a99f00466e84ee224ae26dbebb74780f28e7acbbfe002885d36f21beb79982b26717c00dc164fb76daa6c0d78a726f07235a20ed111752a00cf90f46666585c106509e68f8439469180bcbf19c8d4bb1b39443c9d4a8b35d666d218a5b9ac65b3074de129db1e724d8dfdb10641073f5861371888383496315266d466f6440eb6e3970b5152ea95440049484069f67319c143e8ebe5460576fcccd2123c8613d83e47f5547fc716e58fc48969054f12855dd6bc19efaa813229aea132341fa6ab5eb69c6d7cced34808c6c39e6a5a695db12da4ed253894a8c98d35a1e64554195304e6c333c0d60263ec785193d169f4bbc57ab6811ddf57249b0666f2f552bb03d77285376eb66c53c28f95c709a2f4505fa5547a345075023f814c9ea0874c7ac790e61d11d0b1d93"
  }
  ```

**Регистрация**
----
* **URL**
  
  /api/register

* **Метод**
  
  `POST`

* **Тело запроса**
  
  ```json
  {
    "name_manager":"Ivan Tester",
    "email": "ivan1@test.ru",
    "name_company": "Testers",
    "city": "Москва",
    "password": "foo",
    "c_password": "foo",
    "address": "Лубянка 1"
  }
  ```

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
  ```json
  {
      "token_type": "Bearer",
      "expires_in": 31536000,
      "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiIxMSIsImp0aSI6ImIyMzQ2MTc0YTBkY2Y4ZGI1ZDE4NjFlMTRlM2FmNzZmMmFmZjZkMDYzMjNmMzdiY2IyNjhiZTZhOGViZjk0NDMzMDdmOTJkYmZiODkyMzgyIiwiaWF0IjoxNTgzMTI5NTI3LCJuYmYiOjE1ODMxMjk1MjcsImV4cCI6MTYxNDY2NTUyNywic3ViIjoiMTIiLCJzY29wZXMiOlsiKiJdfQ.gYJlgBsC5c29VYOZiXe4BjvEC9twsFaCPl5dx5GzthG4V7pBS-J7-ICfxYgk6ubaJbPsGqsojObWpvNgb_xLuMyBrHlnkSSzIUZVcqU-jK1gDI9ylMJKBTh-3voSg5p9hh9LFEznPyXidDgJBPp4FcnRtYe_5Os2W2qxzUMy50tW1RcDvXv62FkKwPv2G-MEE8TogqkPQ0ULnk-0fKdPt9zDlcTHqyqLB7GaAGWpbsPUR8YKuujBQShiQrKzcopFoqyhNxq9OU3-DkwXvslgVVFqWScc25_7rd7-CE8GE6uERhfI-WvWqDND31LgPk6lSWCgUHlaayt2lSmSLNgX97Hbs_jfth6lKs1fLI35NW5Sf5VQ1r5voezYXyr3gy-SO3tEU_IejhCtWQ9pd7eGIGb5T-Vq3R1nzGeBh7FPZ3CqntDsIXsGK_j4Ny9vCS0cGRJlDFEntPvUa-_SkeXud7QKkRbAdGITo9nwoJsxZyVrwllSpyJgg6wb1rnNif3O9hft9WBtxTJuQeSnTH1SzwVn1NSH1LgQ6lipl7Ea7guHT2jS4-gCMFgbfGrCrrgGKDFM3FUA-gztMwRnIzpVFxkIFinpc-FV8VtIUcwXWG6gpwJqHW7hZX7xL4Rx0YzIzixi2R9mQoSZSjMPhLur5I39Dy_Or3HjMAfow8hMH6o",
      "refresh_token": "def50200b9cc5e675eab4557dde948314ad5d0922d747613a7111640e449f5620f08ab442ab1ec0f362d1754f65803cb1488c1c6f8a5e0d5f4bc4bf5a99f00466e84ee224ae26dbebb74780f28e7acbbfe002885d36f21beb79982b26717c00dc164fb76daa6c0d78a726f07235a20ed111752a00cf90f46666585c106509e68f8439469180bcbf19c8d4bb1b39443c9d4a8b35d666d218a5b9ac65b3074de129db1e724d8dfdb10641073f5861371888383496315266d466f6440eb6e3970b5152ea95440049484069f67319c143e8ebe5460576fcccd2123c8613d83e47f5547fc716e58fc48969054f12855dd6bc19efaa813229aea132341fa6ab5eb69c6d7cced34808c6c39e6a5a695db12da4ed253894a8c98d35a1e64554195304e6c333c0d60263ec785193d169f4bbc57ab6811ddf57249b0666f2f552bb03d77285376eb66c53c28f95c709a2f4505fa5547a345075023f814c9ea0874c7ac790e61d11d0b1d93"
  }
  ```

* **Error Response:**

  * **Code:** 422 Unprocessable Entity
    **Content:** 
    ```json
    {
      "message": "The given data was invalid.",
      "errors": {
          "email": [
              "The email field is required."
          ]
      }
    }
    ```

**Категории**
----
  Возвращает json-данные со списком категорий товаров

* **URL**

  /api/categories

* **Method:**

  `GET`
  


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
```json {
    "data": [
        {
            "id": 1,
            "value": "Пиво",
            "created_at": null,
            "updated_at": null
        },
        {
            "id": 2,
            "value": "Сидр",
            "created_at": null,
            "updated_at": null
        }
    ],
    "links": {
        "first": "http://svam.test/api/categories?page=1",
        "last": "http://svam.test/api/categories?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "path": "http://svam.test/api/categories",
        "per_page": 15,
        "to": 2,
        "total": 2
    }
}
```
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "Object doesn't exist" }`

**Товары в категории**
----
  Возвращает json-данные о товарах в категории

* **URL**

  /api/categories/:id

* **Method:**

  `GET`
  
*  **URL Params**

   **Обязательные:**
 
   `id=[integer]`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
```json {
    "type": "category",
    "id": 1,
    "value": "Пиво",
    "relationships": {
        "drinks": [
            {
                "type": "drinks",
                "drink_id": 2,
                "attributes": {
                    "name": "Prof. Elliot Schaden MD",
                    "country": "Россия",
                    "properties": {
                        "density": "12.0%",
                        "strength": "5.0%"
                    },
                    "file": [],
                    "link": "http://svam.test/api/drinks/1199"
                },
                "relationships": {
                    "packing": [
                        {
                            "id": 1196,
                            "price": "7868.0000",
                            "pack": "Кег 20L",
                            "balance": 25,
                            "1c_id": "bRLsTRNnhO",
                            "addBasket": "http://svam.test/api/basket/add/1196"
                        }
                    ]
                }                    
            },
            ],
            "first_page_url": "http://svam.test/api/categories/1?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://svam.test/api/categories/1?page=1",
            "next_page_url": null,
            "path": "http://svam.test/api/categories/1",
            "per_page": 15,
            "prev_page_url": null,
            "to": 1,
            "total": 1
        }
    }
}
```
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "Object doesn't exist" }`

  OR

  * **Code:** 403 Forbiden <br />
    **Content:** `{ error : "No access rights" }`

* **Дополнительно** 
  
  В случае с товарами реализуется следующая структура, поскольку у каждого напитка есть тары разного объема и исходя из этого разной цены за литр, то введен механизм торговых предложений. В разделе packing json-ответа указывается массив торговых предложений для товара.


**Корзина**
----
   Корзина пользователя. Для работы необходимо сгенерировать uuid клиента и передавать его в Cookie. 

* **URL**

  /api/basket

* **Method:**

  `GET`
  
* **Cookie**

   cart = {uuid-клиента}
  

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
```json 
  {
    "data": {
        "basket": [
            {
                "type": "offers",
                "id": 1,
                "user_id": 12,
                "offer_id": 11,
                "attributes": {
                    "name": "Mrs. Cortney Stark Sr.",
                    "logo": null,
                    "price": "5423.0000",
                    "packing": "Кег 20L"
                },
                "count": 1,
                "remove_basket": "http://svam.test/api/basket/delete/1"
            },
            {
                "type": "offers",
                "id": 2,
                "user_id": 12,
                "offer_id": 2,
                "attributes": {
                    "name": "Prof. Elliot Schaden MD",
                    "logo": null,
                    "price": "1595.0000",
                    "packing": "Кег 20L"
                },
                "count": 1,
                "remove_basket": "http://svam.test/api/basket/delete/2"
            }
        ],
        "summ": 7018
    },
    "links": {
        "first": "http://ec2-13-58-10-252.us-east-2.compute.amazonaws.com/api/basket?page=1",
        "last": "http://ec2-13-58-10-252.us-east-2.compute.amazonaws.com/api/basket?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "path": "http://ec2-13-58-10-252.us-east-2.compute.amazonaws.com/api/basket",
        "per_page": 15,
        "to": 6,
        "total": 6
    }
  }
```

* **Error Response:**

  * **Code:** 403 Forbiden <br />
    **Content:** `{ error : "No access rights" }`


**Добавление в корзину**
----
   Добавить торговое предложение в корзину

* **URL**

  /api/basket/add

* **Method:**

    `POST`
  
*  **URL Params**

   **Обязательные:**
 
    ***В теле запроса передается массив json. В качестве индекса массива передается идентификатор торгового предложения(поле id в массиве packings) 
    в качестве значения элемента массива передается количество добавляемых элементов***
   
   ``` json
   {
     "offer_id": count
   }
   ``` 
   

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        "message": "Item added"
    }
    ```

* **Error Response:**

  * **Code:** 403 Forbiden <br />
    **Content:** `{ error : "No access rights" }`
    
  * **Code:** 422 Unprocessable Entity <br />
    **Content:** `{ message : "Error add basket"}`
    
  * **Code:** 422 Unprocessable Entity <br />
    **Content:** `{ message: "Item not exist or balance = 0"}`

**Удаление позиции из корзины**
----
  Удалить торговое предложение из корзины

* **URL**

  /api/basket/delete/:id

* **Method:**

  `DELETE`
  
*  **URL Params**

   **Обязательные:**
 
   `id=[integer]` - id позиции в корзине

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        "message": "Delete succesfull"
    }
    ```

* **Error Response:**

  * **Code:** 404 Not Found <br />
    **Content:** `{"message": "Object doesnt exist!"}`

    OR

  * **Code:** 403 Forbidden <br />
    **Content:** `{"message": ""No access rights"}`

**Список заказов текущего пользователя**
----
  Выводит список заказов авторизованного пользователя

* **URL**

  /api/orders

* **Method:**

  `GET`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        "data": [
            {
                "id": 3,
                "status": "NW",
                "summ_price": "10464.0000",
                "date": "2020-03-27T13:22:43.000000Z",
                "items": {
                    "0": {
                        "offer_id": 1215,
                        "name": "Miss Patience Kassulke",
                        "tara": "Кег 20L",
                        "logo": null,
                        "count": 3,
                        "price": "2968.0000",
                        "summ": "8904.0000"
                    },
                    "3": {
                        "offer_id": 1216,
                        "name": "Jerry VonRueden Jr.",
                        "tara": "250г, ваккумная упаковка с zip-lock",
                        "logo": null,
                        "count": 3,
                        "price": "520.0000",
                        "summ": "1560.0000"
                    }
                },
                "link": "http://svam.test/api/orders/3"
            },
            {
                "id": 4,
                "status": "NW",
                "summ_price": "10464.0000",
                "date": "2020-03-27T14:11:34.000000Z",
                "items": {
                    "0": {
                        "offer_id": 1215,
                        "name": "Miss Patience Kassulke",
                        "tara": "Кег 20L",
                        "logo": null,
                        "count": 3,
                        "price": "2968.0000",
                        "summ": "8904.0000"
                    },
                    "3": {
                        "offer_id": 1216,
                        "name": "Jerry VonRueden Jr.",
                        "tara": "250г, ваккумная упаковка с zip-lock",
                        "logo": null,
                        "count": 3,
                        "price": "520.0000",
                        "summ": "1560.0000"
                    }
                },
                "link": "http://svam.test/api/orders/4"
            },
            }
        ],
        "links": {
            "first": "https://svam.dev.kosipov.ru/api/orders?page=1",
            "last": "https://svam.dev.kosipov.ru/api/orders?page=1",
            "prev": null,
            "next": null
        },
        "meta": {
            "current_page": 1,
            "from": 1,
            "last_page": 1,
            "path": "https://svam.dev.kosipov.ru/api/orders",
            "per_page": 15,
            "to": 4,
            "total": 4
        }
    }
    ```

* **Error Response:**

  * **Code:** 403 Forbidden <br />
    **Content:** `{"message": ""No access rights"}`

**Создать заказ**
----
  Создается заказ из тех позиций, которые указаны в корзине

* **URL**

  /api/orders/new

* **Method:**

  `POST`

* **Тело запроса**
  
  ```json
  {
    "comment": "некоторый комментарий"
  }
  ```
  Предполагается, что пользователь, при создании заказа, может оставить какой-то комментарий через этот json комментарий передается в бэк

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        "message": "Order succesfull"
    }
    ```

* **Error Response:**

  * **Code:** 403 Forbidden <br />
    **Content:** `{"message": "No access rights"}`
    
      
**Дублировать заказ**
----
  Дублируется заказ из тех позиций, которые указаны в текущем заказе

* **URL**

  /api/orders/{order_id}/duplicate

* **Method:**

  `POST`

* **Тело запроса**
  
  ```json
  {
    "comment": "некоторый комментарий"
  }
  ```
  Предполагается, что пользователь, при дублировании заказа, может оставить какой-то комментарий через этот json комментарий передается в бэк

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        "message": "Order succesfull"
    }
    ```

* **Error Response:**

  * **Code:** 403 Forbidden <br />
    **Content:** `{"message": "No access rights"}`
    
  * **Code:** 404 Not found <br />
    **Content:** `{"message": "Object doesnt exist!"}`


**Список свойств товаров**
----
  Возвращает список свойств товаров с русским комментарием и с возможными значениями для фильтрации

* **URL**

  /api/drinks/properties

* **Method:**

  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    [
        {
            "json_value": "country",
            "ru_value": "Страна",
            "values": [
                "",
                "Argentina",
                "Bhutan",
                "British Virgin Islands",
                "Canada",
                "Cape Verde",
                "Cocos (Keeling) Islands",
                "Costa Rica",
                "Fiji",
                "Greece",
                "Guadeloupe",
                "Haiti",
                "Heard Island and McDonald Islands",
                "Iceland",
                "Isle of Man",
                "Korea",
                "Lebanon",
                "Liechtenstein",
                "Mayotte",
                "Mexico",
                "Micronesia",
                "Moldova",
                "Norfolk Island",
                "Oman",
                "Pakistan",
                "Papua New Guinea",
                "Russia",
                "Saint Lucia",
                "Samoa",
                "San Marino",
                "Seychelles",
                "Sri Lanka",
                "Thailand",
                "Turkey",
                "Western Sahara"
            ],
            "type_id": "general"
        },
        {
            "json_value": "manufacturer",
            "ru_value": "Производитель",
            "values": [
                "Aspall Cyder Limited",
                "Bayerische Staatsbrauerei Weihenstephan",
                "Philip Mayer",
                "Рога и копыта"
            ],
            "type_id": "general"
        },
        {
            "json_value": "expdate",
            "ru_value": "Срок годности",
            "values": [
                "24 мес."
            ],
            "type_id": "general"
        },
        {
            "json_value": "description",
            "ru_value": "Описание",
            "values": null,
            "type_id": "general"
        },
        {
            "json_value": "style",
            "ru_value": "Стиль",
            "values": [
                "null",
                "бланш",
                "бланш1"
            ],
            "type_id": 1
        },
        {
            "json_value": "fermentation",
            "ru_value": "Тип брожения",
            "values": [
                "null",
                "верховое",
                "низовое"
            ],
            "type_id": 1
        },
        {
            "json_value": "gaz",
            "ru_value": "Газация",
            "values": [],
            "type_id": 5
        },
        {
            "json_value": "density",
            "ru_value": "Плотность",
            "values": [
                "null",
                "12.0%",
                "11.0%"
            ],
            "type_id": 1
        },
        {
            "json_value": "strength",
            "ru_value": "Крепость",
            "values": [
                "null",
                "5.0%"
            ],
            "type_id": 1
        },
        {
            "json_value": "consist",
            "ru_value": "Состав",
            "values": [
                "чай зеленый сенча"
            ],
            "type_id": 4
        }
    ]
    ```
    
    Данный метод также возможно использовать для реализаци механизма фильтрации, с целью получения фильтруемых
    свойств. В поле type_id указывается id категории товара, для которой существует данное свойство. В случае,
    если в данном поле указано "general" это означает, что данное свойство является общим для всех товаров.
    
    Также прошу заметить, что те свойства, для которых values = null не являются свойствами для фильтрации товара.
    

**Фильтрация товара**
----
  Осуществляет фильтрацию товаров по указанным свойствам.

* **URL**

  /api/categories/{id_category}/filter

* **Method:**

  `GET`

* **Example:**
    
    ```http://svam.test/api/categories/1/filter?density=12.0%&country=Russia ```

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        "data": {
            "attributes": {
                "type": "category",
                "id": 1,
                "value": "Пиво"
            },
            "relationships": {
                "drinks": {
                    "Russia": [
                        {
                            "type": "drinks",
                            "country": "Russia",
                            "id": 1200,
                            "attributes": {
                                "name": "Dr. Camryn Rolfson Jr.",
                                "price": "200.0000",
                                "properties": {
                                    "density": "12.0%",
                                    "strength": "5.0%"
                                },
                                "file": [
                                    {
                                        "logo": "http://svam.test/storage/img/pivo1.jpg"
                                    }
                                ],
                                "link": "http://svam.test/api/drinks/1200"
                            },
                            "relationships": {
                                "packing": [
                                    {
                                        "id": 1197,
                                        "price": "6243.0000",
                                        "pack": "Кег 20L",
                                        "balance": 0,
                                        "1c_id": "rGrWa3EzVW",
                                        "addBasket": "http://svam.test/api/basket/add"
                                    }
                                ]
                            }
                        }
                    ]
                }
            },
            "links": {
                "first": "http://svam.test/api/categories/1/filter?density=12.0%25&country=Russia&page=1",
                "last": "http://svam.test/api/categories/1/filter?density=12.0%25&country=Russia&page=1",
                "prev": null,
                "next": null
            },
            "meta": {
                "current_page": 1,
                "from": 1,
                "last_page": 1,
                "per_page": 15,
                "to": 1,
                "total": 1
            }
        }
    }
    ```

* **Error Response:**

  * **Code:** 422 Unprocessable Entity <br />
    **Content:** 
    ```
    {
        "message": "Property not found"
    }
    ```
