## Sort:
```javascript
use('CraftShop')
db.employees.aggregate(
    [
        {$sort: {salary:1}}, //ascending sort
    ]
)
```
```javascript
use('CraftShop')

db.employees.aggregate(
    [
        {$sort: {salary:-1}}, //descending sort
    ]
)
```