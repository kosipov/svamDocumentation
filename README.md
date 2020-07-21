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
        "email": "petr@test.ru",
        "phone": "+79991234567",
        "inn": "456Н-2189",
        "message": "здесь какое-то сообщение"
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
            "id": 32,
            "username": "ivan",
            "organization": "ДОРОНИН СЕРГЕЙ ВАСИЛЬЕВИЧ",
            "inn": "7704350685",
            "address": [
                {
                    "id": 11,
                    "organization_id": "7704350685",
                    "address": {
                        "street": "улица Пушкина-колотушкина"
                    }
                }
            ],
            "phone": null,
            "credit": "0.0000",
            "count_users": 1
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
```json 
{
    "data": [
        {
            "type": "drinks",
            "country": "Россия",
            "id": 233,
            "attributes": {
                "name": "Нат Баттер (Nut Butter)",
                "properties": {
                    "density": "12.0%",
                    "strength": "5.0%"
                },
                "price": "Цена по запросу",
                "file": [
                    {
                        "logo": null
                    }
                ],
                "link": "http://svam.test/api/drinks/233"
            },
            "relationships": {
                "packing": [
                    {
                        "id": 218,
                        "price": "Цена по запросу",
                        "tara": " БУТ 0,5л*12 шт.",
                        "taraQuantity": 12,
                        "unit": "шт",
                        "balance": null,
                        "1c_id": null,
                        "addBasket": "http://svam.test/api/basket/add"
                    }
                ]
            }
        }
    ],
    "links": {
        "first": "http://svam.test/api/categories/1/filter?page=1",
        "last": "http://svam.test/api/categories/1/filter?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "path": "http://svam.test/api/categories/1/filter",
        "per_page": 15,
        "to": 1,
        "total": 1
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
        "data": [
            {
                "type": "drinks",
                "country": "Россия",
                "id": 233,
                "attributes": {
                    "name": "Нат Баттер (Nut Butter)",
                    "properties": {
                        "density": "12.0%",
                        "strength": "5.0%"
                    },
                    "price": "Цена по запросу",
                    "file": [
                        {
                            "logo": null
                        }
                    ],
                    "link": "http://svam.test/api/drinks/233"
                },
                "relationships": {
                    "packing": [
                        {
                            "id": 218,
                            "price": "Цена по запросу",
                            "tara": " БУТ 0,5л*12 шт.",
                            "taraQuantity": 12,
                            "unit": "шт",
                            "balance": null,
                            "1c_id": null,
                            "addBasket": "http://svam.test/api/basket/add"
                        }
                    ]
                }
            }
        ],
        "links": {
            "first": "http://svam.test/api/categories/1/filter?page=1",
            "last": "http://svam.test/api/categories/1/filter?page=1",
            "prev": null,
            "next": null
        },
        "meta": {
            "current_page": 1,
            "from": 1,
            "last_page": 1,
            "path": "http://svam.test/api/categories/1/filter",
            "per_page": 15,
            "to": 1,
            "total": 1
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
        "data": [
            {
                "type": "drinks",
                "country": "Аргентина",
                "id": 235,
                "attributes": {
                    "name": "Клаштер тёмный (Klaster tmave)",
                    "category": "Пиво",
                    "properties": null,
                    "file": [],
                    "link": "http://svam.test/api/drinks/235"
                },
                "relationships": {
                    "packing": [
                        {
                            "id": 220,
                            "price": "Цена по запросу",
                            "tara": " Ж/Б. 0,5 х 24 шт. ",
                            "taraQuantity": 24,
                            "unit": "шт",
                            "balance": null,
                            "1c_id": null,
                            "addBasket": "http://svam.test/api/basket/add"
                        }
                    ]
                }
            },
            {
                "type": "drinks",
                "country": "Россия",
                "id": 244,
                "attributes": {
                    "name": "Клаштер светлый (Klaster svetle)",
                    "category": "Пиво",
                    "properties": null,
                    "file": [],
                    "link": "http://svam.test/api/drinks/244"
                },
                "relationships": {
                    "packing": [
                        {
                            "id": 229,
                            "price": "Цена по запросу",
                            "tara": " Ж/Б 0,5 х 24 шт. ",
                            "taraQuantity": 24,
                            "unit": "шт",
                            "balance": null,
                            "1c_id": null,
                            "addBasket": "http://svam.test/api/basket/add"
                        }
                    ]
                }
            },
            {
                "type": "drinks",
                "country": "Россия",
                "id": 252,
                "attributes": {
                    "name": "Клаштер светлый (Klaster svetle)",
                    "category": "Пиво",
                    "properties": null,
                    "file": [],
                    "link": "http://svam.test/api/drinks/252"
                },
                "relationships": {
                    "packing": [
                        {
                            "id": 237,
                            "price": "Цена по запросу",
                            "tara": " бут. 0,5 х 20 шт. ",
                            "taraQuantity": 20,
                            "unit": "шт",
                            "balance": null,
                            "1c_id": null,
                            "addBasket": "http://svam.test/api/basket/add"
                        }
                    ]
                }
            },
            {
                "type": "drinks",
                "country": "Россия",
                "id": 256,
                "attributes": {
                    "name": "Клаштер тёмный (Klaster tmave)",
                    "category": "Пиво",
                    "properties": null,
                    "file": [],
                    "link": "http://svam.test/api/drinks/256"
                },
                "relationships": {
                    "packing": [
                        {
                            "id": 241,
                            "price": "Цена по запросу",
                            "tara": " бут. 0,5 х 20 шт. ",
                            "taraQuantity": 20,
                            "unit": "шт",
                            "balance": null,
                            "1c_id": null,
                            "addBasket": "http://svam.test/api/basket/add"
                        }
                    ]
                }
            },
            {
                "type": "drinks",
                "country": "Россия",
                "id": 320,
                "attributes": {
                    "name": "Клаштер светлый (Klaster svetle)",
                    "category": "Пиво",
                    "properties": null,
                    "file": [],
                    "link": "http://svam.test/api/drinks/320"
                },
                "relationships": {
                    "packing": [
                        {
                            "id": 305,
                            "price": "Цена по запросу",
                            "tara": " КЕГ 20 л.",
                            "taraQuantity": null,
                            "unit": "шт",
                            "balance": null,
                            "1c_id": null,
                            "addBasket": "http://svam.test/api/basket/add"
                        }
                    ]
                }
            }
        ],
        "links": {
            "first": "http://svam.test/api/drinks/search?query=%D0%9A%D0%BB%D0%B0%D1%88%D1%82%D0%B5%D1%80&page=1",
            "last": "http://svam.test/api/drinks/search?query=%D0%9A%D0%BB%D0%B0%D1%88%D1%82%D0%B5%D1%80&page=1",
            "prev": null,
            "next": null
        },
        "meta": {
            "current_page": 1,
            "from": 1,
            "last_page": 1,
            "path": "http://svam.test/api/drinks/search",
            "per_page": 15,
            "to": 5,
            "total": 5
        }
    }
    ```

