## Insert More than one document:
- ### 1 tar beshi document insert korte chaile `db.collectionName.inserMany()` method use korbo:
```javascript
use('CraftShop');

db.brand.insertMany([
    {"Name":"IBM"}, 
    {"Name": "BP"},
    {"Name": "UPS"},
    {"Name": "BMW"}
]);
```