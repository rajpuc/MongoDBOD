# Foreign Key:
In a database, a **foreign key** is a field (or a set of fields) in one table that references the **primary key** in another table. It establishes a relationship between the two tables, ensuring referential integrity by making sure the value in the foreign key column exists in the referenced primary key column.

---

### Key Points:
- **Purpose**: Links related data across tables.
- **Enforces Consistency**: Ensures that you cannot add a value to the foreign key column unless it exists in the referenced table.
- **Cascading Actions**: Can define actions like `ON DELETE CASCADE` or `ON UPDATE CASCADE` to automatically update or delete related rows.

---

### Example:
#### Table: `categories`
| categoryId (Primary Key) | name         |
|---------------------------|--------------|
| 1                         | Electronics  |
| 2                         | Fashion      |

#### Table: `products`
| productId | name           | categoryId (Foreign Key) |
|-----------|----------------|--------------------------|
| 1         | iPhone 14      | 1                        |
| 2         | Air Max 90     | 2                        |

Here, `categoryId` in the `products` table is a foreign key referencing `categoryId` in the `categories` table. This links each product to its category.

---
---

## Join in MongoDB:
- ### Normally amra jokon SQL a kaj kori, SQL a kaj korer shomoy amra inner join, left join,right join etc diye takhi. Orthad table a table join diye data ber kore niye ashar j process ta shei process ta mongoDB te korte chailele sheikhetre amader `$lookup` operator use korte hobe:

- ### Join valo vabe bujar jonno ami `AmazonDB` namer akta DB banalam. then shekhane nicher dewa collection gula insert kore nilam:

```javascript
db.brands.insertMany([
    { name: "Nike", brandId: 1, createdAt: ISODate("2023-01-10T10:00:00Z") },
    { name: "Adidas", brandId: 2, createdAt: ISODate("2023-01-11T12:00:00Z") },
    { name: "Puma", brandId: 3, createdAt: ISODate("2023-01-12T09:30:00Z") },
    { name: "Reebok", brandId: 4, createdAt: ISODate("2023-01-13T15:00:00Z") },
    { name: "Under Armour", brandId: 5, createdAt: ISODate("2023-01-14T08:45:00Z") },
    { name: "New Balance", brandId: 6, createdAt: ISODate("2023-01-15T14:20:00Z") },
    { name: "Asics", brandId: 7, createdAt: ISODate("2023-01-16T13:10:00Z") },
    { name: "Skechers", brandId: 8, createdAt: ISODate("2023-01-17T10:30:00Z") },
    { name: "Fila", brandId: 9, createdAt: ISODate("2023-01-18T11:45:00Z") },
    { name: "Columbia", brandId: 10, createdAt: ISODate("2023-01-19T09:00:00Z") },
    { name: "Patagonia", brandId: 11, createdAt: ISODate("2023-01-20T10:50:00Z") },
    { name: "North Face", brandId: 12, createdAt: ISODate("2023-01-21T14:30:00Z") },
    { name: "Timberland", brandId: 13, createdAt: ISODate("2023-01-22T11:15:00Z") },
    { name: "Vans", brandId: 14, createdAt: ISODate("2023-01-23T12:40:00Z") },
    { name: "Converse", brandId: 15, createdAt: ISODate("2023-01-24T13:20:00Z") },
    { name: "Lululemon", brandId: 16, createdAt: ISODate("2023-01-25T09:10:00Z") },
    { name: "Levi's", brandId: 17, createdAt: ISODate("2023-01-26T10:25:00Z") },
    { name: "Gucci", brandId: 18, createdAt: ISODate("2023-01-27T14:45:00Z") },
    { name: "Prada", brandId: 19, createdAt: ISODate("2023-01-28T11:50:00Z") },
    { name: "Armani", brandId: 20, createdAt: ISODate("2023-01-29T13:35:00Z") },
    { name: "Versace", brandId: 21, createdAt: ISODate("2023-01-30T09:30:00Z") },
    { name: "Burberry", brandId: 22, createdAt: ISODate("2023-01-31T10:15:00Z") },
    { name: "Louis Vuitton", brandId: 23, createdAt: ISODate("2023-02-01T14:10:00Z") },
    { name: "Chanel", brandId: 24, createdAt: ISODate("2023-02-02T11:30:00Z") },
    { name: "H&M", brandId: 25, createdAt: ISODate("2023-02-03T13:40:00Z") },
    { name: "Zara", brandId: 26, createdAt: ISODate("2023-02-04T09:45:00Z") },
    { name: "Uniqlo", brandId: 27, createdAt: ISODate("2023-02-05T10:50:00Z") },
    { name: "Gap", brandId: 28, createdAt: ISODate("2023-02-06T12:30:00Z") },
    { name: "Old Navy", brandId: 29, createdAt: ISODate("2023-02-07T14:00:00Z") },
    { name: "Banana Republic", brandId: 30, createdAt: ISODate("2023-02-08T11:20:00Z") }
]);
```

