This README has been written with [Typora](https://typora.io/) software.

[TOC]

# Carcacounter - Backend

Tiny project to develop a score manager for [Carcassonne gameboard](https://www.zmangames.com/en/products/carcassonne/). 

This repository contains documentation of the backend.



We are aiming to have a friendly app to count the scores of a match.



The project will be split on 3 repositories:

* Backend - https://github.com/MikeLirio/carcacounter-backend
* Frontend - https://github.com/MikeLirio/carcacounter-frontend
* Main App builder - https://github.com/MikeLirio/carcacounter

# Backend

This API is written in NodeJS. We will be using Typescript as well.

### Modules

* [express](https://expressjs.com/): main framework that provide everything we need to build our API.
* [dotenv](https://www.npmjs.com/package/dotenv): used to allow us to read environment variables.
* [body-parser](https://www.npmjs.com/package/body-parser): Node.js body parsing middleware. allows us to read more easily the data.

### Testing Modules

* 

# REST API Documentation

The REST API coded along the app are described below

## Health Check - Get /health

Creates a new match and return the identifier of the match.

### Request 

body

```json
{}
```

### Response

`HTTP code 200`

```json
{
	"version": 0.0.1
}
```

## Create a new Match - POST /match

Creates a new match and return the identifier of the match.

### Request 

body

```json
{}
```

### Response

`HTTP code 201`

```json
{
	"matchId": "f8c3245e-3e3e-4f36-84f1-aaa61043aff4"
}
```

## Get Match - GET /match/[id]

Get actual status of the match given.

### Request 

body

```json
{}
```

### Response

`HTTP code 200`

```json
{
    "matchId": "f8c3245e-3e3e-4f36-84f1-aaa61043aff4",
    "players": [
        {
            "playerId": 1,
            "color": "red",
            "name": "Jhon",
            "score": 26,
            "resources": {
                "wheet": 3,
                "beer": 0,
                "fabric": 0
            }
        }, {
            "playerId": 2,
            "color": "blue",
        	"name":	"Jane",
            "score": 55,
            "resources": {
                "wheet": 0,
                "beer": 2,
                "fabric": 0
            }
        }, {
            "playerId": 3,
        	"color": "black",
        	"name":	"Mike",
            "score": 10,
            "resources": {
                "wheet": 1,
                "beer": 1,
                "fabric": 0
            }
        }, {
            "playerId": 4,
        	"color": "pink",
        	"name":	"Ana",
            "score": 100,
            "resources": {
                "wheet": 0,
                "beer": 0,
                "fabric": 0
            }
        }, {
            "playerId": 5,
        	"color": "pink",
        	"name":	"Ana",
            "score": 100,
            "resources": {
                "wheet": 0,
                "beer": 0,
                "fabric": 0
            }
        }, {
            "playerId": 6,
        	"color": "yellow",
        	"name":	"Doe",
            "score": 33,
            "resources": {
                "wheet": 0,
                "beer": 0,
                "fabric": 1
            }
        }
    ]
}
```



## Update Match - POST /match/[id]

Set the properties of the match. It cannot be modified one time setted.

### Request

body

```json
{
    "matchId": "f8c3245e-3e3e-4f36-84f1-aaa61043aff4",
    "expansions": [1, 2],
    "players": [
        {
            "playerId": 1,
            "color": "red",
            "name": "Jhon"
    	}, {
            "playerId": 2,
        	"color": "blue",
        	"name":	"Jane"
    	}, {
            "playerId": 3,
        	"color": "black",
        	"name":	"Mike"
    	}, {
            "playerId": 4,
        	"color": "pink",
        	"name":	"Ana"
    	}, {
            "playerId": 5,
        	"color": "green",
        	"name":	"Sarah"
    	}, {
            "playerId": 6,
        	"color": "yellow",
        	"name":	"Doe"
    	}
    ]
}
```

### Response

`HTTP code 200`

```json
{}
```

## Create Score - POST /match/[id]/score

### Request

body

```json
{
    "players": [1, 2],
    "type": "city",
    "hasCathedral": false,
    "size": 5
}
```

### Response

`HTTP code 201`

```json
{
    "scoreId": "3fed8e9e-7c36-46f5-a2b8-0bf2a4760d17",
    "matchId": "f8c3245e-3e3e-4f36-84f1-aaa61043aff4",
    "players": [
        {
            "playerId": 1,
            "color": "red",
            "name": "Jhon",
            "score": 26,
            "resources": {
                "wheet": 3,
                "beer": 0,
                "fabric": 0
            }
        }, {
            "playerId": 2,
            "color": "blue",
        	"name":	"Jane",
            "score": 55,
            "resources": {
                "wheet": 0,
                "beer": 2,
                "fabric": 0
            }
        }, {
            "playerId": 3,
        	"color": "black",
        	"name":	"Mike",
            "score": 10,
            "resources": {
                "wheet": 1,
                "beer": 1,
                "fabric": 0
            }
        }, {
            "playerId": 4,
        	"color": "pink",
        	"name":	"Ana",
            "score": 100,
            "resources": {
                "wheet": 0,
                "beer": 0,
                "fabric": 0
            }
        }, {
            "playerId": 5,
        	"color": "pink",
        	"name":	"Ana",
            "score": 100,
            "resources": {
                "wheet": 0,
                "beer": 0,
                "fabric": 0
            }
        }, {
            "playerId": 6,
        	"color": "yellow",
        	"name":	"Doe",
            "score": 33,
            "resources": {
                "wheet": 0,
                "beer": 0,
                "fabric": 1
            }
        }
    ]
}
```

## End Match - POST /match/[id]/end

### Request

body

```json
{}
```

### Response

`HTTP code 200`

```json
{
    "matchId": "f8c3245e-3e3e-4f36-84f1-aaa61043aff4",
    "players": [
        {
            "playerId": 1,
            "color": "red",
            "name": "Jhon",
            "score": 26,
        }, {
            "playerId": 2,
            "color": "blue",
        	"name":	"Jane",
            "score": 55
        }, {
            "playerId": 3,
        	"color": "black",
        	"name":	"Mike",
            "score": 10
        }, {
            "playerId": 4,
        	"color": "pink",
        	"name":	"Ana",
            "score": 130
        }, {
            "playerId": 5,
        	"color": "pink",
        	"name":	"Ana",
            "score": 100
        }, {
            "playerId": 6,
        	"color": "yellow",
        	"name":	"Doe",
            "score": 33
        }
    ]
}
```
