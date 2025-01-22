## Ajk amra Database Related j method gula ace shegula dekbo:
- ### ai method gula practice er shomoy amr suggestion takbe localhost (MongoDB Community Server) use kora cause aikhaner besh kicu method MongoDB atlas a exicute hobe na. for example: `db.hostInfo()`- Monogo db toh cloud system, sha to tar host information apnake dibe na.
```javascript
db.help(); // MongoDB database system a kicu commonly used attribute ache. ai method ta likhe query exicute korle - kotogula attribute ace, kontar ki name, kontar ki kaj, shomosto description apni aikhane peye jaben.  
```

```jvascript
db.hostInfo(); // amader database server ta kon machine a host kora ache sheta dekhai.
```
```jvascript
db.getName(); // current kon DB teke query ta exicute hocce sheta dekhabe.
```
```jvascript
db.getMongo(); // current DB er database connection string ta dekhabe.
```
```jvascript
db.currentOp(); // DB er current operations gula dekhabe.
```
```jvascript
db.dropDatabase() //Current Database delete hoye jabe.
```
```jvascript
db.getCollectionInfos() // Amr database er moddhe ki ki collection ache shegular info dekte parbo.
```
```jvascript
db.getCollectionNames() // Amr DB te ki ki collection ace tar name gula dekhabe.
```
```jvascript
db.getLastError() // Amr database a shorbosesh kono error ashece kina! jodi ashe takhe tahole sheta ki, ta dekhabe. And ai method borthoman a r use hoi na.
```
```jvascript
db.getLastErrorObj() //returns the status document for the last operation. ata o r use hoi na.
```
```jvascript
db.isMaster() // amra j db te query ta chalacci sheta ki kono replica set naki kono master set ta bole dei.
```
```jvascript
db.getReplicationInfo() // Jodi kono replica set tekhe takhe tahole shetar akta details amra pabo.
```
```jvascript
db.listCommands() //Displays a list of common database commands.
```
```jvascript
db.logout() // jodi DB te amader login kora takhe tahole ai method exicute korle amra logout hoye jabo
```
```jvascript
db.printCollectionStats() // Amader db er protita collection er akta Statistics dekhabe.
```
```jvascript
db.serverBuildInfo() //Returns a mongodb documentation record containing the parameters for the instance.
```
```jvascript
db.serverStatus() // Returns a document that provides an overview of the state database process.
```
```jvascript

db.shutdownServer()
// Cleanly and safely stops the current mongodb or mongos process.

```
```jvascript
db.stats()
// Returns a document record containing a report on the current database state.
```
```jvascript
db.version()
// Returns the version number of the mongodb instance:
```
```jvascript
// db.createCollection('demo')
Returns a mongod documentation record containing the compile parameters for the instance.


```
```jvascript
db.CollectionName.drop()
// It completely removes a collection from the database and does not leave any indexes associated with the dropped collections
```
```jvascript
```
```jvascript
```
```jvascript
```
```jvascript
```
```jvascript
```