```javascript
db.categories.insertMany([
    { name: "Electronics", categoryId: 1, createdAt: ISODate("2023-01-01T10:00:00Z") },
    { name: "Fashion", categoryId: 2, createdAt: ISODate("2023-01-02T11:00:00Z") },
    { name: "Home Appliances", categoryId: 3, createdAt: ISODate("2023-01-03T12:00:00Z") },
    { name: "Books", categoryId: 4, createdAt: ISODate("2023-01-04T13:00:00Z") },
    { name: "Beauty & Health", categoryId: 5, createdAt: ISODate("2023-01-05T14:00:00Z") },
    { name: "Toys & Games", categoryId: 6, createdAt: ISODate("2023-01-06T15:00:00Z") },
    { name: "Sports & Outdoors", categoryId: 7, createdAt: ISODate("2023-01-07T16:00:00Z") },
    { name: "Automotive", categoryId: 8, createdAt: ISODate("2023-01-08T17:00:00Z") },
    { name: "Pet Supplies", categoryId: 9, createdAt: ISODate("2023-01-09T18:00:00Z") },
    { name: "Groceries", categoryId: 10, createdAt: ISODate("2023-01-10T19:00:00Z") },
    { name: "Office Supplies", categoryId: 11, createdAt: ISODate("2023-01-11T20:00:00Z") },
    { name: "Music Instruments", categoryId: 12, createdAt: ISODate("2023-01-12T21:00:00Z") },
    { name: "Movies & TV", categoryId: 13, createdAt: ISODate("2023-01-13T22:00:00Z") },
    { name: "Video Games", categoryId: 14, createdAt: ISODate("2023-01-14T23:00:00Z") },
    { name: "Jewelry", categoryId: 15, createdAt: ISODate("2023-01-15T10:00:00Z") },
    { name: "Furniture", categoryId: 16, createdAt: ISODate("2023-01-16T11:00:00Z") },
    { name: "Kitchenware", categoryId: 17, createdAt: ISODate("2023-01-17T12:00:00Z") },
    { name: "Art & Craft", categoryId: 18, createdAt: ISODate("2023-01-18T13:00:00Z") },
    { name: "Baby Products", categoryId: 19, createdAt: ISODate("2023-01-19T14:00:00Z") },
    { name: "Travel Accessories", categoryId: 20, createdAt: ISODate("2023-01-20T15:00:00Z") }
]);
```

