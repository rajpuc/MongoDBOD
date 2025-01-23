## Delete one Or Many:
```javascript
db.brand.deleteOne(
  {
    _id:ObjectId("6790f8797b30f88de6dadc5f") //specific condition diye amra akta document delete korte pari.
  }
)
```
```javascript
db.employees.deleteMany(
  {
    salary:{$in:[30000,35000]} //jekhane jekhane ai condition match korbe sha shob document delete hoye jabe.
  }
)
```
```javascript
```
```javascript
```