**Информация об адресах организации**
----
  Возвращает информацию об адресах организации по ИНН

* **URL**

  /api/user/address/{inn}

* **Method:**

  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```json 
        [
            {
                "dogovor_id": "136f9d05-7b87-11e8-a41e-f079595bc33f",
                "dogovor": "Договор № ВР-17-586 от 01.03.2017 г",
                "address": "140150, Московская обл, Раменский р-н, Быково рп, Аэропортовская ул, дом № 14, корпус Т"
            },
            {
                "dogovor_id": "18bb2174-2338-11e7-ad53-f079595bc33f",
                "dogovor": "**Договор № ВР-17-586 от 01.03.2017 г",
                "address": "140150, Московская обл, Раменский р-н, Быково рп, Аэропортовская ул, дом № 14, зд-корпус А, лит. 1Б, 1 эт., помещ. 1, номер по плану 13"
            },
        ]
    ```
    
**Информация об движениях по задолженности организации**
----
  Возвращает информацию о движении по договорам организации
  
    "sum_receipt" - сумма по приходу
    
    "sum_consumption" - сумма по расходу
                      
    "sum_end_balance" - сумма конечного остатка
    
    Аналогичные поля с префиксом all дают сумму по всем договорам организации

  Возможна фильтрация договоров и движений по ним по временным периодам. Если
  необходимо вывести все договора начиная с определенной даты, необходимо в URL 
  указать:
  
    ?filter[start_date]=2019-12-01
  
  Если необходимо получить все договора до определенной даты, то используется 
  следующий префикс
    ?filter[end_date]=2019-12-01
    
  Допускается комбинирование параметров, для указания временного диапазона, например:
    ?filter[start_date]=2019-12-01&?filter[end_date]=2019-12-05