```javascript
db.products.insertMany([
    { productId: 1, categoryId: 1, brandId: 1, name: "iPhone 14", price: 999, unit: "pcs", details: "Latest iPhone model", createdAt: ISODate("2023-01-01T10:00:00Z") },
    { productId: 2, categoryId: 1, brandId: 2, name: "Galaxy S23", price: 899, unit: "pcs", details: "Latest Samsung flagship", createdAt: ISODate("2023-01-02T11:00:00Z") },
    { productId: 3, categoryId: 1, brandId: 1, name: "MacBook Pro", price: 1299, unit: "pcs", details: "16-inch MacBook Pro", createdAt: ISODate("2023-01-03T12:00:00Z") },
    { productId: 4, categoryId: 2, brandId: 3, name: "Air Max 90", price: 150, unit: "pair", details: "Classic running shoe", createdAt: ISODate("2023-01-04T13:00:00Z") },
    { productId: 5, categoryId: 2, brandId: 3, name: "Air Force 1", price: 120, unit: "pair", details: "Iconic basketball shoe", createdAt: ISODate("2023-01-05T14:00:00Z") },
    { productId: 6, categoryId: 2, brandId: 4, name: "UltraBoost 22", price: 180, unit: "pair", details: "High-performance running shoe", createdAt: ISODate("2023-01-06T15:00:00Z") },
    { productId: 7, categoryId: 2, brandId: 4, name: "Stan Smith", price: 100, unit: "pair", details: "Timeless sneaker", createdAt: ISODate("2023-01-07T16:00:00Z") },
    { productId: 8, categoryId: 3, brandId: 5, name: "Microwave Oven", price: 200, unit: "pcs", details: "Compact microwave oven", createdAt: ISODate("2023-01-08T17:00:00Z") },
    { productId: 9, categoryId: 3, brandId: 5, name: "Refrigerator", price: 1000, unit: "pcs", details: "Double-door fridge", createdAt: ISODate("2023-01-09T18:00:00Z") },
    { productId: 10, categoryId: 4, brandId: 6, name: "Fiction Novel", price: 15, unit: "pcs", details: "Bestselling novel", createdAt: ISODate("2023-01-10T19:00:00Z") },
    { productId: 11, categoryId: 4, brandId: 6, name: "Non-Fiction Book", price: 20, unit: "pcs", details: "Inspirational stories", createdAt: ISODate("2023-01-11T20:00:00Z") },
    { productId: 12, categoryId: 5, brandId: 7, name: "Moisturizer", price: 25, unit: "pcs", details: "Daily hydrating cream", createdAt: ISODate("2023-01-12T21:00:00Z") },
    { productId: 13, categoryId: 5, brandId: 7, name: "Face Wash", price: 10, unit: "pcs", details: "Gentle cleanser", createdAt: ISODate("2023-01-13T22:00:00Z") },
    { productId: 14, categoryId: 6, brandId: 8, name: "Lego Set", price: 50, unit: "pcs", details: "Creative building set", createdAt: ISODate("2023-01-14T23:00:00Z") },
    { productId: 15, categoryId: 6, brandId: 8, name: "Board Game", price: 40, unit: "pcs", details: "Fun family game", createdAt: ISODate("2023-01-15T10:00:00Z") },
    { productId: 16, categoryId: 1, brandId: 1, name: "iPad Pro", price: 799, unit: "pcs", details: "High-end tablet", createdAt: ISODate("2023-01-16T11:00:00Z") },
    { productId: 17, categoryId: 1, brandId: 2, name: "Galaxy Tab S8", price: 699, unit: "pcs", details: "Samsung premium tablet", createdAt: ISODate("2023-01-17T12:00:00Z") },
    { productId: 18, categoryId: 2, brandId: 3, name: "Air Zoom Pegasus", price: 140, unit: "pair", details: "Versatile running shoe", createdAt: ISODate("2023-01-18T13:00:00Z") },
    { productId: 19, categoryId: 2, brandId: 4, name: "Yeezy Boost 350", price: 220, unit: "pair", details: "Exclusive sneaker", createdAt: ISODate("2023-01-19T14:00:00Z") },
    { productId: 20, categoryId: 3, brandId: 5, name: "Dishwasher", price: 600, unit: "pcs", details: "Energy-efficient dishwasher", createdAt: ISODate("2023-01-20T15:00:00Z") },
    { productId: 21, categoryId: 7, brandId: 9, name: "Treadmill", price: 800, unit: "pcs", details: "High-end treadmill", createdAt: ISODate("2023-01-21T16:00:00Z") },
    { productId: 22, categoryId: 7, brandId: 9, name: "Dumbbell Set", price: 100, unit: "pcs", details: "Adjustable dumbbells", createdAt: ISODate("2023-01-22T17:00:00Z") },
    { productId: 23, categoryId: 3, brandId: 5, name: "Refrigerator", price: 1000, unit: "pcs", details: "Double-door fridge", createdAt: ISODate("2023-01-23T18:00:00Z") },
    { productId: 24, categoryId: 2, brandId: 4, name: "UltraBoost 22", price: 180, unit: "pair", details: "High-performance running shoe", createdAt: ISODate("2023-01-24T19:00:00Z") },
    { productId: 25, categoryId: 6, brandId: 8, name: "Lego Set", price: 50, unit: "pcs", details: "Creative building set", createdAt: ISODate("2023-01-25T20:00:00Z") },
    { productId: 26, categoryId: 5, brandId: 7, name: "Face Wash", price: 10, unit: "pcs", details: "Gentle cleanser", createdAt: ISODate("2023-01-26T21:00:00Z") },
    { productId: 27, categoryId: 4, brandId: 6, name: "Fiction Novel", price: 15, unit: "pcs", details: "Bestselling novel", createdAt: ISODate("2023-01-27T22:00:00Z") },
    { productId: 28, categoryId: 1, brandId: 1, name: "iPad Pro", price: 799, unit: "pcs", details: "High-end tablet", createdAt: ISODate("2023-01-28T23:00:00Z") },
    { productId: 29, categoryId: 3, brandId: 5, name: "Microwave Oven", price: 200, unit: "pcs", details: "Compact microwave oven", createdAt: ISODate("2023-01-29T10:00:00Z") },
    { productId: 30, categoryId: 1, brandId: 1, name: "iPhone 14", price: 999, unit: "pcs", details: "Latest iPhone model", createdAt: ISODate("2023-01-30T11:00:00Z") },
    { productId: 31, categoryId: 2, brandId: 4, name: "Stan Smith", price: 100, unit: "pair", details: "Timeless sneaker", createdAt: ISODate("2023-01-31T12:00:00Z") },
    { productId: 32, categoryId: 7, brandId: 9, name: "Yoga Mat", price: 20, unit: "pcs", details: "Non-slip yoga mat", createdAt: ISODate("2023-02-01T13:00:00Z") },
    { productId: 33, categoryId: 2, brandId: 3, name: "Air Max 90", price: 150, unit: "pair", details: "Classic running shoe", createdAt: ISODate("2023-02-02T14:00:00Z") },
    { productId: 34, categoryId: 6, brandId: 8, name: "Board Game", price: 40, unit: "pcs", details: "Fun family game", createdAt: ISODate("2023-02-03T15:00:00Z") },
    { productId: 35, categoryId: 3, brandId: 5, name: "Dishwasher",

 price: 600, unit: "pcs", details: "Energy-efficient dishwasher", createdAt: ISODate("2023-02-04T16:00:00Z") },
    { productId: 36, categoryId: 5, brandId: 7, name: "Moisturizer", price: 25, unit: "pcs", details: "Daily hydrating cream", createdAt: ISODate("2023-02-05T17:00:00Z") },
    { productId: 37, categoryId: 1, brandId: 2, name: "Galaxy Tab S8", price: 699, unit: "pcs", details: "Samsung premium tablet", createdAt: ISODate("2023-02-06T18:00:00Z") },
    { productId: 38, categoryId: 7, brandId: 9, name: "Treadmill", price: 800, unit: "pcs", details: "High-end treadmill", createdAt: ISODate("2023-02-07T19:00:00Z") },
    { productId: 39, categoryId: 5, brandId: 7, name: "Face Wash", price: 10, unit: "pcs", details: "Gentle cleanser", createdAt: ISODate("2023-02-08T20:00:00Z") },
    { productId: 40, categoryId: 2, brandId: 3, name: "Air Force 1", price: 120, unit: "pair", details: "Iconic basketball shoe", createdAt: ISODate("2023-02-09T21:00:00Z") }
]);
```
### Fields:
1. **`productId`**: Unique identifier for the product.
2. **`categoryId`**: Links the product to its category.
3. **`brandId`**: Links the product to its brand.
4. **`name`**: Name of the product.
5. **`price`**: Price of the product.
6. **`unit`**: Unit of measurement (e.g., pcs, pair).
7. **`details`**: Description of the product.
8. **`createdAt`**: Date and time of product creation.

