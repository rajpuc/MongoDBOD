## Limiting 


```javascript
use('CraftShop')


db.employees.aggregate(
    [
        {$limit: 3}, // 3 ta document select kore niye ashbe.  
        // problem is 1st er 3ta dicce naki last er 3ta dicce sure na. 
    ]
)
```
```javascript
use('CraftShop')


db.employees.aggregate(
    [
        {$sort: { salary: 1 }},
        {$limit: 3}, //Suru tekhe 3 ta document select kore niye ashbe.  
    ]
)

```
```javascript
use('CraftShop')
db.employees.aggregate(
    [
        {$sort: { salary: -1 }},
        {$limit: 3}, //Sesh tekhe 3 ta document select kore niye ashbe.  
    ]
)
```