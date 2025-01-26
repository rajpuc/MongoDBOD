## join korer por apni projection korte chaile:
```javascript
use('AmazonDB')


db.products.aggregate(
    [
        {
            $lookup: {
                from: "categories",
                localField: "categoryId",
                foreignField: "categoryId",
                as: "AikhaneJKonoNameDiteParen"
            }
        },
        {
            $lookup: {
                from: "brands",
                localField: "brandId",
                foreignField: "brandId",
                as: "bradnd"
            }
        },
        {
            $project: {
                "_id": 0,
                "productId": 1,
                "categoryId": 1,
                "brandId": 1,
                "ProductName": "$name",// product collection er name property er value gula akhon notun projection object a ProductName er moddhe ashbe.
                "price":{$toDouble:"$price"}, //Price property er value gula double a convert hoye show hobe.
                "unit": 1,
                "details":1,
                "createdAt":1,
                "AikhaneJKonoNameDiteParen":{$first:"$AikhaneJKonoNameDiteParen.name"},
                "bradnd": {$first:"$bradnd.name"} // aitar mane hocce amra brand details er jonno puro object ta na niye shetar just akta property k access korlam
            }
        },
        {
            $limit: 2
        }
    ]
)


//output:
[
  {
    "productId": 1,
    "categoryId": 1,
    "brandId": 1,
    "unit": "pcs",
    "details": "Latest iPhone model",
    "createdAt": {
      "$date": "2023-01-01T10:00:00Z"
    },
    "ProductName": "iPhone 14",
    "price": 999,
    "AikhaneJKonoNameDiteParen": "Electronics",
    "bradnd": "Nike"
  },
  {
    "productId": 2,
    "categoryId": 1,
    "brandId": 2,
    "unit": "pcs",
    "details": "Latest Samsung flagship",
    "createdAt": {
      "$date": "2023-01-02T11:00:00Z"
    },
    "ProductName": "Galaxy S23",
    "price": 899,
    "AikhaneJKonoNameDiteParen": "Electronics",
    "bradnd": "Adidas"
  }
]
```