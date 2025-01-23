## Sort,Limit,Distinct, Count

```javascript

db.monthlyBudget.find().sort({
  category:1 //ascending order a sort korbe.
})

```
```javascript

db.monthlyBudget.find().sort({
  category:-1 //descending order a sort korbe.
})

```
```javascript

db.monthlyBudget.find().count('total')//koita document ache sheta count kore dibe and count er bithore 'total' likha ta mendatory. 

```
```javascript

db.employees.find().limit(2) //first 2 ta document select kore niye ashbe

```
```javascript

db.employees.find().sort({
  _id:-1 
}).limit(2) //last 2 ta document select kore niye ashbe

```
```javascript
db.employees.distinct('name'); // name propety er under a joto gula unique value ache sobgula value k aksathe akta array er moddhe return korbe.
```
