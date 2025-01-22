## Comparison Query Operator:
- ### Mongodb te query operate korer jonno onkgula comprasion operator royeces and aikhane operator er shamne `$`sign use kora hoi. jemon:
    - ### $eq => equal to Operator
    - ### $lt => less than Operator
    - ### $lte => less than or equal to Operator
    - ### $gt => greater than Operator
    - ### $gte => greater than or equal to Operator
    - ### $ne => not equal to Operator
    - ### $in => in Operator
    - ### $nin => not in Operator
- ## For example:
```javascript

db.employees.find( 
    {
        salary:{$gt:55000}
    }
)

```
```javascript
db.employees.find( 
    {
        salary:{$gt:55000}
    }
)
```
```javascript

db.employees.find( 
    {
        salary:{$in:[55000,80000,65000]} // j j employee er salary 55000,80000 & 65000 shudumatro shei employee gulakei select korbe.
    }
)
```
```javascript

db.employees.find( 
    {
        salary:{$nin:[55000,80000,65000]} // j j employee er salary 55000,80000 & 65000 tader chara baki employeeder select korbe.
    }
)
```