### Uporer collection gula valo kore keyal korle bujte parben `products` collection er sathe `categories` and `products` collection er ekta relation ache:
- ### `products` er sathe 'brands' er relation hocce `products` collection er moddhe takha `brandId` diye. 
- ### `products` er sathe 'categories' er relation hocce `products` collection er moddhe takha `categoryId` diye. 

### Akhon amra collection join kora dekhbe $lookup use kore:


```javascript
db.products.aggregate(
    [
        {
            $lookup: {
              from: "categories",
              localField: "categoryId",
              foreignField: "categoryId" ,
              as: "AikhaneJKonoNameDiteParen"
            }
        },{
            $limit: 1
        }
    ]
    /*
    - from:-> er value hishebe jar sathe join diben,shei collectioner name diye diye dite hobe.
    - localField: -> er value hishebe foreignkey er name dite hobe
    - foreignField: ->  j collection er sathe join diben shei collection er primary key.
    - as: -> joining er pore property gula ki name a shongjukto hobe tar name diye dite hobe:
    */
)

//output

[
  {
    "_id": {
      "$oid": "6795b1017c63944999d4bb53"
    },
    "productId": 1,
    "categoryId": 1,
    "brandId": 1,
    "name": "iPhone 14",
    "price": 999,
    "unit": "pcs",
    "details": "Latest iPhone model",
    "createdAt": {
      "$date": "2023-01-01T10:00:00Z"
    },
    "AikhaneJKonoNameDiteParen": [
      {
        "_id": {
          "$oid": "6795b0cec9113f2454890655"
        },
        "name": "Electronics",
        "categoryId": 1,
        "createdAt": {
          "$date": "2023-01-01T10:00:00Z"
        }
      }
    ]
  }
]
```

