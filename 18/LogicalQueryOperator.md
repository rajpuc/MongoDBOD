## Logical Query Operator
- ### $and => Logical AND Operator
- ### $or => Logical OR Operator
- ### $not => Logical NOT Operator
- ### $nor => Logical NOR Operator

### Logical operator gular moddhe shob ceye beshi and,or and not e beshi use hoi.
```javascript
db.employees.find( 
    {
        $and:[
            {salary:{$gt:55000}},
            {city:{$eq:"New York"}},
        ]
    }
)
```
```javascript
db.employees.find( 
    {
        $or:[
            {salary:{$gt:55000}},
            {city:{$eq:"New York"}},
        ]
    }
)
```

In MongoDB, the **`$nor` operator** is used to combine multiple query conditions and returns documents that **do not match any of the conditions** specified.

### Syntax:
```javascript
{ $nor: [ { condition1 }, { condition2 }, ... ] }
```

### How It Works:
- If a document matches **any one** of the conditions in the `$nor` array, it is excluded from the results.
- Only documents that **do not match all the conditions** are included.

---

### Example:

Suppose you have the following `employees` collection:
```javascript
db.employees.insertMany([
    { name: "Alice", salary: 60000, city: "New York" },
    { name: "Bob", salary: 55000, city: "San Francisco" },
    { name: "Charlie", salary: 80000, city: "Seattle" },
    { name: "Diana", salary: 65000, city: "Austin" },
    { name: "Ethan", salary: 70000, city: "Denver" }
]);
```

### Query:
Find employees whose salary is **not greater than 60000** and who do **not live in New York**:
```javascript
db.employees.find({
    $nor: [
        { salary: { $gt: 60000 } },
        { city: "New York" }
    ]
});
```

### Explanation:
1. **Condition 1 (`{ salary: { $gt: 60000 } }`)**: Salary greater than 60000.
2. **Condition 2 (`{ city: "New York" }`)**: Lives in New York.
3. **`$nor`**: Returns documents where **neither condition is true**.

---

### Output:
```javascript
[
    { name: "Bob", salary: 55000, city: "San Francisco" }
]
```

### Why?
- **Bob** has a salary less than or equal to 60000 **and** does not live in New York.
- Other documents match at least one condition, so they are excluded. 

The **`$nor` operator** is useful when you want to filter out documents matching multiple conditions.