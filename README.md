# Demo API's for study and testing purpose

Test API's for testing and studying purpose

**Base Url :** https://demo.chzapps.com/api/

Available Api's
- [Create User](#create-user-account)
- [Login User](#login)


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
  GET /users/login
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