* **URL**

  /api/dogovors

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
                    "name": "Договор № ВР-17-586 от 01.03.2017 г",
                    "items": [
                        {
                            "id": 5,
                            "dogovor_id": 3,
                            "name": "Реализация товаров и услуг СГ000057011 от 12.11.2019 8:20:38",
                            "start_balance": null,
                            "receipt": "282183.03",
                            "consumption": null,
                            "end_balance": null,
                            "start_date": "2019-11-12",
                            "pay_date": "2019-12-22",
                            "created_at": "2020-07-17 17:09:21",
                            "updated_at": "2020-07-17 17:09:21"
                        },
                        {
                            "id": 6,
                            "dogovor_id": 3,
                            "name": "Реализация товаров и услуг СГ000058317 от 19.11.2019 11:08:56",
                            "start_balance": null,
                            "receipt": "62557.87",
                            "consumption": null,
                            "end_balance": null,
                            "start_date": "2019-11-19",
                            "pay_date": "2019-12-29",
                            "created_at": "2020-07-17 17:09:21",
                            "updated_at": "2020-07-17 17:09:21"
                        },
                        {
                            "id": 7,
                            "dogovor_id": 3,
                            "name": "Реализация товаров и услуг СГ000062559 от 10.12.2019 10:08:50",
                            "start_balance": null,
                            "receipt": "291269.38",
                            "consumption": null,
                            "end_balance": null,
                            "start_date": "2019-12-10",
                            "pay_date": "2020-01-19",
                            "created_at": "2020-07-17 17:09:21",
                            "updated_at": "2020-07-17 17:09:21"
                        },
                        {
                            "id": 8,
                            "dogovor_id": 3,
                            "name": "Реализация товаров и услуг СГ000055543 от 05.11.2019 9:57:16",
                            "start_balance": null,
                            "receipt": "565565.21",
                            "consumption": null,
                            "end_balance": null,
                            "start_date": "2019-11-05",
                            "pay_date": "2019-12-15",
                            "created_at": "2020-07-17 17:09:21",
                            "updated_at": "2020-07-17 17:09:21"
                        },
                        {
                            "id": 9,
                            "dogovor_id": 3,
                            "name": "Реализация товаров и услуг СГ000054095 от 29.10.2019 11:23:54",
                            "start_balance": null,
                            "receipt": "49595.7",
                            "consumption": null,
                            "end_balance": null,
                            "start_date": "2019-10-29",
                            "pay_date": "2019-12-08",
                            "created_at": "2020-07-17 17:09:21",
                            "updated_at": "2020-07-17 17:09:21"
                        },
                        {
                            "id": 10,
                            "dogovor_id": 3,
                            "name": "Реализация товаров и услуг СГ000061203 от 03.12.2019 9:04:54",
                            "start_balance": null,
                            "receipt": "230305.55",
                            "consumption": null,
                            "end_balance": null,
                            "start_date": "2019-12-03",
                            "pay_date": "2020-01-12",
                            "created_at": "2020-07-17 17:09:21",
                            "updated_at": "2020-07-17 17:09:21"
                        },
                        {
                            "id": 11,
                            "dogovor_id": 3,
                            "name": "Реализация товаров и услуг СГ000059764 от 26.11.2019 8:28:11",
                            "start_balance": null,
                            "receipt": "60384.91",
                            "consumption": null,
                            "end_balance": null,
                            "start_date": "2019-11-26",
                            "pay_date": "2020-01-05",
                            "created_at": "2020-07-17 17:09:21",
                            "updated_at": "2020-07-17 17:09:21"
                        },
                        {
                            "id": 12,
                            "dogovor_id": 3,
                            "name": "Реализация товаров и услуг СГ000052899 от 22.10.2019 12:08:24",
                            "start_balance": null,
                            "receipt": "49296.51",
                            "consumption": null,
                            "end_balance": null,
                            "start_date": "2019-10-22",
                            "pay_date": "2019-12-01",
                            "created_at": "2020-07-17 17:09:21",
                            "updated_at": "2020-07-17 17:09:21"
                        }
                    ],
                    "sum_receipt": "1591158.16",
                    "sum_consumption": 0,
                    "sum_end_balance": 0
                }
            ],
            "all_sum_receipt": 1591158.16,
            "sum_consumption": 0,
            "sum_end_balance": 0
        }
    ```