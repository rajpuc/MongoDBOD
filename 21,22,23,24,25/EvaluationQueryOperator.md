## Evaluation Query Operator:
- ### Evaluation query operator onkgula. Shob operator j shobshomoi use hoi beparta orokom na. but amra shob operators er sathe introduce hobo. Tar moddhe j operator amader kajer khetre beshi beshi use hoi shegula amra practice korbo:


    - ### $expr : Allows use of aggregation expressions within the query language. Amra jokon aggregation porbo tokon ata use kora shikbo.

    - ### $jsonSchema : Validate documents against the given JSON Schema. ata temon use hoi na.

    - ### $mod : Performs a modulo operation on the value of a field and selects documents with specified result.

    - ### $regex : Selects documents where values match a specified regular expression.

    - ### $text :Performs text search.

    - ### $where : Matches documents that satisfy a JavaScript expression.
- ### Ai operators gular use case gula valovabe bujar jonno `monthlyBudget` name er akta collection insert kore nibo amader DB te:
```javascript
db.monthlyBudget.insertMany([{
  "category": "food",
  "budget": 400,
  "spent": 1450
},{
  "category": "drinks",
  "budget": 100,
  "spent": 15
},{
  "category": "clothes",
  "budget": 100,
  "spent": 50
},{
  "category": "misc",
  "budget": 500,
  "spent": 300
},{
  "category": "travel",
  "budget": 200,
  "spent": 650
}])

```
```javascript
db.monthlyBudget.find(
  {
    $expr:{
      $lt:["$budget","$spent"] // '$' sign diye jokon amra kono property/column er name likhi tokon oi column er shomosto value e variable er moto kaj korbe.
    }
  }
)
```
```javascript
db.monthlyBudget.find(
  {
    spent: {
      $mod : [2,0] //spent k 2 diye devide korle jgular remainder 0 hobe shegula k select korbe.
    }
  }
)
```
```javascript
// $regex operator kono akta specific pattern er data k select korte ata use hoi.
// Say apni amn akta specific pattern dilen, j ei patternta Bangladesh er grammen phone er mobile er number er sathe match korbe, tahole sha grammen phone er shob mobile select kore niye ashbe. 
db.employees.find(
  {
    name:{
      $regex:"R" //R ache jader name a shegula kujhe ber korbe.
    }
  }
)
// Regular expression kivabe likhte hoi shegular jonno alada porashuna ache. icche korle shegula porte paro nijer tekhe.
```
```javascript
// Comparison er kaj ta amra $where operator use koreo korte pari.
db.monthlyBudget.find(
  {
    $where:"this.budget < this.spent"
  }
);
```