## Group by na kore apni jodi sum,avg,max,min ber korte chan:

```javascript


db.employees.aggregate(
    [
        {
            $group: {
              _id:0, 
              JKonoNameDitheParenAiJaigai:{$min:"$salary"} //shob document er modddhe j salary minimum sheta return korbe.
            }
        }
    ]
)

//output
[
  {
    "_id": 0,
    "JKonoNameDitheParenAiJaigai": 48000
  }
]
```