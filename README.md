


# Hunter x Hunter API

## Documentation

Welcome to the Hunter X Hunter API! This guide is your key to exploring the world of HTTP requests in the Hunter X Hunter universe. Before you embark on your data-gathering quest, take a moment to familiarize yourself with this documentation. Let your API requests be as potent as Nen abilities – sharp as Kurapika's chains and quick as Killua's lightning!

## Base URL
https://hxh-api.onrender.com/

## Rate Limit
While this Hunter X Hunter API is freely accessible without authentication, a simple key generation process is implemented to ensure responsible usage. To safeguard against misuse, a daily rate limit of 10,000 requests is set in place. Should you reach this limit, a 429 status code will temporarily suspend access for 24 hours, preserving the integrity of the API environment.

## Generate API Key

Endpoint to register and generate api key.

```
POST /api/v1/guest/register
```

Body  
**Note: the email you provided must be active or valid**
```json
{
   "email":"johndoe@gmail.com",
   "name":"john doe",
   "usage":"educational purpose only"
}
```
Response
```json
{
   "status":"success",
   "statusCode":201,
   "statusText":"Created",
   "message":"Register successful, A verification link to activate your key was sent to: johndoe@gmail.com"
}
```
Check your email for verification process.
## Character Endpoints

#### Character Attributes

| Attribute   | Type          | Description  |
| ----------- |:-------------:| ------------ |
| _id          | integer       | Unique Id per character |
| name        | string        | A character's full name |
| japanese_name| string        | A Japanese character's full name |
| also_known_as| array        | A character's aliases  |
| gender| string| |
| nen_type| array| A character's nen type, like Transmutation |
| abilities| array| A character's abilities, like gon's Jajanken |
| professions | array         | List of character's known professions |
| img         | object| Character's images   |
| state | string        | Are they alive or deceased|
| family | object| Family info |
| hunter_star| number| A hunter star if hunter |


#### Get single character
```
GET /api/v1/characters/1?api_key=[generated api key]
```

Response

```json
{
   "status":"success",
   "statusCode":200,
   "statusText":"OK",
   "message":"Data retrieved successfully.",
   "data": 
	 {
	   "_id":"64d6ffcd51403af1e30e7663",
	   "name":"chrollo lucilfer",
	   "also_known_as":[
	      "Boss",
	      "Phantom Troupe Member #0"
	   ],
	   "gender":"male",
	   "nen_type":["Specialization"],
	   "image":[],
	   "images":[],
	   "abilities":[
	      "Indoor Fish (Stolen)",
	      "Fun Fun Cloth (Stolen)",
	      "Teleportation (Stolen)",
	      "Black Voice (Stolen)",
	      "The Sun and Moon (Stolen)",
	      "Order Stamp (Stolen)",
	      "Gallery Fake (Stolen)",
	      "Convert Hands (Stolen)",
	      "Lovely Ghostwriter (Stolen; Former)",
	      "Double Face"
	   ],
	   "japanese_name":"クロロ゠ルシルフル",
	   "affiliations":[],
	   "professions":[
	      "thieve",
	      "Leader of the Phantom",
	      "Phantom Troupe Member #0",
	      "Floor Master",
	      "Red Cleaner (acting role)"
	   ],
	   "state":"alive",
	   "groups":[
	      {
	         "_id":"64d88505f5d42e977fffa4fb",
	         "name":"Phantom Troupe"
	      }
	   ]
	}
}
```

#### Get all characters
Endpoint to retrieve information from all characters.
```
GET /api/v1/characters?api_key=[generated api key]
```

Response

```json
{
   "status":"success",
   "statusCode":200,
   "statusText":"OK",
   "message":"Data retrieved successfully.",
   "data":[...]
}
```


#### Get characters paginated response
```
GET /api/v1/characters?api_key=[generated api key]&page=1&limit=2
```

Response

```json
{
   "status":"success",
   "statusCode":200,
   "statusText":"OK",
   "message":"Data retrieved successfully.",
   "data":[],
   "_paginate":{
      "results":1,
      "total":1,
      "from":1,
      "to":1,
      "page_size":2,
      "current_page":1,
      "next_page":null,
      "previous_page":null,
      "last_page":1
   }
}
```

## Group Endpoints
#### Get single group
```
GET /api/v1/groups/1?api_key=[generated api key]
```

Response

```json
{
   "status":"success",
   "statusCode":200,
   "statusText":"OK",
   "message":"Data retrieved successfully.",
   "data":[
      {
         "_id":"64d88505f5d42e977fffa4fb",
         "name":"Phantom Troupe",
         "also_known_as":[
            "Gen'ei Ryodan",
            "Spiders"
         ],
         "image":[
            {
               "_id":"64d8b8a4fd527f994bfdc322",
               "public_id":"hxh_api_oop/wxbktua0fo5aix2sdnqk",
               "secure_url":"https://res.cloudinary.com/erro/image/upload/v1691924647/hxh_api_oop/wxbktua0fo5aix2sdnqk.jpg",
               "width":728,
               "height":485
            }
         ],
         "images":[],
         "leaders":[
            {
               "_id":"64d6ffcd51403af1e30e7663",
               "name":"chrollo lucilfer"
            }
         ],
         "status":"active",
         "classification":"thieves",
         "createdAt":"2023-08-13T07:23:49.945Z",
         "updatedAt":"2023-08-13T12:07:33.912Z"
      }
   ]
}
```

#### Get all groups
Endpoint to retrieve information from all groups.
```
GET /api/v1/groups?api_key=[generated api key]
```

Response

```json
{
   "status":"success",
   "statusCode":200,
   "statusText":"OK",
   "message":"Data retrieved successfully.",
   "data":[...]
}
```

## Get random 

Endpoint to retrieve one random data in every endpoint.
```
GET /api/v1/[endpoint]/random?api_key=[generated api key]
```

Response

```json
{
   "status":"success",
   "statusCode":200,
   "statusText":"OK",
   "message":"Data retrieved successfully.",
   "data":{...}
}
```


