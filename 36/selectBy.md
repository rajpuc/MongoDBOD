## select by $match opeartor, and use of $and & $or opertor with $match:

```javascript

use('CraftShop')


db.employees.aggregate(
    [
        {
            $match: {
                salary:{$gt:80000},
            },
            $match: {
              city:{$eq: 'Phoenix'},
            }
        } 
    ]
)

// tahole ata amader shei array of documents return korbe jader salary 80000 boro and city hocce 'Phoenix'. But amra jodi erokon multiple stage a condition gula likhte na chai tahole amader $and operator use korte hobe.
```
```javascript
use('CraftShop')


db.employees.aggregate(
    [
        {
            $match: {
                $and:[
                    {salary:{$gt: 40000}},
                    {city: {$eq: "Austin"}}
                ]
            }
        } 
    ]
)
//aikhane amra 2 step a uporer problem ta solve na kore 1 step a $and opearator use kore korlam. Ekivabe tumi chaile $or operator use korte paro tomer requirement onujayi.
```

