## group by:
- ### group kore select er mane hocce ekhi doroner distinct data gula k select kora.
```javascript
//Aggregation use kore
db.employees.aggregate(
    [
       {$group: {
         _id: "$city" //keep in mind: aikhane _id ta $group er default property, employees collection er _id na. r ata amader collection er moddhe jotogula unique city pabe shegular return korbe.
             }
        }
    ]
)

//output:
[
  {
    "_id": "San Francisco"
  },
  {
    "_id": "Dallas"
  },
  {
    "_id": "Houston"
  },
  {
    "_id": "Denver"
  },
  {
    "_id": "Chicago"
  },
  {
    "_id": "Philadelphia"
  },
  {
    "_id": "San Diego"
  },
  {
    "_id": "Orlando"
  },
  {
    "_id": "Phoenix"
  },
  {
    "_id": "Boston"
  },
  {
    "_id": "Los Angeles"
  },
  {
    "_id": "Charlotte"
  },
  {
    "_id": "Austin"
  },
  {
    "_id": "Miami"
  },
  {
    "_id": "Nashville"
  },
  {
    "_id": "Atlanta"
  },
  {
    "_id": "Seattle"
  },
  {
    "_id": "San Jose"
  },
  {
    "_id": "New York"
  }
]
```
```javascript
// find use kore:
//"group by" find method diye kora jai na.
```
## Group by sum
- ### Dorun apner Employees namer 1ta DB ache. And shei Db te 4ta unique city ache, Tar mane apner employee ra oi 4ta location chara onno kotaw takhe na. Akon jodi ami apnake boli oi location gula tekhe kon location gula te total koto salary dite hocce sheta ber koro ? - ata korer jonno amader group by use korte hobe cause 1ta location a amader onk employee takhte pare.
```javascript
//Aggregation use kore
use('CraftShop')


db.employees.aggregate(
    [
        {
            $group: {
              _id: "$city", 
              J_KonoNameDitheParenAiJaigai:{$sum:"$salary"}
              //field name er aghe "$" dithe miss korben na.
            }
        }
    ]
)
```
## group by avg:
```javascript
//Aggregation use kore
db.employees.aggregate(
    [
        {
            $group: {
              _id: "$city", 
              J_KonoNameDitheParenAiJaigai:{$avg:"$salary"}
              //field name er aghe "$" dithe miss korben na.
            }
        }
    ]
)
```
## group by max
```javascript
//Aggregation use kore
use('CraftShop')


db.employees.aggregate(
    [
        {
            $group: {
              _id: "$city", 
              JKonoNameDitheParenAiJaigai:{$max:"$salary"}
              //field name er aghe "$" dithe miss korben na.
            }
        }
    ]
)

```
## group by min
```javascript
//Aggregation use kore
use('CraftShop')


db.employees.aggregate(
    [
        {
            $group: {
              _id: "$city", 
              JKonoNameDitheParenAiJaigai:{$min:"$salary"}
              //field name er aghe "$" dithe miss korben na.
            }
        }
    ]
)
```

