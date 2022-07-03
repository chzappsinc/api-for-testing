# Demo API's for study and testing purpose

Test API's for testing and studying purpose

**Base Url :** https://demo.chzapps.com/api/

Info : 
Backend : `Node.js`
Database : `MySQL`

Available Api's
- [Create User](#create-user-account)
- [Login User](#login-user)


## Auth

### Create user account

```http
  POST /user/create-account
```
Body:

| Key | Value     | Description                |
| :-------- | :------- | :------------------------- |
| `username` | `string` | **Required**. username |
| `password` | `string` | **Required**. password |
| `first_name` | `string` | **Required**. first_name |
| `last_name` | `string` | **Required**. last_name |
| `gender` | `string` | **Required**. gender |

#### Response 

Status code : _**500**_ (Missing some body key and values)

Response : (Sample)
```json
{
    "MessageChannel": 1,
    "message": "Please enter all fields username | password | first_name | last_name | gender",
    "RequestedMethod": "POST", //Method from client side
    "ApprovedMethod": "POST"
}
```

**Status code** : _**400**_ (Username already taken)

Response : 
```json
{
    "message": "Username not available"
}
```


**Status code** : _**200**_ (User Created succesfully)

Response : 
```json
{
    "message": "User created successfully, Now login"
}
```


### Login user

```http
  POST /users/login
```

Body

| Key | Value     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `username`      | `string` | **Required**. username |
| `password`      | `string` | **Required**. password |

#### Response

**Status code** : _**500**_ (Some fields Missing)

Response : 
```json
{
    "MessageChannel": 1,
    "message": "Enter all fields username | password"
}
```

**Status code** : _**400**_ (Failed Login)

Response : 
```json
{
    "MessageChannel": 2,
    "message": "username or password doesn't match",
}
```

**Status code** : _**200**_ (succesfully Login)

Response : 
```json
{
    "MessageChannel": 3,
    "message": "Login success",
    "token": "eyJhbGciOiJI....",
    "data": {
        "first_name": "david",
        "last_name": "rouge",
        "user_name": "rogers4"
    }
}
```

### User Details

```http
  GET /users/user-details
```

Headers : 

authorization  : `Bearer eyJhbGciOiJIUz...`

Body

| Key | Value     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `username`      | `string` | **Required**. username |

#### Response

**Status code** : _**500**_ (No such user)

Response : 
```json
{
    "message": "No such user found",
    "MessageChannel": 1
}
```

**Status code** : _**401**_ (Missing username field)

Response : 
```json
{
    "message": "username is missing"
}
```

**Status code** : _**200**_ (succesfully fetch)

Response : 
```json
{
    "username": "rogers",
    "first_name": "david",
    "last_name": "rouge",
    "verified": 1,
    "gender": "male"
}
```


---END---

