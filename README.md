# README

## Purpose

The purpose of this repository is to showcase what a standard Take Home evaluation might look like. MVP is three endpoints. 


## Approach

The approach I took with this project was one I would take on the job. MVP has been achieved and robustly tested. I did not include additonal endpoints as though this would have been easy, I was thinking from an on the job perspective. If a manager asked me a list of three endpoints I would want to return those three endpoints and their tests but that was it. I would not want to spend extra time creating extra end points or functionality just for the sake of it. I would rather begin working on a new ticket. 

## Schema with stretch schema

<img width="1175" alt="Screen Shot 2022-07-27 at 4 31 04 PM" src="https://user-images.githubusercontent.com/97201304/181383808-478a2a05-4035-4816-beb3-9f39253f4f22.png">


## Setup 

- Clone project to local machine
- Run ``` bundle install ```
- Run ``` rails s ``` 
- Endpoints can now be fetched by calling ``` http://www.localhost:3000/{insert endpoint here} ```

## Endpoints 

<details> 
  <summary><b> Subscribe Customer to tea subscription </b> </summary>
Request: 

```
POST api/v1/customers/:cust_id/subscriptions

body: {
  tea_name: "Earl Grey",
  price: 10
  frequency: "weekly"
}
```

Response: 
```
status: 201
{
  "data": {
    "id": "1",
    "type": "Subscription",
    "attributes": {
      "tea_name": "Earl Grey",
      "price": 10,
      "status: "active",
      "frequency": "weekly"
    }
  }
}
```

</details>

<details> 
  <summary><b> Cancel a Customer's tea subscription </b> </summary>
Request: 

```
PATCH api/v1/customers/:cust_id/subscriptions/:id?status=cancelled
```

Response: 
```
status: 200
{
  "data": {
    "id": "1",
    "type": "Subscription",
    "attributes": {
      "tea_name": "Earl Grey",
      "price": 10,
      "status": "cancelled",
      "frequency": "weekly"
    }
  }
}
```

</details>


<details> 
  <summary><b> Get all customers subscriptions including cancelled ones </b> </summary>
Request: 

```
GET api/v1/customers/:cust_id/subscriptions
```

Response: 
```
status: 200
{
  "data": {
    "id": "1",
    "type": "Subscription",
    "attributes": [
      {
        "tea_name": "Earl Grey",
        "price": 10,
        "status": "cancelled",
        "frequency": "weekly"
      },
      {
        "tea_name": "Green tea",
        "price": 30,
        "status": "cancelled",
        "frequency": "monthly"
      },
      {
        "tea_name": "Himilayan Monk Juju",
        "price": 1012,
        "status": "cancelled",
        "frequency": "annual"
      },
    ]
  }
}
```

</details>
