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
        "name":"Petr Tester",
        "email": "petr@test.ru",
        "name_company": "ООО Моя оборона",
        "phone": "+79991234567",
        "dogovor": "456Н-2189"
    }
  ```
  
Прошу заметить, что необязательно придерживаться какого-либо определенного формата при ввода номера телефона.
Допускается  8904..... либо 904..... либо 7904.... любой введенный номер будет приведен к формату
+7904..... Также встроена верификация телефонного номера, если будет попытка ввести
несуществующий номер телефона(например указан неверный код города), то будет возвращена ошибка  

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
  ```json
  {
      "name": "Petr Tester",
      "password": "mZ9H99a5",
      "e-mail": "petr@test.ru",
      "phone": "+79991234567",
      "organization": "ООО Моя оборона"
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

**Сброс пароля**
----
  Находит пользователя по введенному email и отправляет сообщение с ссылкой и кодом для сброса пароля
  На сегодняшний день в функционале есть ограничения, сброс возможен только у пользователя test@kosipov.ru
  это связано с тем, что сервер приема-передачи электронной почты настроен для тестового домена.
  Также необходимо обратить внимание, что полученная по почте ссылка введет на временную форму сброса пароля
  
* **URL**

  /api/forgot
  
* **Method:**

  `POST`
  
* **Success Response:**

  * **Code:** 201 <br />
    **Content:**
    ```json
        {
            "message": "Reset link sent to your email.",
            "success": true
        }
    ```
    
* **Error Response:**

  * **Code:** 401 Unauthorized <br />
    **Content:** 
    ```json
    {
        "message": "Unable to send reset link",
        "success": false
    }
    ```    

**Информация о текущем пользователе**
----
  Возвращает информацию о текущем пользователе и его организации

* **URL**

  /api/user

* **Method:**

  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        "data": {
            "id": 2,
            "name": "Petr Tester",
            "email": "petr@test.ru",
            "credit": null,
            "debit": null,
            "organization": "ООО Моя оборона",
            "dogovor": "456Н-2189",
            "logo": null,
            "address": [
                {
                    "city": "Москва",
                    "home": "89",
                    "street": "Московское шоссе",
                    "zip-code": 278987
                },
                {
                    "city": "Екатеринбург",
                    "home": "123а",
                    "street": "пр-кт Летова",
                    "zip-code": 228228
                }
            ]
        }
    }
    ```

* **Error Response:**

  * **Code:** 403 Forbidden <br />
    **Content:** `{"message": "No access rights"}`
  

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
  Возвращает json-данные о товарах в категории. В списке категорий возвращается только тот файл, который должен
  отображаться на обложке товара. В тестовом API товар с id 1206 обладает набором фото

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
                    "file": [
                                {
                                    "logo": "https://svam.dev.kosipov.ru/storage/img/pivo1.jpg"
                                }
                            ],
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


**Карточка товара**
----
   Карточка товара с полными свойствами. В свойстве files передается массив с url картинок товара
   
* **URL**

    /api/drinks/{id_drink}
    
* **Method:**

    `GET`
    
* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
```json 
{
    "type": "drinks",
    "id": 1214,
    "attributes": {
        "name": "Alfonso Hill",
        "description": "Лучший напиток",
        "type": {
            "id": 1,
            "value": "Пиво"
        },
        "country": "Russia",
        "manufacturer": "Рога и копыта",
        "expdate": "24 мес.",
        "price": "200.0000",
        "packing": [
            {
                "id": 1211,
                "drink_id": 1214,
                "tara": "Кег 20L",
                "price": "2008.0000",
                "1c_id": "MAtUgee9v0",
                "balance": 6,
                "created_at": "2020-03-13 14:54:26",
                "updated_at": "2020-04-07 09:58:50"
            }
        ],
        "properties": {
            "style": "бланш",
            "density": "11.0%",
            "strength": "5.0%",
            "fermentation": "верховое"
        },
        "files": [
            {
                "logo": "https://svam.dev.kosipov.ru/storage/img/pivo1.jpg"
            },
            {
                "logo": "https://svam.dev.kosipov.ru/storage/img/pivo2.jpg"
            }
]
    }
}
```

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
   
   * **Cookie**
   
      cart = {uuid-клиента}
   

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
                "link": "http://svam.test/api/orders/3"
            },
            {
                "id": 4,
                "status": "NW",
                "summ_price": "10464.0000",
                "date": "2020-03-27T14:11:34.000000Z",
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
  	"comment": "некоторый комментарий",
  	"address": "address_id - integer"
  }
  ```
  Предполагается, что пользователь, при создании заказа, может оставить какой-то комментарий через этот json комментарий передается в бэк.
  Для того, чтобы определить id адреса ниже представлен метод /api/user/addreses.
  
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
    
  * **Code:** 422 Unprocessable Entity <br />
        **Content:** `{"message": "Wrong address!"}`
    
      
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
    "comment": "некоторый комментарий",
    "address": "address_id - integer"
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
    
  * **Code:** 422 Unprocessable Entity <br />
      **Content:** `{"message": "Wrong address!"}`  

**Адреса текущего пользователя**
----
  Возвращает список адресов текущего пользователя

* **URL**

  /api/user/addreses

