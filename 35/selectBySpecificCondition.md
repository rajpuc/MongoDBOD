## Select by Specific Condition:
```javascript

use('CraftShop')


db.employees.aggregate(
    [
        {$match: {salary:{$gt:60000}}}  // aggregation a amra jodi kono data condition er upor base kore select korte chai tahole $match operator use korte hobe.
    ]
)
```