## Projection 
- ### Projection means jokon amra mongodb teke data k find korci ba select korci, tokon shekhane onkgula column/property takhte pare, akhon ai shobgula column/property er moddhe amader kon kon column/property chai sheta ber kore anar process tai projection.
- ### future a query practice er shubidar jonno prothome nicher data gula diye first a akta employee collection banai felo:
```javascript
db.employees.insertMany([
    { name: "Alice Johnson", designation: "Software Engineer", salary: 60000, city: "New York" },
    { name: "Bob Smith", designation: "Data Analyst", salary: 55000, city: "San Francisco" },
    { name: "Charlie Brown", designation: "Product Manager", salary: 80000, city: "Seattle" },
    { name: "Diana White", designation: "UI/UX Designer", salary: 65000, city: "Austin" },
    { name: "Ethan Green", designation: "DevOps Engineer", salary: 70000, city: "Denver" },
    { name: "Fiona Black", designation: "Software Tester", salary: 50000, city: "Boston" },
    { name: "George King", designation: "Full-Stack Developer", salary: 75000, city: "Chicago" },
    { name: "Hannah Lee", designation: "Backend Developer", salary: 72000, city: "Los Angeles" },
    { name: "Ivy Brown", designation: "Frontend Developer", salary: 68000, city: "Miami" },
    { name: "Jack Williams", designation: "System Architect", salary: 95000, city: "Houston" },
    { name: "Karen Davis", designation: "Project Manager", salary: 88000, city: "Phoenix" },
    { name: "Liam Taylor", designation: "Mobile Developer", salary: 62000, city: "Dallas" },
    { name: "Mia Walker", designation: "Quality Analyst", salary: 54000, city: "Philadelphia" },
    { name: "Noah Harris", designation: "Business Analyst", salary: 58000, city: "Atlanta" },
    { name: "Olivia Martin", designation: "Database Administrator", salary: 67000, city: "San Diego" },
    { name: "Paul Adams", designation: "Cloud Engineer", salary: 77000, city: "Orlando" },
    { name: "Quincy Roberts", designation: "Security Specialist", salary: 72000, city: "San Jose" },
    { name: "Rachel Moore", designation: "Technical Writer", salary: 51000, city: "Charlotte" },
    { name: "Sam Wilson", designation: "Support Engineer", salary: 48000, city: "Nashville" },
    { name: "Tina Evans", designation: "Data Scientist", salary: 90000, city: "San Francisco" }
]);
```
```javascript
db.employees.find( //employee collection tekeh sob document select korbe and -
    {},
    {"_id":0,"designation":0} // oi prottekta document tekhe j j property/column amra select korte chacchi shegular name likhe tar value 1 kore dite hobe. Jodi 0 dei tahole select hobe na, and ai example a id and designation chara baki shob property select hobe.
)
```