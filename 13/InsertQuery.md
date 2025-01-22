## Ai porbo tekhe amra Application level query shekha suru korbo. Shurutei asha jak insret queryte:
- ### Mongodb te 1ta document insert korer jonno  `db.collectionName.insertOne()` method use korte hobe.

```javascript
use('CraftShop');  // Prothome kon Database niye kaj korbo sheta bole dite hobe.

db.brand.insertOne({ // aikhane amr collection er name brand. "brand" collection er moddhe ai query ta insert hobe.
    "name": "Nafis",
    "designation": "Manager",
    "salary": 95000,
    "city": "Dhaka"
});
```
