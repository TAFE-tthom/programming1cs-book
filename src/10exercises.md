## Exercises

### 1. Your todo-database

You have been tasked with writing a todo-list database. The focus of this task is to create a `class` called `TodoDatabase` which will have the following:

* `TodoDatabase()` - No parameters, it simply initialises the object.

* `AddTodo(string key, string title, string description)` - Three parameters, `key` is a unique identifier for the todo-object, it is used to ,  `title` outlines the heading that it would be under and the `description` are the details associated with the object.

* `GetTodo(string key)` - One parameter, `key` as with `AddTodo`, `GetTodo` is used to retrieve a `todo-object`. The object will be in the form:

```js
{
  key: 'unique_value',
  title: 'Cleaning up garage',
  description: 'Make sure we have necessary cleaning materials'
}  
```

* `RemoveTodo(string key)` - One parameter, `key` which is associated with the `todo-object`, will be removed and returned by the method. If the object does not exist, it is to return `null`.

* `UpdateTodo(key, TodoObject entry)` - Two parameters, `key` which is associated with the `todo-object`. The other parameter is an object in which the fields `title` and `description` are considered `optional`, so you will need to check which field exist and if one or both exist, take the changes from them and update the `todo-object` with it.

Example:

```cs
TodoDatabase todoDB = new TodoDatabase();

todoDB.AddTodo("first-entry", "Working on C#",
  "Finishing these exericses"); //Will be added to the database

todoDB.Update("first-entry", new TodoObject("Learning C#", " Finishing these exercises" });
// Previously { key: 'first-entry', title: 'Working on C#', ... }
// Now { key: 'first-entry', title: 'Learning C#', ... }

```



### 2. Your todo-api

You are to take your `TodoDatabase` class and use it as part of an `expressjs` application. The goal with this is that you are to create a simple `CRUD` application.

You will need to implement the following endpoints:

* `GET /todos` - This will return an array of objects, where each object is a todo-object. The endpoint always returns a success status of `200` unless something fundamentally has gone wrong.

Example data of that the endpoint should return:
```js
[
  {
    key: 'study-db',
    title: 'Studying Databases',
    description: 'Studying databases for week 7'
  },
  {
    key: 'study-js',
    title: 'Studying javascript',
    description: 'Working on expressjs and callbacks'
  }
]
```

* `GET /todos/:key` - This will return an object in the format:

```js
{
  key: '<key associated>',
  title: '<title>',
  description: '<description>'
}
```

Upon a successful retrieval, the endpoint must return a status of `200` along with the object above. If the key does not exist, a status of `404` should be returned and the following object.

```js
{
  error: true,
  reason: 'Unable to find object associated with key'
}
```

* `POST /todos` - This endpoint will accept a JSON object via the `body`, This will require the following object:

```js
{
  key: '<key associated>',
  title: '<title>',
  description: '<description>'
}
```

All fields must be present and the endpoint must return status `200` to outline a success. If the object is missing any of the fields associated, then the endpoint should return and a status of `404`:

```js
{
  error: true,
  reason: 'Unable to add new object to todo list'
}
```


* `PUT /todos/:key` - This endpoint will accept JSON object that will contain:

```js
{
  title?: '<title changes>',
  description?: '<description changes>'
}
```

Upon success, this update the relevant fields of the object. If it is successful, the endpoint should send back the updated object with status `200`.

If the key does not exist, the endpoint should return and a status of `404`:

```js
{
  error: true,
  reason: 'Unable to find object associated with key'
}
```


* `DELETE /todos/:key` - This endpoint will be responsible for deleting an object associated with a `key`. If the object is to be delete, the endpoint should return the object along with status `200`, however if the key does not exist, the endpoint should return an error object along with status `404`.

Example of error object:

```js
{
  error: true,
  reason: 'Unable to find object associated with key'
}
```

Make sure with your solution, you provide a function called `launchServer` that will launch the server and listen on port `5062`.



### 3. Persistent Data Storage


Carrying on from question 2, when storing your `todos`, you will need to create a mechanism to read and write from a file.

The `GET` methods associated with the `todo-api` will need to retrieve the file from disk and find the entry mapped to the key associated.

Any `POST`, `PUT` or `DELETE` methods associated with the `todo-api` will modify the file,

* `POST` methods, if it is going to be successful, should add to the file.
* `PUT` methods that are to be successful, should modify the entry inside the file.
* `DELETE` methods are to be successful, should remove an entry inside the file.

Use ADO.NET and **Sqlite** to achieve this task. You should be able to make a simple SQL database or in-memory database using this.

## Tasks with Test Cases

Please refer to the following code repository for the exercises <https://github.com/TAFE-tthom/programming1-cs>.

Attempt the following exercises in the **Week08** folder.

Ensure you run `npm install` and `npm run test` while your shell is in the directory of a particular question. Run `npm run test` to check to see if your solution works as specified.


