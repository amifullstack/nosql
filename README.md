## Connect to db
> `sudo mongod --config /etc/mongod`

**Login to DB**
> `mongo`

**Basics Queries**
> 1. `show dbs`
> 2. Create database `use mycustomers`
> 3. Show current DB `db`
> 4. Create User

>  ```db.createUser({
    user: "sanjay",
    pwd: "1234",
    roles: ["readwrite", "dbadmin"]
    })```

> 5. Create Collection(Tables) `db.createCollection('customers')`
> 6. Show Collections `show collections`
> 7. Insert data into the collections

>  ```
      db.customers.insert(
        [
          {first_name: "vin", last_name: "diesel"},
          {first_name: "powel", last_name: "walker"}
        ]
      )```
> 8. Display the document(data) in the collections(table) `db.customers.find()`
> 9. Update
> ```
    db.customers.update( {first_name: "vin"},
    {first_name:"vinvin", gender: "male"} );```
>   Notice that `update` will have a new values as `first_name` and `gender` discarded `last_name` for that use `$set` as follows.

> 10. `$set`
> ```
  db.customers.update({first_name: "vinvin"},
  {$set:{phno: "123123"}}
  )```
> 11. Query particular document `db.customers.find({first_name:"powel"})`

> 12. `pretty()` `db.news.find().pretty()`

> 13. Update two or more fields
>   ```
      db.customers.update({first_name: "powel"},
      {$set: {phno: 3434, gender: "male"}})```
> 14. Update whole document
    ```
      db.news.updateMany({},
      {$set: {tag: ["sports", "technology"]}})```

> 15. `$unset`  operator delets a particular filed
      `db.news.update({title: "B"}, {$unset: {likes: 1}})`

> 16. `upsert`

> ```
      db.news.update({title: "D"},
      {title: "D", description: "know more about D",
      likes: 10, tag: ["sports", "technology"]},
      {upsert: true})```

> 17.
    `$rename` updates the name of the field
    ```db.news.update({},
     {rename: {tag: "tags"}})```
> To update all

> 18  . remove `db.news.remove({title: "D"})`

> 19  . `$gt` `db.news.find({dislikes: {$gt: 19}})`
