## Aggregation er pipeliner result er sathe extra field add korer jonno:
```javascript
db.products.aggregate(
    [
        {$match: {price:{$gt:999}}},
        {$addFields: { "rajesh": 20}} // result er prottekdocument er sathe ai property ta add hoye jabe. and apni chaile er value hishebe kono calculation er result o rakhte paren.
    ]
)
//output:
[
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
    "rajesh": 20
  },
  {
    "_id": {
      "$oid": "6795b1017c63944999d4bb5b"
    },
    "productId": 9,
    "categoryId": 3,
    "brandId": 5,
    "name": "Refrigerator",
    "price": 1000,
    "unit": "pcs",
    "details": "Double-door fridge",
    "createdAt": {
      "$date": "2023-01-09T18:00:00Z"
    },
    "rajesh": 20
  },
  {
    "_id": {
      "$oid": "6795b1017c63944999d4bb69"
    },
    "productId": 23,
    "categoryId": 3,
    "brandId": 5,
    "name": "Refrigerator",
    "price": 1000,
    "unit": "pcs",
    "details": "Double-door fridge",
    "createdAt": {
      "$date": "2023-01-23T18:00:00Z"
    },
    "rajesh": 20
  }
]
```
```javascript
db.products.aggregate([
    { $match: { price: { $gt: 999 } } },
    { 
        $addFields: { 
            "rajesh": { $add: ["$price", 10] } // prottekta document er price er sathe 10 add hoye "rajesh" property er value hishebe boshbe
        } 
    }
]);
//output
[
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
    "rajesh": 1309
  },
  {
    "_id": {
      "$oid": "6795b1017c63944999d4bb5b"
    },
    "productId": 9,
    "categoryId": 3,
    "brandId": 5,
    "name": "Refrigerator",
    "price": 1000,
    "unit": "pcs",
    "details": "Double-door fridge",
    "createdAt": {
      "$date": "2023-01-09T18:00:00Z"
    },
    "rajesh": 1010
  },
  {
    "_id": {
      "$oid": "6795b1017c63944999d4bb69"
    },
    "productId": 23,
    "categoryId": 3,
    "brandId": 5,
    "name": "Refrigerator",
    "price": 1000,
    "unit": "pcs",
    "details": "Double-door fridge",
    "createdAt": {
      "$date": "2023-01-23T18:00:00Z"
    },
    "rajesh": 1010
  }
]
```

```javascript

db.products.aggregate([
    { $match: { price: { $gt: 999 } } },
    { 
        $addFields: { 
            "rajesh": { $add: ["$price", 10] },
            "hello":"hey" //so apni chaile akhadik field apner icce moto add korte paren.
        } 
    }
]);

```
```javascript

use('AmazonDB')


db.products.aggregate([
    { $match: { price: { $gt: 999 } } },
    { 
        $addFields: { 
            "rajesh": { $add: ["$price", 10] }
        }
    },
    {
        $addFields: {
            "hello":"hey" //so apni chaile akhadik field apner icce moto add korte paren.
        }
    }
]);
```