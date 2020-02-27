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
    "attributes": {
        "drinks": [
            {
                "type": "drinks",
                "drink_id": 2,
                "attributes": {
                    "name": "Prof. Elliot Schaden MD",
                    "descript": "Лучший пивчанский на планете",
                    "country": "Россия",
                    "style": "Топ пивчик",
                    "strength": "66.6%",
                    "manufacturer": "Рога и копыта",
                    "density": "66.6%",
                    "expdate": "24 мес.",
                    "fermentation": "верховое",
                    "packing": [
                        {
                            "id": 2,
                            "price": "1595.0000",
                            "pack": "Кег 20L",
                            "balance": 100,
                            "1c_id": "DUjG3yDxLc",
                            "addBasket": "http://svam.test/api/basket/add/2"
                        }
                    ],
                    "link": "http://svam.test/api/drinks/2"
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

