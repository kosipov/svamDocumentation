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
    "id": 2,
    "value": "Сидр",
    "attributes": {
        "drinks": {
            "current_page": 1,
            "data": [
                {
                    "drink_id": 47,
                    "name": "Aracely Fritsch",
                    "type_id": 2,
                    "unit": "литр",
                    "country": "United Kingdom",
                    "style": "Best",
                    "strength": "66.6%",
                    "manufacturer": "Рога и копыта",
                    "density": "66.6%",
                    "expdate": "24 мес.",
                    "fermentation": "верховое",
                    "descript": "Лучший пивчанский на планете",
                    "price": "666.6000",
                    "1c_id": "askdjaklsjdklsajdklasjdlkewj",
                    "created_at": "2020-02-13 09:25:36",
                    "updated_at": "2020-02-13 09:25:36",
                    "balance": null
                }
            ],
            "first_page_url": "http://svam.test/api/categories/2?page=1",
            "from": 1,
            "last_page": 1,
            "last_page_url": "http://svam.test/api/categories/2?page=1",
            "next_page_url": null,
            "path": "http://svam.test/api/categories/2",
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