```javascript
//2nd example:

use('AmazonDB')


db.products.aggregate(
    [
        {
            $lookup: {
              from: "categories",
              localField: "categoryId",
              foreignField: "categoryId" ,
              as: "AikhaneJKonoNameDiteParen"
            }
        },
        {
            $lookup: {
              from: "brands",
              localField: "brandId",
              foreignField: "brandId" ,
              as: "bradnd"
            }
        },{
            $limit: 1
        }
    ]
)
//output:
[
  {
    "_id": {
      "$oid": "6795b1017c63944999d4bb53"
    },
    "productId": 1,
    "categoryId": 1,
    "brandId": 1,
    "name": "iPhone 14",
    "price": 999,
    "unit": "pcs",
    "details": "Latest iPhone model",
    "createdAt": {
      "$date": "2023-01-01T10:00:00Z"
    },
    "AikhaneJKonoNameDiteParen": [
      {
        "_id": {
          "$oid": "6795b0cec9113f2454890655"
        },
        "name": "Electronics",
        "categoryId": 1,
        "createdAt": {
          "$date": "2023-01-01T10:00:00Z"
        }
      }
    ],
    "bradnd": [
      {
        "_id": {
          "$oid": "6795ad461c1ed4b226b4a070"
        },
        "name": "Nike",
        "brandId": 1,
        "createdAt": {
          "$date": "2023-01-10T10:00:00Z"
        }
      }
    ]
  }
]
```
## Facet operator:
 - ### ek kothai bolte gele $facet diye amra multiple result eksathe niye aste pari ba multiple pipeline use korte pari:

```javascript
db.products.aggregate(
    [
       {
            $facet: 
            {
                "A":[{}],// keyal koren ata akta pipeline
                "B":[{}]// ata o akta pipeline 
            }
       }
    ]
)
// so amra bolte pari $facet use kore amra multiple pipeline eksathe use koret pari.
```
```javascript

db.products.aggregate(
    [
       {
            $facet: 
            {
                "total":[
                    {$count: 'total'} // total property er value hishebe amra total koita document ache products collection er moddhe sheta pabo.
                ],
                "Datat":[{$limit:3}], //  "Datat" er moddhe amra products collection er first 3ta document pabo.
                // ai property gular name apni jemon icce temon dite paren.
            }
       }
    ]
)

//output
[
  {
    "total": [
      {
        "total": 40
      }
    ],
    "Datat": [
      {
        "_id": {
          "$oid": "6795b1017c63944999d4bb53"
        },
        "productId": 1,
        "categoryId": 1,
        "brandId": 1,
        "name": "iPhone 14",
        "price": 999,
        "unit": "pcs",
        "details": "Latest iPhone model",
        "createdAt": {
          "$date": "2023-01-01T10:00:00Z"
        }
      },
      {
        "_id": {
          "$oid": "6795b1017c63944999d4bb54"
        },
        "productId": 2,
        "categoryId": 1,
        "brandId": 2,
        "name": "Galaxy S23",
        "price": 899,
        "unit": "pcs",
        "details": "Latest Samsung flagship",
        "createdAt": {
          "$date": "2023-01-02T11:00:00Z"
        }
      },
      {
        "_id": {
          "$oid": "6795b1017c63944999d4bb55"
        },
        "productId": 3,
        "categoryId": 1,
        "brandId": 1,
        "name": "MacBook Pro",
        "price": 1299,
        "unit": "pcs",
        "details": "16-inch MacBook Pro",
        "createdAt": {
          "$date": "2023-01-03T12:00:00Z"
        }
      }
    ]
  }
]
```