* **Method:**

  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
        {
            "id": 4,
            "organization_id": "456Н-2189",
            "address": {
                "city": "Москва",
                "home": "89",
                "street": "Московское шоссе",
                "zip-code": 278987
            }
        },
        {
            "id": 3,
            "organization_id": "456Н-2189",
            "address": {
                "city": "Екатеринбург",
                "home": "123а",
                "street": "пр-кт Летова",
                "zip-code": 228228
            }
        }
    ```


**Список свойств товаров**
----
  Возвращает список свойств товаров с русским комментарием и с возможными значениями для фильтрации

* **URL**

  /api/drinks/properties/{id_category}
  
* **Parameters**

    id_category - необязательный параметр, при указании, возвращает только те свойства, которые
    принадлежат конкретной категории
      
    values = true/false необязательный параметр, если указано true или если не указан, 
    то возвращается массив со всеми возможными значениями каждого параметра. Если указано false, то
    возвращается массив без значений.

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


**Поиск товара**
----
   Осуществляет поиск товаров по указанному слову. Поиск возможно осуществлять как по всем товарам, так и внутри категорий.

* **URL**

  /api/categories/{id_category}/search?query=Поисковая фраза
  
  либо
  
  /api/drinks/search?query=Поисковая фраза

* **Method:**

  `GET`

* **Example:**
    
    ```http://svam.test/api/categories/1/search?query=Kelton ```

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
                    "Argentina": [
                        {
                            "type": "drinks",
                            "country": "Argentina",
                            "id": 1208,
                            "attributes": {
                                "name": "Kelton Schaden",
                                "properties": {
                                    "density": "11.0%",
                                    "strength": "5.0%"
                                },
                                "file": [],
                                "link": "https://svam.dev.kosipov.ru/api/drinks/1208"
                            },
                            "relationships": {
                                "packing": [
                                    {
                                        "id": 1205,
                                        "price": "3306.0000",
                                        "pack": "Кег 20L",
                                        "balance": 65,
                                        "1c_id": "zLasQGrF8w",
                                        "addBasket": "https://svam.dev.kosipov.ru/api/basket/add"
                                    }
                                ]
                            }
                        }
                    ]
                }
            },
            "links": {
                "first": "https://svam.dev.kosipov.ru/api/categories/1/search?query=Kelton&page=1",
                "last": "https://svam.dev.kosipov.ru/api/categories/1/search?query=Kelton&page=1",
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

**Информация об организации**
----
  Возвращает информацию об организации пользователя для админки и странички об организации

* **URL**

  /api/organization

* **Method:**

  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        "data": {
            "id": "456Н-2189",
            "name": "ООО Моя оборона",
            "filename": null,
            "debit": null,
            "credit": null,
            "count_user": 2
        }
    }
    ```
    
    
**Сотрудники**
----
  Возвращает информацию о сотрудниках организации

* **URL**

  /api/users

* **Method:**

  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        "data": [
            {
                "id": 2,
                "name": "Petr Tester",
                "email": "petr@test.ru",
                "email_verified_at": null,
                "credit": null,
                "debit": null,
                "role_id": "director",
                "organization_id": "456Н-2189",
                "created_at": "2020-04-17 10:02:17",
                "updated_at": "2020-04-17 10:02:17"
            },
            {
                "id": 3,
                "name": "Василий Манагеров",
                "email": "vaska@test.ru",
                "email_verified_at": null,
                "credit": null,
                "debit": null,
                "role_id": "manager",
                "organization_id": "456Н-2189",
                "created_at": "2020-04-21 12:37:25",
                "updated_at": "2020-04-21 12:37:25"
            }
        ],
        "links": {
            "first": "http://svam.test/api/users?page=1",
            "last": "http://svam.test/api/users?page=1",
            "prev": null,
            "next": null
        },
        "meta": {
            "current_page": 1,
            "from": 1,
            "last_page": 1,
            "path": "http://svam.test/api/users",
            "per_page": 15,
            "to": 2,
            "total": 2
        }
    }
    ```

**Добавить менеджера**
----
  Добавляет менеджера в организацию пользователя(для добавление необходимо иметь учетную запись директора организации) 

* **URL**

  /api/users/add

* **Method:**

  `POST`

* **Тело запроса**
  
  ```json
  {
    "name":"Petr Tester",
    "phone": "+79990999999",
    "email": "petr@test.ru"
  }
  ```

Прошу заметить, что необязательно придерживаться какого-либо определенного формата при ввода номера телефона.
Допускается  8904..... либо 904..... либо 7904.... любой введенный номер будет приведен к формату
+7904.....

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
    {
        {
            "name": "Petr Tester",
            "password": "roOsRa2S",
            "e-mail": "petr123@test.ru",
            "organization": "ООО Моя оборона"
            "phone": "+79990999999"
        }
    }
    ```
    
**Изменить данные текущего пользователя**
----
  Редактирование аккаунта текущего пользователя, возможно изменить такие данные, как
  ФИО, электронную почту, номер телефона, пароль, все перечисленные в теле запроса свойства
  являются необязательными, можно изменить как сразу несколько значений, так и одно

* **URL**

  /api/user/edit

* **Method:**

  `POST`

* **Тело запроса**
  
  ```json
  {
    "name": "фио",
    "password": "пароль",
    "password_confirmation": "подтверждение пароля",
    "phone": "номер телефона",
    "email": "электронная почта"
  }
  ```

* **Success Response:**

  * **Code:** 201 <br />
    **Content:** 
    ```json 
    {
        "message": "Change property successful"
    }
    ```
  