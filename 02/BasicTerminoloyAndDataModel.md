## Ajk shikbo Basic Terminology and Data model:
- ### Amra jodi Traditional SQL er sathe MongoDB k compare kori tahole cholun dekha jak terminology er dik diye duitar moddhe ki ki match kore:
- ### Traditional DB(SQL)  a Database bolte amra ja buji MongoDB te DB bolte tai e buaji.
- ### Traditional DB(like: MS SQL, MySQL, SQLite etc) te amra Table(Relational DB te Table k `entity` o bola hoi) bolte j bishoita k bujano hoi, MongoDB te shei bishoi ti k table na bole amra boli collection. Toh bishoita eki concept ek, kaj ek, shudumatro namer partokkho.
- ### Tradtioal DB jta k amra row/Tuple boli, MongoDB te sheta k amra document boli.
- ### Ekivabe Tradition DB te amra jta k column boli mongoDB te sheta k amra field boli.
- ### then Tradition DB te `table join` bolte amra j concepts gula k buji , sheta k amra mongoDB te ashe bolci `embeded documents`.
- ### R Tradition DB te amader primary key manage korte hoi, Tik ekivabe mongoDBte o amader primary key manage korte hoi. Toh mongoDB er khetre akta shubida ache sheta hocce protita document er sathe mongoDB by default `_id` name a akta primary key she nije nijei generate kore dei.
- ### Mongo DB te dui doroner Data model niye kaj kora jai:
    1. ### ekta hocce Embeded data model.
    2. ### R ekta hocce normalized data model.

### Embeded Data model means apner akta single document takbe, shei single document er bithorei apni alada alada object kore-kore data gula k rekhe diben(nicher example ta keyal korun). Dorun apner kace akta employee er information ace. Shei employe er id "10025AE336". Ekhon ai j akjon employee apner protishtan a ace shei employee er personal detail ace, contact details ace, shei employee er address ache. Akhon doren oi akta employee er against a onkgula tottho: employee er personal detail,contact detail, address, ba shei employee er educational details takhte pare, work experience details takhte pare - erokom r o onk details takhte pare akta employee er against a. Akhon ai shobgula details k apni object akhare akta single document er moddhe rekhe den tokon sheta k amra boli Embeded data model.
- ### shohoj kothai, in this model you can have(embeded) all the related data in a single document. It is also known as `de-normalized` data model. 
```javascript
    {
        _id: ,
        Emp_ID: "10025AE336"
        Personal_details:{
            First_Name: "Radhika",
            Last_Name: "Sharma",
            Date_Of_Birth: "1995-09-26"
        }
        Contact: {
            e-mail: "radhika_sharma.123@gmail.com",
            phone: "9848022338"
        },
        Address: {
            city: "Hyderabad",
            >Area: "Madapur",
            State: "Telangana"
        }
    }
```
### But akta single document er moddhe na rekhe amra jodi shegula venghe venghe alada alada document hishebe rekhe ditam like shown in below example. Tahole shetai hoto normalized data model. Tahole chaile amra Employee id,address details, personal details and contact details er jonno alada alada document manage ba r o valovabe bolte gele collection manage korte partam.
```javascript

    {
        _id: <0bjectId101>,
        Emp_ID: "10025AE336",
    }

    {
        _id: <0bjectId104>,
        empDocID: " ObjectId101",
        city: "Hyderabad",
        Area: "Madapur",
        State: "Telangana"
    }

    {
        _id: <0bjectId103>,
        empDocID: " ObjectId101",
        e-mail: "radhika_sharma.123@gmail.com",
        phone: "9848022338",
    }

    {

        _id: <0bjectId102>,
        empDocID: " ObjectId101",
        First_Name: "Radhika",
        Last_Name: "Sharma",
        Date_Of_Birth: "1995-09-26",
    }
```
