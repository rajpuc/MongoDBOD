## Boolean Aggregation Operators:
![](./image.png)

### use:

```javascript
use('AmazonDB')


db.products.aggregate([
    { 
        $addFields: { 
            "IsBetween800&1000": {
                $and:[
                    {$lte:["$price",1000]},
                    {$gte:["$price",800]}

                ]
            }
        }
    },
    {$limit: 5}
]);

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
    "IsBetween800&1000": true
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
    },
    "IsBetween800&1000": true
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
    },
    "IsBetween800&1000": false
  },
  {
    "_id": {
      "$oid": "6795b1017c63944999d4bb56"
    },
    "productId": 4,
    "categoryId": 2,
    "brandId": 3,
    "name": "Air Max 90",
    "price": 150,
    "unit": "pair",
    "details": "Classic running shoe",
    "createdAt": {
      "$date": "2023-01-04T13:00:00Z"
    },
    "IsBetween800&1000": false
  },
  {
    "_id": {
      "$oid": "6795b1017c63944999d4bb57"
    },
    "productId": 5,
    "categoryId": 2,
    "brandId": 3,
    "name": "Air Force 1",
    "price": 120,
    "unit": "pair",
    "details": "Iconic basketball shoe",
    "createdAt": {
      "$date": "2023-01-05T14:00:00Z"
    },
    "IsBetween800&1000": false
  }
]
```