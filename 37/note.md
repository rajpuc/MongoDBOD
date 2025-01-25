## like operator:
- ### jokon amra konokicur "moto(like)" data find korte chai tahole `/jei datar moto find korte chacci sheta likbo ai slash gular moddhe/` opearator use korte hoi. ata k `like` operator bole:
```javascript
//Aggregation use kore
db.employees.aggregate(
    [
        {
            $match: {
               city: /r/ //jekhane jekhane city er value te "r" pabe shei shob documents return korbe 1ta array er moddhe.
            }
        } 
    ]
)
```

```javascript
// find er sathe like opeator er use:
db.employees.find( {
    city: /c/ //jekhane jekhane city er value te "c" pabe shei shob documents return korbe 1ta array er moddhe.
 })

```
## in operator:

```javascript
//Aggregation use kore
db.employees.aggregate(
    [
        {
            $match: {
               city:{$in:["San Francisco", "Chicago"]} //"Chicago" othoba(or) "San Francisco" j j document a pabe shei shob document 1ta array er moddhe return korbe orthad json array return korbe.
            }
        } 
    ]
)
```
```javascript
// find use kore:
db.employees.find({
    city: { $in: ["San Francisco"] } //"San Francisco" j j document a pabe shei shob document 1ta array er moddhe return korbe orthad json array return korbe.
})
```
## Projection:
- ### Akta collection tekhe specific property/column/field jai bolen - select korer process kei projection bole.
```javascript
//Aggregation use kore
db.employees.aggregate(
    [
        {
            $project: {
              name:1,designation:1 //2. aikhane amader shei shob property er name likhe dite hobe jgula amra access korte chacchi and obosshoi tader value 1 set kore dite hobe as shown in example. BTW aikhane jodi amra name and designation property er value 0 kore ditam tahole jeta hoto - name and designation chara oi collection er baki property gular access amra peye jetam.
            }
        }// 1. so amra jehetu projection korte chacci tai amader akta projection satge define korte hobe and ai projection korer jonno amader $project operator use korte hobe aggregation er moddhe. 
    ]
)
```
```javascript
// find use kore:
db.employees.find(
    {},
    { name:0 } //name chara baki field gula dekhabe.
)
```
## Skip
- ### $skip operator use kore amra kotogula data skip kore data select korbe sheta bole dite pari.
- ### $skip with $limit kore amra pagination korte pari.
```javascript
//Aggregation use kore

//1st example:
db.employees.aggregate(
    [
       {$skip: 0}, //$skip er value 0 dile kono document e skip hobe na.
       {$limit: 2}
    ]// prothom tekhe 2 ta document select kore dibe.
)

//2nd example
db.employees.aggregate(
    [
       {$skip: 2}, //prothom teke shudu 2ta skip korbe
    ]
)

```
```javascript
// find use kore:
db.employees.find({}).skip(4).limit(2); // prothom teke 4ta document skip kore, tar porer 2ta document select kore niye ashbe.
```
