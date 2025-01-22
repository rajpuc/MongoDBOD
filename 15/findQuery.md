## kivabe db tekhe data find korte hoi sheta shikbo:

```javascript

use('CraftShop')

db.brand.find() // "brand" collection tai return korbe. Means apni jodi puro akta collection select korte chan tokon ata use korbe.

```
```javascript

use('CraftShop')

db.brand.findOne(
    {"Name":"BP"} //condition er upor base kore 1ta dcoument select korte chaile tokon ata use korbo.
)

```