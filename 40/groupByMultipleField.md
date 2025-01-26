## Group by multiple property:
- ### multiple field diye group by korer jonno:

```javascript
use('CraftShop')


db.employees.aggregate(
    [
        {
            $group: {
              _id:{city:"$city", designation: "$designation"}, 
              JKonoNameDitheParenAiJaigai:{$sum:"$salary"}
            }
            // ata group korbe tader niye jader salary and designation same then tader salary er sum return korbe.
        }
    ]
)

```
use('CraftShop')


db.employees.aggregate(
    [
        {
            $group: {
              _id:{city:"$city", designation: "$designation"}, 
              JKonoNameDitheParenAiJaigai:{$sum:"$salary"},
              avg:{$avg:"$salary"},
              max:{$max:"$salary"},
              min:{$min:"$salary"},
              // apni chaile sum,avg,max,min shob eksathei ber korte paren.
            }
        }
    ]
)
````



In MongoDB, grouping by multiple fields using the `$group` stage in aggregation returns a document for each unique combination of the specified fields along with the computed results.

---

### Syntax:
```javascript
db.collection.aggregate([
  { $group: { _id: { field1: "$field1", field2: "$field2" }, computedField: { <aggregation-operator>: "$<field>" } } }
]);
```

---

### Example:

#### Data:
```javascript
db.employees.insertMany([
  { name: "Alice", designation: "Engineer", city: "New York", salary: 60000 },
  { name: "Bob", designation: "Engineer", city: "San Francisco", salary: 55000 },
  { name: "Charlie", designation: "Manager", city: "New York", salary: 80000 },
  { name: "Diana", designation: "Engineer", city: "New York", salary: 65000 },
  { name: "Ethan", designation: "Manager", city: "San Francisco", salary: 70000 }
]);
```

#### Query:
Group by `designation` and `city`, and calculate the total salary:
```javascript
db.employees.aggregate([
  { 
    $group: { 
      _id: { designation: "$designation", city: "$city" },
      totalSalary: { $sum: "$salary" }
    }
  }
]);
```

#### Output:
```javascript
[
  { _id: { designation: "Engineer", city: "New York" }, totalSalary: 125000 },
  { _id: { designation: "Engineer", city: "San Francisco" }, totalSalary: 55000 },
  { _id: { designation: "Manager", city: "New York" }, totalSalary: 80000 },
  { _id: { designation: "Manager", city: "San Francisco" }, totalSalary: 70000 }
]
```

---

### Explanation:
- **`_id`**: Unique combination of `designation` and `city`.
- **`totalSalary`**: Sum of salaries for each group.