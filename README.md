# FlipFlop APIs

## Endpoints

**Dev**

```js
http://flipflop.dev.konabackend.com
```

**Stg**

```js
http://flipflop.stg.konabackend.com
```


**Basic filters**

All the API (/resource, /resource/:id, /resource/find-one have this features

Example.

```js
GET /locations

[
  {
    _id: "565cc4afbbd0214e3c97d85f",
    _createdAt: "2015-11-30T21:50:39.394Z",
    _updatedAt: "2015-11-30T21:50:39.394Z",
    name: "Oficina",
    address: "benito blanco 1030",
    creditCard: true,
    english: false,
    age: "ALL",
    category: "5659f53b6388abeba14bc875",
    description: "Some bar",
    website: "office.com",
    country: "565660b8be9743a9498edd60",
    city: "5656b4d1bee882183c175072",
    zone: "565bbc9c3f6ad1fc51a7bfb3"  
  }
]  
```

**Where**

Find

```js
GET /locations?where[category]=5659f53b6388abeba14bc875
```

**Select**

Project fields

```js
GET /locations?select[name]=1
```

Using multiple conditions

```js
GET /locations?select[name]=1&where[category]=5659f53b6388abeba14bc875
```

**Sort**

Sorting by field

```js
GET /locations?sort[_updatedAt]=1
```

```js
GET /locations?sort[_updatedAt]=-1
```

**Populate**

Populate model reference

```js
GET locations?populate[]=category&populate[]=zone&populate[]=country&populate[]=city
```

**Pagination**

Add qs offset limit

```js
GET locations?populate[]=category&populate[]=zone&populate[]=country&populate[]=city?offset=0&limit=10
```

## SIGN IN PAGE 1

### Register with email


```js
POST /users HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache

{  
   "email":"santiago@konacloud.io",
   "password":"****"
}
```

```js
{
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfX3YiOjAsImVtYWlsIjoic2FudGlhZ29Aa29uYWNsb3VkLmlvIiwiX2lkIjoiNTY1NjkzMzQ5NTRmNzUyMTIyMzFhZDQxIiwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.wtknVCA1ykQ7q0261TZyahgUqZ15hbDwtExcuyh75vY",
    "user": {
        "__v": 0,
        "email": "santiago@konacloud.io",
        "_id": "56569334954f75212231ad41"
    }
}
```


### Register/Login with Facebook

Request

```js
POST /users/login-with-facebook HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
x-facebook-access-token: CAACEdEose0cBAJNKSGogM4TAHOABUwVUXqxTfnw10gWZBdXf8k7AXgZC76FIbP2XolVMWxVwmK3wMBMiPmEJcM0Rrct1d671ZCSkZCozbUNAGKsYwUb1cGAfovMAcet07zCy2Rvcwh264htCA9gBaSnEQ2j5fgC104EwngunrlH37Vwwhg9zEFuV95TkmAWI6qdZCYLJiuwQeE3X41k7z
Cache-Control: no-cache

{ }

```

Response

```js
{
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2YWYyZDQwNDQ3YThjNGRlZDE4NWMiLCJlbWFpbCI6IjE2MjEyMzQ2MjRAZmFjZWJvb2suY29tIiwiZmFjZWJvb2tJZCI6IjE2MjEyMzQ2MjQiLCJfX3YiOjAsImZhdm91cml0ZVJlY29tbWVuZGVkIjpbXSwiZmF2b3VyaXRlRXZlbnRzIjpbXSwiaW50ZXJlc3RzIjpbXSwiY291bnRyaWVzVmlzaXRlZCI6W10sImNvdW50cmllc1RvVmlzaXQiOltdLCJkZXNjcmlwdGlvbiI6W10sImN1cnJlbnRQb3NpdGlvbiI6W10sInByb2ZpbGVQaG90b3MiOltdfQ.DLOTq39xPY8ibEEjCMRSaEVcRJ3nI4xPBL9DxWE0ufo",
    "user": {
        "_id": "5656af2d40447a8c4ded185c",
        "email": "1621234624@facebook.com",
        "facebookId": "1621234624",
        "__v": 0,
        "favouriteRecommended": [],
        "favouriteEvents": [],
        "interests": [],
        "countriesVisited": [],
        "countriesToVisit": [],
        "description": [],
        "currentPosition": [],
        "profilePhotos": []
    }
}
```

### Login with email

```js
POST /users/login
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache

{ 
    "email" : "santiago@konacloud.io", 
    "password" : "clear300"
}

```

Response

```js
{
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImZhdm91cml0ZVJlY29tbWVuZGVkIjpbXSwiZmF2b3VyaXRlRXZlbnRzIjpbXSwiaW50ZXJlc3RzIjpbIjU2NTY2ZWI5YmVlODgyMTgzYzE3NTA3MCIsIjU2NTY2ZThiYmVlODgyMTgzYzE3NTA2ZSIsIjU2NTY2ZTViYmVlODgyMTgzYzE3NTA2NiJdLCJjb3VudHJpZXNWaXNpdGVkIjpbIjU2NTY2MGUxYmU5NzQzYTk0OThlZGQ2MyJdLCJjb3VudHJpZXNUb1Zpc2l0IjpbIjU2NTY2MGI4YmU5NzQzYTk0OThlZGQ2MCJdLCJkZXNjcmlwdGlvbiI6WyJTb21lIGRlc2NyaXB0aW9uIGFib3V0IG1lIl0sImN1cnJlbnRQb3NpdGlvbiI6W10sInByb2ZpbGVQaG90b3MiOltdfQ.VhtO-POeXVlbVjUvAdPjLy5pstcU_D2LBf5GkplWyag",
    "user": {
        "_id": "56569334954f75212231ad41",
        "email": "santiago@konacloud.io",
        "__v": 0,
        "birthPlace": {
            "name": "Montevideo, Uruguay",
            "countryCode": "UY"
        },
        "profileImageUrl": "bucket/5656959af660147e34d1ba4e",
        "birthday": "1989-06-20T00:00:00.000Z",
        "currentPlace": "Montevideo, Uruguay",
        "status": "VACATIONS",
        "favouriteRecommended": [],
        "favouriteEvents": [],
        "interests": [
            "56566eb9bee882183c175070",
            "56566e8bbee882183c17506e",
            "56566e5bbee882183c175066"
        ],
        "countriesVisited": [
            "565660e1be9743a9498edd63"
        ],
        "countriesToVisit": [
            "565660b8be9743a9498edd60"
        ],
        "description": [
            "Some description about me"
        ],
        "currentPosition": [],
        "profilePhotos": []
    }
}
```

## SIGN IN PAGE 2

![Simulator_Screen_Shot_Nov_26__2015__2.39.26_AM](http://git.teamkona.io/whatson/backend/uploads/444661028107404a4da72bc7ddb19b4b/Simulator_Screen_Shot_Nov_26__2015__2.39.26_AM.png)


### Upload profile Picture


```js
POST /bucket HTTP/1.1
Host: flipflop.dev.konabackend.com
Cache-Control: no-cache

----WebKitFormBoundaryE19zNvXGzXaLvS5C
Content-Disposition: form-data; name="file"; filename="Screen Shot 2015-11-22 at 01.26.22.png"
Content-Type: image/png


----WebKitFormBoundaryE19zNvXGzXaLvS5C
```

  Response

```js
{
    "url": "bucket/565693f5a6f070c027a15bb3"
}
```

### Get places from google


```
GET /maps/api/place/textsearch/json?key=AIzaSyDJsKQ25-BKRG4EetV0SIrQep6DYA_dPR0&query=montevideo HTTP/1.1
Host: maps.googleapis.com
```



```js
{
    "html_attributions": [],
    "results": [
        {
            "formatted_address": "Montevideo, Uruguay",
            "geometry": {
                "location": {
                    "lat": -34.9011127,
                    "lng": -56.16453139999999
                },
                "viewport": {
                    "northeast": {
                        "lat": -34.70193,
                        "lng": -56.0292436
                    },
                    "southwest": {
                        "lat": -34.9379555,
                        "lng": -56.4311685
                    }
                }
            },
            "icon": "https://maps.gstatic.com/mapfiles/place_api/icons/geocode-71.png",
            "id": "13ce4603475f6e0d1516a69408ea50884eb69c7f",
            "name": "Montevideo",
            "place_id": "ChIJ0_c7xv-An5URmexbNS4bMms",
            "reference": "CnRwAAAALC65_S3TV6IdY8p43RBzBm_03RB9ffwq0WUA5T2OSoEs1DahFnDaoRffRQLmaFEIJIqeabrovlrP2W7GqfqE3lPABK6YbYPhZPYCuMqOc6JXWBE0_Z250w_HsHRhUVo5v7nogyxHUOtns4ul-8-szRIQ370Igo7tipb1UkVj_uigcBoUIDHBsb9mjlnA5OQt7G4zfhABQoI",
            "types": [
                "locality",
                "political"
            ]
        }
    ],
    "status": "OK"
}
```

### Find country from place_id

  Request

```
GET https://maps.googleapis.com/maps/api/place/details/json?key=AIzaSyDJsKQ25-BKRG4EetV0SIrQep6DYA_dPR0&placeid=ChIJ0_c7xv-An5URmexbNS4bMms
```

  Response
```js
{
    "html_attributions": [],
    "result": {
        "address_components": [
            {
                "long_name": "Montevideo",
                "short_name": "Montevideo",
                "types": [
                    "locality",
                    "political"
                ]
            },
            {
                "long_name": "Departamento de Montevideo",
                "short_name": "Departamento de Montevideo",
                "types": [
                    "administrative_area_level_1",
                    "political"
                ]
            },
            {
                "long_name": "Uruguay",
                "short_name": "UY",
                "types": [
                    "country",
                    "political"
                ]
            }
        ],
        "adr_address": "<span class=\"locality\">Montevideo</span>, <span class=\"country-name\">Uruguay</span>",
        "formatted_address": "Montevideo, Uruguay",
        "geometry": {
            "location": {
                "lat": -34.9011127,
                "lng": -56.16453139999999
            },
            "viewport": {
                "northeast": {
                    "lat": -34.70193,
                    "lng": -56.0292436
                },
                "southwest": {
                    "lat": -34.9379555,
                    "lng": -56.4311685
                }
            }
        },
        "icon": "https://maps.gstatic.com/mapfiles/place_api/icons/geocode-71.png",
        "id": "13ce4603475f6e0d1516a69408ea50884eb69c7f",
        "name": "Montevideo",
        "place_id": "ChIJ0_c7xv-An5URmexbNS4bMms",
        "reference": "CnRwAAAAHpfohqXkbdFdYZWOFJd__S_-uCTWYdKBuz63cCO_L59vuq10A9Y3txMfiJIOHvw1HcJZ62THvzYDz1FxD0lEf4h_KAl98Smn_8Yb1WKqkAgKqxaZHch--UE6o1adK-03z37LtxlVygIwTFCFxQEreBIQaMDGbcpwksl0FsGuw38xgRoUUROj-d6uFzz9Lxw5npVj036gUXs",
        "scope": "GOOGLE",
        "types": [
            "locality",
            "political"
        ],
        "url": "https://maps.google.com/?q=Montevideo,+Uruguay&ftid=0x959f80ffc63bf7d3:0x6b321b2e355bec99",
        "vicinity": "Montevideo"
    },
    "status": "OK"
}
```


### Show country from by country ID

```js
GET /flags/:countryId.png
Host: flipflop.dev.konabackend.com
```

***countryId lowercase***

Example

```js
GET /flags/uy.png
Host: flipflop.dev.konabackend.com
```

### Update profile with photo,etc

  Request

```js
PUT /users HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.yin9vWd6ieRdyAh5N67xYyFMxtHaHDtNznq_13aDY3g
Cache-Control: no-cache

{  
   "profileImageUrl":"bucket/5656959af660147e34d1ba4e",
   "birthPlace":{  
      "name" : "Montevideo, Uruguay",
      "countryCode":"UY"
   },
   "birthday":"1989-06-20",
   "gender":"M"
}
```

## SIGN IN PAGE 3

![Simulator_Screen_Shot_Nov_26__2015__2.48.30_AM](http://git.teamkona.io/whatson/backend/uploads/f11f659bc59438c7f44400504d264ee4/Simulator_Screen_Shot_Nov_26__2015__2.48.30_AM.png)

### Get interests

  Request

```js
GET /interests HTTP/1.1
Host: flipflop.dev.konabackend.com
Cache-Control: no-cache
```

  Response

```js
[
    {
        "_id": "56566eb9bee882183c175070",
        "name": "WALKS",
        "color": "#094A38"
    },
    {
        "_id": "56566e8bbee882183c17506e",
        "name": "SPORT_TURISIM",
        "color": "#67BDFA"
    },

...
```

### Get countries list

  Request

```js
GET /countries HTTP/1.1
Host: flipflop.dev.konabackend.com
Cache-Control: no-cache
```

  Response

```js
[
    {
        "_id": "5656612f083a63804d6f18e5",
        "flag": "bucket/56566129083a63804d6f18e3",
        "name": "Venezuela",
        "__v": 0
    },
...
```

### Update profile page 3

Actual status posible values

- LOCAL
- AIMLESSLY
- WORK_AND_TRAVEL
- VACATIONS

  Request

```js
PUT /users HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.yin9vWd6ieRdyAh5N67xYyFMxtHaHDtNznq_13aDY3g
Cache-Control: no-cache

{  
   "countriesToVisit":[  
      "565660b8be9743a9498edd60"
   ],
   "countriesVisited":[  
      "565660e1be9743a9498edd63"
   ],
   "interests":[  
      "56566eb9bee882183c175070",
      "56566e8bbee882183c17506e",
      "56566e5bbee882183c175066"
   ],
   "status":"VACATIONS",
   "description":"Some description about me",
   "currentPlace":"Montevideo, Uruguay"
}
```

## Set current hostel


### List hostels

  Request

```js
GET /hostels HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache
```

  Response

```js
[
    { 
    "_id" : ObjectId("5656b549bee882183c175076"), 
    "name" : "El viajero Hostels", 
    "description" : "El Viajero Downtown Hostel & Suites is conveniently located in the heart of Montevideo: two blocks away from our most important Avenue 18 de Julio and just 10 minutes away from Montetvideo’s top places", 
    "meetingPoint" : "Bar", 
    "website" : "http://www.elviajerohostels.com/hostel-montevideo-down-town/", 
    "email" : "contacto@elviajerohostels.com", 
    "phone" : "099123456", 
    "zone" : "5656b4f2bee882183c175074", 
    "address" : "San jose y Rio negro", 
    "picture" : "bucket/565a3dccbee882183c175078", 
    "location" : [
        -34.9071263, 
        -56.1956573
    ]
  }
]
```

### Set current hostel

  Request

```js
PUT /users HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.yin9vWd6ieRdyAh5N67xYyFMxtHaHDtNznq_13aDY3g
Cache-Control: no-cache

{ 
  "currentHostel" : "5656b549bee882183c175076"
}
```

### Set current position

  Request

```js
PUT /users HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.yin9vWd6ieRdyAh5N67xYyFMxtHaHDtNznq_13aDY3g
Cache-Control: no-cache

{ 
  "currentPosition" : [-56.1956573, -34.9071263]
}

```

{ 
  "currentPosition" : [longitude, latitude]
}

## Home

```js
GET /home HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.yin9vWd6ieRdyAh5N67xYyFMxtHaHDtNznq_13aDY3g
Cache-Control: no-cache
```

Respose

```js
{
    "plans": 0,
    "events": 3,
    "backpackers": 5
}
```

## Forgot password

```js
POST /users/forgot-password HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache

{ "email": "tin.isasa@gmail.com" }

```

## Locations (Recommended)

### Get locations

![Screen_Shot_2015-11-28_at_18.31.51](http://git.teamkona.io/whatson/backend/uploads/45f418cb91d84852ced3911531a34ea0/Screen_Shot_2015-11-28_at_18.31.51.png)


  Request

```js
GET /locations HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache
```

  Response

```js
[
    {
        "_id": "565a15c01cfb29af65c182c2",
        "name": "Paris",
        "picture": "bucket/565a154e1585573b639023ea",
        "price": "1",
        "days": [
            {
                "name": "Lunes",
                "benefits": [
                    {
                        "startHour": 3,
                        "endHour": 6,
                        "type": {
                            "_id": "FREE",
                            "name": "Free"
                        },
                        "description": "Pizza"
                    }
                ]
            },
            {
                "name": "Martes",
                "benefits": []
            },
            {
                "name": "Miercoles",
                "benefits": []
            },
            {
                "name": "Jueves",
                "benefits": [
                    {
                        "startHour": 1,
                        "endHour": 5,
                        "type": {
                            "_id": "FREE",
                            "name": "Free"
                        },
                        "description": "Pizza"
                    },
                    {
                        "startHour": 3,
                        "endHour": 5,
                        "type": {
                            "_id": "2X1",
                            "name": "2x1"
                        },
                        "description": "Champagne"
                    }
                ]
            },
            {
                "name": "Viernes",
                "benefits": []
            },
            {
                "name": "Sabado",
                "benefits": [
                    {
                        "startHour": 2,
                        "endHour": 12,
                        "type": {
                            "_id": "2X1",
                            "name": "2x1"
                        },
                        "description": "Champagne"
                    }
                ]
            },
            {
                "name": "Domingo",
                "benefits": []
            }
        ]
    },
    {
        "_id": "565a14e8cf21e9635e1c5ec7",
        "name": "Brickell",
        "picture": "bucket/565a14a07bbcc7f05b1f6fd5",
        "price": "1",
        "days": [
            {
                "name": "Lunes",
                "benefits": [
                    {
                        "startHour": 2,
                        "endHour": 5,
                        "type": {
                            "_id": "2X1",
                            "name": "2x1"
                        },
                        "description": "CHELA"
                    }
                ]
            },
            {
                "name": "Martes",
                "benefits": []
            },
            {
                "name": "Miercoles",
                "benefits": []
            },
            {
                "name": "Jueves",
                "benefits": []
            },
            {
                "name": "Viernes",
                "benefits": []
            },
            {
                "name": "Sabado",
                "benefits": []
            },
            {
                "name": "Domingo",
                "benefits": []
            }
        ]
    }
]
```

### Get all location attributes

```js
GET /locations HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
```

** Get one location by id**

```js
GET /locations/:id HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
```

## Events

### Get all events

Request

```js
GET /events HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache
```

  Response

```js
[  
   {  
      "_id":"565cfa8dc2e649e9dbb29894",
      "_createdAt":"2015-12-01T00:31:29.411Z",
      "_updatedAt":"2015-12-01T00:31:29.411Z",
      "name":"Another Event",
      "startTime":"02:00",
      "endTime":"03:00",
      "address":"abadie y benito blano",
      "creditCard":true,
      "english":false,
      "age":"ALL",
      "picture":"bucket/565cea2ec2d09c69317694a7",
      "category":"565ce180c8e51cf84c38f9a0",
      "description":"The coolest event",
      "website":"cool.event",
      "country":"565660b8be9743a9498edd60",
      "city":"5656b4d1bee882183c175072",
      "zone":"565bbc9c3f6ad1fc51a7bfb3",
      "startDate":"2015-11-20T00:00:00.000Z",
      "price":"3",
      "priceNotes":"Some price",
      "__v":0,
      "endDate":"2015-11-26T00:00:00.000Z",
      "location":[  
         -34.917235,
         -56.15034220000001
      ],
      "peopleGoing": 1,
      "people": [
		{
			"_id": "56569334954f75212231ad41",
			"email": "santiago@konacloud.io",
			"birthPlace": {
			    "name": "Montevideo, Uruguay",
			    "countryCode": "UY"
		        },
			"profileImageUrl": "bucket/5656959af660147e34d1ba4e",
			"birthday": "1989-06-20T00:00:00.000Z",
			"name": "Santiago Cotto"
		}
	] 
   },
   {  
      "_id":"565cfa67c2e649e9dbb29892",
      "_createdAt":"2015-12-01T00:31:29.411Z",
      "_updatedAt":"2015-12-01T00:31:29.411Z",
      "name":"Other Event",
      "startTime":"02:00",
      "endTime":"03:00",
      "address":"abadie y benito blano",
      "creditCard":true,
      "english":false,
      "age":"ALL",
      "picture":"bucket/565cea2ec2d09c69317694a7",
      "category":"565ce180c8e51cf84c38f9a0",
      "description":"The coolest event",
      "website":"cool.event",
      "country":"565660b8be9743a9498edd60",
      "city":"5656b4d1bee882183c175072",
      "zone":"565bbc9c3f6ad1fc51a7bfb3",
      "startDate":"2015-11-20T00:00:00.000Z",
      "price":"3",
      "priceNotes":"Some price",
      "__v":0,
      "endDate":"2015-11-26T00:00:00.000Z",
      "location":[  
         -34.917235,
         -56.15034220000001
      ],
      "peopleGoing": 1,
      "people": [
		{
			"_id": "56569334954f75212231ad41",
			"email": "santiago@konacloud.io",
			"birthPlace": {
			    "name": "Montevideo, Uruguay",
			    "countryCode": "UY"
		        },
			"profileImageUrl": "bucket/5656959af660147e34d1ba4e",
			"birthday": "1989-06-20T00:00:00.000Z",
			"name": "Santiago Cotto"
		}
	] 
   }
]
```

### Attend event

***This is an idempotent HTTP method***

```js
POST /events/565cfa67c2e649e9dbb29892/attend HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache

{}
```

### No Attend Event

***This is an idempotent HTTP method***

```js
DELETE /events/565cfa67c2e649e9dbb29892/attend HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache

{}
```

### Get people attending to a event

```js
GET /events/565cfa67c2e649e9dbb29892/people HTTP/1.1
Host: localhost:2006
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache

```

Response

```js
[
    {
        "_id": "56569334954f75212231ad41",
        "email": "santiago@konacloud.io",
        "birthPlace": {
            "name": "Montevideo, Uruguay",
            "countryCode": "UY"
        },
        "profileImageUrl": "bucket/5656959af660147e34d1ba4e",
        "birthday": "1989-06-20T00:00:00.000Z",
        "name": "Santiago Cotto"
    }
]
```

## Plan

### Create Plan (Event)

  Request

```js
POST /plans HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache

{
  "meetingTime" : "20:00",
  "meetingPoint" : "Hostel Bar",
  "event" : "565cfa8dc2e649e9dbb29894"
}
```

### Create Plan (Location)

  Request

```js
POST /plans HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache

{
  "meetingTime" : "20:00",
  "meetingPoint" : "Hostel Bar",
  "location" : "565f3027f386ddd84bf764b4"
}
```

### Get plans

```js
GET /plans HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache
```

 Response

```js
[
    {
        "_id": "56633e599f652d58063c0b85",
        "_createdAt": "2015-12-05T19:43:21.228Z",
        "_updatedAt": "2015-12-05T19:43:21.228Z",
        "hostel": "5656b549bee882183c175076",
        "meetingTime": "20:00",
        "meetingPoint": "Hostel Bar",
        "location": "565f3027f386ddd84bf764b4",
        "__v": 0
    },
    {
        "_id": "56633e609f652d58063c0b86",
        "_createdAt": "2015-12-05T19:43:28.870Z",
        "_updatedAt": "2015-12-05T19:43:28.870Z",
        "hostel": "5656b549bee882183c175076",
        "meetingTime": "20:00",
        "meetingPoint": "Hostel Bar",
        "event": "565cfa8dc2e649e9dbb29894",
        "__v": 0
    }
]
```

### Get plans populating references

```js
GET /plans?populate[]=location&populate[]=event HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache
```

  Response

```js
[
    {
        "_id": "56633e599f652d58063c0b85",
        "_createdAt": "2015-12-05T19:43:21.228Z",
        "_updatedAt": "2015-12-05T19:43:21.228Z",
        "hostel": "5656b549bee882183c175076",
        "meetingTime": "20:00",
        "meetingPoint": "Hostel Bar",
        "location": {
            "_id": "565f3027f386ddd84bf764b4",
            "_createdAt": "2015-12-02T17:53:43.181Z",
            "_updatedAt": "2015-12-02T17:53:43.181Z",
            "name": "lupa",
            "address": "Gonzalo ramirez 1543",
            "creditCard": true,
            "english": true,
            "age": ">35",
            "picture": "bucket/565f2f81f386ddd84bf764b1",
            "category": "5659f53b6388abeba14bc875",
            "description": "xxxx",
            "country": "565660b8be9743a9498edd60",
            "city": "5656b4d1bee882183c175072",
            "zone": "565bbc9c3f6ad1fc51a7bfb3",
            "price": "3",
            "contact": {
                "name": "Maite",
                "tel": "094818037"
            },
            "website": "www.xxx.com",
            "__v": 0,
            "location": [
                -34.9121919,
                -56.177388399999984
            ],
            "days": [
                {
                    "name": "Lunes",
                    "benefits": [
                        {
                            "startHour": "21:00",
                            "endHour": "2:00",
                            "type": "2X1",
                            "description": "Cervezas",
                            "people": 6
                        }
                    ]
                },
                {
                    "name": "Martes",
                    "benefits": []
                },
                {
                    "name": "Miercoles",
                    "benefits": []
                },
                {
                    "name": "Jueves",
                    "benefits": []
                },
                {
                    "name": "Viernes",
                    "benefits": []
                },
                {
                    "name": "Sabado",
                    "benefits": []
                },
                {
                    "name": "Domingo",
                    "benefits": []
                }
            ]
        },
        "__v": 0
    },
    {
        "_id": "56633e609f652d58063c0b86",
        "_createdAt": "2015-12-05T19:43:28.870Z",
        "_updatedAt": "2015-12-05T19:43:28.870Z",
        "hostel": "5656b549bee882183c175076",
        "meetingTime": "20:00",
        "meetingPoint": "Hostel Bar",
        "event": {
            "_id": "565cfa8dc2e649e9dbb29894",
            "_createdAt": "2015-12-01T00:31:29.411Z",
            "_updatedAt": "2015-12-01T00:31:29.411Z",
            "name": "Another Event",
            "startTime": "02:00",
            "endTime": "03:00",
            "address": "abadie y benito blano",
            "language": "English",
            "age": "ALL",
            "picture": "bucket/565cea2ec2d09c69317694a7",
            "category": "565ce180c8e51cf84c38f9a0",
            "description": "The coolest event",
            "website": "cool.event",
            "country": "565660b8be9743a9498edd60",
            "city": "5656b4d1bee882183c175072",
            "zone": "565bbc9c3f6ad1fc51a7bfb3",
            "startDate": "2015-11-20T00:00:00.000Z",
            "price": 200,
            "priceNotes": "Some price",
            "__v": 0,
            "endDate": "2015-11-26T00:00:00.000Z",
            "payMethods": [
                "CASH",
                "CREDIT_CARD",
                "DEBIT_CARD"
            ],
            "location": [
                -34.917235,
                -56.15034220000001
            ]
        },
        "__v": 0
    }
]
```

### Attend Plan

***This is an idempotent HTTP method***

```js
POST /plans/5664e5c5f8f94c14075fc414/attend HTTP/1.1
Host: localhost:2006
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache

{ }
```

### No Attend Plan

***This is an idempotent HTTP method***

```js
DELETE /plans/5664e5c5f8f94c14075fc414/attend HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache

{ }
```

### Get people attending a plan

```js
GET /plans/5664e57cf8f94c14075fc413/people HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache

{
}
```

Response

```js
[
    {
        "_id": "56569334954f75212231ad41",
        "email": "santiago@konacloud.io",
        "birthPlace": {
            "countryCode": "UY",
            "name": "Montevideo, Uruguay"
        },
        "profileImageUrl": "bucket/5656959af660147e34d1ba4e",
        "birthday": "1989-06-20T00:00:00.000Z",
        "name": "Santiago Cotto",
        "age": 26
    }
]
```


## IceBrecker

### Send deviceId

IOS and android deviceId/registerId -> Push Notification

```js
POST /devices HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NWYxZjAzYTY0OGFhN2JmMTIwYmI1ZTkiLCJlbWFpbCI6InN0cmluZyIsImF1dGhUeXBlIjoic3RyaW5nIiwibmFtZSI6InN0cmluZyIsIl9jcmVhdGVkX2F0Ijoic3RyaW5nIiwiX3VwZGF0ZWRfYXQiOiJzdHJpbmciLCJfX3YiOjAsImlhdCI6MTQ0NzMwNzEzNH0.LkmcyzhoL09uYec7_k9dQ_zvozbZ5pNHQJeKs_GctE4
Cache-Control: no-cache

{ 
  "deviceId" : "1234", 
  "deviceType" : "android" 
}

```

deviceType values:
  - android
  - ios
  - 
### Get users in Current Hostel

  Request

```js
GET /users/current-hostel HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache
```

  Response

```js
[
    {
        "_id": "56569334954f75212231ad41",
        "email": "santiago@konacloud.io",
        "birthPlace": {
            "name": "Montevideo, Uruguay",
            "countryCode": "UY"
        },
        "profileImageUrl": "bucket/5656959af660147e34d1ba4e",
        "birthday": "1989-06-20T00:00:00.000Z"
    }
]
```


### Get nearby users

```js
GET /users/nearby HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjcwZDdiNzY0MTE5MjBjMWIwNzRkNDAiLCJfY3JlYXRlZEF0IjoiMjAxNS0xMi0xNlQwMzoxNzoxMS41MzFaIiwiX3VwZGF0ZWRBdCI6IjIwMTUtMTItMTZUMDM6MTc6MTEuNTMxWiIsImVtYWlsIjoiaGVybmFuQHRlYW1rb25hLmlvIiwiX192IjowLCJuYW1lIjoiSGVybmFuIiwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgTW9udGV2aWRlbyBEZXBhcnRtZW50LCBVcnVndWF5IiwiY291bnRyeUNvZGUiOiJVWSJ9LCJiaXJ0aGRheSI6IjE5ODktMTItMTZUMDA6MDA6MDAuMDAwWiIsImhvd1RyYXZlbCI6IkFMT05FIiwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NzFiYWE0ODIzMDM4MzEzMDU4YTlmNyIsImdlbmRlciI6Ik0iLCJjdXJyZW50UGxhY2UiOiJNb250ZXZpZGVvLCBNb250ZXZpZGVvIERlcGFydG1lbnQsIFVydWd1YXkiLCJjdXJyZW50SG9zdGVsIjoiNTY1NmI1NDliZWU4ODIxODNjMTc1MDc2IiwiZGVzY3JpcHRpb24iOiJIZXJuYW4iLCJzdGF0dXMiOiJWQUNBVElPTlMiLCJmcmllbmRzIjpbXSwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOlsiNTY1NjZlNWJiZWU4ODIxODNjMTc1MDY2IiwiNTY1NjZlMzBiZWU4ODIxODNjMTc1MDYwIiwiNTY1NjZlODJiZWU4ODIxODNjMTc1MDZjIl0sImNvdW50cmllc1Zpc2l0ZWQiOlsiNTY3MGNmZTczZWJjMGFhMDA1NzlmZmJlIiwiNTY3MGNmZTczZWJjMGFhMDA1NzlmZjJhIiwiNTY3MGNmZTczZWJjMGFhMDA1NzlmZmJmIl0sImNvdW50cmllc1RvVmlzaXQiOlsiNTY3MGNmZTczZWJjMGFhMDA1NzlmZWVlIl0sImN1cnJlbnRQb3NpdGlvbiI6WyIzNy4zMzIzMzEiLCItMTIyLjAzMTIxOSJdLCJwcm9maWxlUGhvdG9zIjpbXX0.zESQOefZliHpAD-a6pJPqIh-O_NtVMAkrgX2kLaIANQ
Cache-Control: no-cache
```

Response

```js
[
    {
        "_id": "5670d7b76411920c1b074d40",
        "email": "hernan@teamkona.io",
        "currentPosition": [
            37.332331,
            -60.031219
        ],
        "name": "Hernan",
        "birthPlace": {
            "countryCode": "UY",
            "name": "Montevideo, Montevideo Department, Uruguay"
        },
        "birthday": "1989-12-16T00:00:00.000Z",
        "howTravel": "ALONE",
        "profileImageUrl": "bucket/5671baa4823038313058a9f7",
        "age": 26,
        "distance": 0
    },
    {
        "_id": "5670d92e3f6ee968b8cb79d2",
        "email": "hernanalbano@gmail.com",
        "name": "Hernán Albano",
        "birthPlace": {
            "countryCode": "UY",
            "name": "Montevideo, Montevideo Department, Uruguay"
        },
        "birthday": "2015-12-16T00:00:00.000Z",
        "howTravel": "ALONE",
        "profileImageUrl": "bucket/5671ddb39570fe1f2b6d9d2f",
        "currentPosition": [
            37.332331,
            -60.031219
        ],
        "age": 0,
        "distance": 0
    },
    {
        "_id": "5672ff0781c11a1754debb2e",
        "email": "gonzalo@teamkona.io",
        "currentPosition": [
            37.332331,
            -60.031219
        ],
        "howTravel": "FAMILY",
        "birthPlace": {
            "name": "Melo, Cerro Largo, Uruguay",
            "countryCode": "UY"
        },
        "profileImageUrl": "bucket/5672ff3181c11a1754debb2f",
        "birthday": "1989-08-17T00:00:00.000Z",
        "name": "GMELO",
        "age": 26,
        "distance": 0
    }
]
```

### Get phrases

```
GET /phrases HTTP/1.1
Host: flipflop.dev.konabackend.com
```

  Response

```js
[  
   {  
      _id:"566223d73f6ee968b8cb7983",
      nameEs:"Gracias!",
      nameEn:"Thanks!",
      color:"#E22D20"
   },
   {  
      _id:"566223d73f6ee968b8cb7982",
      nameEs:"Voy a llegar tarde",
      nameEn:"I'll be arriving later",
      color:"#FC2461"
   }
...
]
``` 

### Send phrase

```js
POST /messages HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache

{  
   "to":"565f1a7af386ddd84bf764aa",
   "phrase":"566223d73f6ee968b8cb7982"
}
```

### Send emoticon

```js
POST /messages HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache

{  
   "to":"565f1a7af386ddd84bf764aa",
   "emoticon":"U+1F601"
}
```

### Send event

```js
POST /messages HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache

{  
   "to":"565f1a7af386ddd84bf764aa",
   "event":"565cfa8dc2e649e9dbb29894",
   "data" : {
   	"meetingTime" : "10:00",
   	"meetingPoint" : "Bar"
   }
}
```

### Send location

```js
POST /messages HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache

{  
   "to":"565f1a7af386ddd84bf764aa",
   "location":"565f3027f386ddd84bf764b4",
   "data" : {
   	"meetingTime" : "10:00",
   	"meetingPoint" : "Bar"
   }
}
```

  Response

```js
{
    "_id": "5660cc4031cee6f980b97f38",
    "_createdAt": "2015-12-03T23:12:00.706Z",
    "_updatedAt": "2015-12-03T23:12:00.706Z",
    ...
}
```

### Get my conversations

  Request

```js
GET /conversations HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache

```

  Response

```js
[
    {
        "_id": "5660cc1631cee6f980b97f36",
        "_createdAt": "2015-12-03T23:11:18.334Z",
        "_updatedAt": "2015-12-03T23:12:01.109Z",
        "message": {
            "_id": "5660cc4031cee6f980b97f38",
            "_createdAt": "2015-12-03T23:12:00.706Z",
            "_updatedAt": "2015-12-03T23:12:00.706Z",
            "from": "56569334954f75212231ad41",
            "to": "565f1a7af386ddd84bf764aa",
            "emoticon": ":)",
            "__v": 0
        },
        "__v": 0,
        "user": {
            "_id": "565f1a7af386ddd84bf764aa",
            "email": "hernan2@teamkona.io",
            "birthPlace": {
                "countryCode": "UY",
                "name": "Sarandi ­ Grande, Florida, Uruguay"
            },
            "birthday": "2015-02-12T06:00:00.000Z",
            "profileImageUrl": "bucket/565f1a84f386ddd84bf764ab"
        }
    }
]
```


### Get Conversation by ConversationId

```js
GET /conversations/5660cc1631cee6f980b97f36 HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache
```

  Response

```js
[
    {
        "_id": "5660cc4031cee6f980b97f38",
        "_createdAt": "2015-12-03T23:12:00.706Z",
        "_updatedAt": "2015-12-03T23:12:00.706Z",
        "from": "56569334954f75212231ad41",
        "to": "565f1a7af386ddd84bf764aa",
        "phrase":"566223d73f6ee968b8cb7982",
        "__v": 0
    },
    {
        "_id": "5660cc3331cee6f980b97f37",
        "_createdAt": "2015-12-03T23:11:47.990Z",
        "_updatedAt": "2015-12-03T23:11:47.990Z",
        "from": "56569334954f75212231ad41",
        "to": "565f1a7af386ddd84bf764aa",
        "emoticon":"U+1F601",
        "__v": 0
    },
    {
        "_id": "5660cc1531cee6f980b97f35",
        "_createdAt": "2015-12-03T23:11:17.897Z",
        "_updatedAt": "2015-12-03T23:11:17.897Z",
        "from": "56569334954f75212231ad41",
        "to": "565f1a7af386ddd84bf764aa",
        "event": "565cfa8dc2e649e9dbb29894",
        "__v": 0
    }
]
```

### Get Conversation by userId

```js
GET /conversations/find-one?where[user]=565f1a7af386ddd84bf764aa&limit=10&offset=0 HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache
```

  Response

```js
[
    {
        "_id": "5660cc4031cee6f980b97f38",
        "_createdAt": "2015-12-03T23:12:00.706Z",
        "_updatedAt": "2015-12-03T23:12:00.706Z",
        "from": "56569334954f75212231ad41",
        "to": "565f1a7af386ddd84bf764aa",
        "phrase":"566223d73f6ee968b8cb7982",
        "__v": 0
    },
    {
        "_id": "5660cc3331cee6f980b97f37",
        "_createdAt": "2015-12-03T23:11:47.990Z",
        "_updatedAt": "2015-12-03T23:11:47.990Z",
        "from": "56569334954f75212231ad41",
        "to": "565f1a7af386ddd84bf764aa",
        "emoticon":"U+1F601",
        "__v": 0
    },
    {
        "_id": "5660cc1531cee6f980b97f35",
        "_createdAt": "2015-12-03T23:11:17.897Z",
        "_updatedAt": "2015-12-03T23:11:17.897Z",
        "from": "56569334954f75212231ad41",
        "to": "565f1a7af386ddd84bf764aa",
        "event": "565cfa8dc2e649e9dbb29894",
        "__v": 0
    }
]
```


## Friends

### Add users as a friend

```js
POST /users/friends HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache

{ "user" : "5665b747543992a80252d04f" }

```

### Get my friends

```js
GET /users/friends HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache
```

### Remove friend

```js
DELETE /users/friends/56676c43ab5e87916f0dc9f4 HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache
```


## Destinations

### Places Autocomplete

find places with name like  **monte**

```js
GET /cities?where[name][$options]=i&limit=20&where[name][$regex]=monte
Host: flipflop.dev.konabackend.com
Content-Type: application/json
```

Response

```js
[  
   {  
      "_id":"56720b113f6ee968b8cb88c5",
      "country":"5670cfe73ebc0aa00579ffbf",
      "name":"Montevideo",
      "_updatedAt":"2015-12-17T01:52:33.690Z",
      "__v":0
   },
   {  
      "_id":"56720a013f6ee968b8cb8840",
      "country":"5670cfe73ebc0aa00579ff48",
      "name":"Montepulciano",
      "_updatedAt":"2015-12-17T01:52:33.820Z",
      "__v":0
   }
...
]
```

### Add Destination

```js
POST /destinations HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfX3YiOjAsIl9jcmVhdGVkQXQiOiIyMDE1LTEyLTE3VDAxOjU0OjI1LjU3N1oiLCJfdXBkYXRlZEF0IjoiMjAxNS0xMi0xN1QwMTo1NDoyNS41NzdaIiwiZW1haWwiOiJzYW50aWFnb0Brb25hY2xvdWQuaW8iLCJfaWQiOiI1NjcyMTVkMTJiODdiNmMwMGNkYmUyMTQiLCJmcmllbmRzIjpbXSwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImN1cnJlbnRQb3NpdGlvbiI6W10sInByb2ZpbGVQaG90b3MiOltdfQ.ekj9KAbJIaJ2zzQH01qhLUgko-FuhgYniZyhSZbgQ8k
Cache-Control: no-cache

{
  "city" : "56720b113f6ee968b8cb88c5",
  "from" : "2015-12-25",
  "to" : "2015-12-28"
}
```

### Get my destinations countries

```js
GET /destinations/countries
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfX3YiOjAsIl9jcmVhdGVkQXQiOiIyMDE1LTEyLTE3VDAxOjU0OjI1LjU3N1oiLCJfdXBkYXRlZEF0IjoiMjAxNS0xMi0xN1QwMTo1NDoyNS41NzdaIiwiZW1haWwiOiJzYW50aWFnb0Brb25hY2xvdWQuaW8iLCJfaWQiOiI1NjcyMTVkMTJiODdiNmMwMGNkYmUyMTQiLCJmcmllbmRzIjpbXSwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImN1cnJlbnRQb3NpdGlvbiI6W10sInByb2ZpbGVQaG90b3MiOltdfQ.ekj9KAbJIaJ2zzQH01qhLUgko-FuhgYniZyhSZbgQ8k
Cache-Control: no-cache
```

Response

```js
[
    {
        "_id": "5670cfe73ebc0aa00579ffbf",
        "_createdAt": "2015-12-16T02:43:51.347Z",
        "_updatedAt": "2015-12-16T02:43:51.347Z",
        "name": "Uruguay",
        "countryCode": "UY",
        "__v": 0
    }
]
```

### Get my destinations by country

```js
GET /destinations?where[country]=5670cfe73ebc0aa00579ffbf
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfX3YiOjAsIl9jcmVhdGVkQXQiOiIyMDE1LTEyLTE3VDAxOjU0OjI1LjU3N1oiLCJfdXBkYXRlZEF0IjoiMjAxNS0xMi0xN1QwMTo1NDoyNS41NzdaIiwiZW1haWwiOiJzYW50aWFnb0Brb25hY2xvdWQuaW8iLCJfaWQiOiI1NjcyMTVkMTJiODdiNmMwMGNkYmUyMTQiLCJmcmllbmRzIjpbXSwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImN1cnJlbnRQb3NpdGlvbiI6W10sInByb2ZpbGVQaG90b3MiOltdfQ.ekj9KAbJIaJ2zzQH01qhLUgko-FuhgYniZyhSZbgQ8k
Cache-Control: no-cache
```

Response

```js
[
    {
        "_id": "5673328a4ebd932945cf4bf4",
        "_createdAt": "2015-12-17T22:09:14.733Z",
        "_updatedAt": "2015-12-17T22:09:14.733Z",
        "country": {
            "_id": "5670cfe73ebc0aa00579ffbf",
            "_createdAt": "2015-12-16T02:43:51.347Z",
            "_updatedAt": "2015-12-16T02:43:51.347Z",
            "name": "Uruguay",
            "countryCode": "UY",
            "__v": 0
        },
        "user": "567215d12b87b6c00cdbe214",
        "to": "2015-12-19T00:00:00.000Z",
        "city": {
            "_id": "56720b113f6ee968b8cb88c5",
            "country": "5670cfe73ebc0aa00579ffbf",
            "name": "Montevideo",
            "_updatedAt": "2015-12-17T01:52:33.690Z",
            "__v": 0
        },
        "from": "2015-12-17T00:00:00.000Z",
        "__v": 0,
        "picture": "https://farm6.staticflickr.com/5731/23533632880_fffece1de2.jpg"
    },
    {
        "_id": "5672f8e4a2a5dcf20e803a29",
        "_createdAt": "2015-12-17T18:03:16.104Z",
        "_updatedAt": "2015-12-17T18:03:16.104Z",
        "country": {
            "_id": "5670cfe73ebc0aa00579ffbf",
            "_createdAt": "2015-12-16T02:43:51.347Z",
            "_updatedAt": "2015-12-16T02:43:51.347Z",
            "name": "Uruguay",
            "countryCode": "UY",
            "__v": 0
        },
        "user": "567215d12b87b6c00cdbe214",
        "city": {
            "_id": "56720b113f6ee968b8cb88c5",
            "country": "5670cfe73ebc0aa00579ffbf",
            "name": "Montevideo",
            "_updatedAt": "2015-12-17T01:52:33.690Z",
            "__v": 0
        },
        "from": "2015-12-25T00:00:00.000Z",
        "to": "2015-12-28T00:00:00.000Z",
        "__v": 0,
        "picture": "https://farm1.staticflickr.com/730/23201225274_38ed7f4882.jpg"
    }
]
```


