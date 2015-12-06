# Endpoints

**Dev**

```
http://flipflop.dev.konabackend.com
```

**Stg**

```
http://flipflop.stg.konabackend.com
```


# Basic

All the API (/resource, /resource/:id, /resource/find-one have this features

Example.

```
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
  zone: "565bbc9c3f6ad1fc51a7bfb3",

```

## Where

Find

```
GET /locations?where[category]=5659f53b6388abeba14bc875
```

## Select

Project fields

```
GET /locations?select[name]=1
```

Using multiple conditions

```
GET /locations?select[name]=1&where[category]=5659f53b6388abeba14bc875
```

## Sort

Sorting by field

```
GET /locations?sort[_updatedAt]=1
```

```
GET /locations?sort[_updatedAt]=-1
```

## Populate

Populate model reference

```
GET locations?populate[]=category&populate[]=zone&populate[]=country&populate[]=city
```

# Register

## Register with email

### Request

```
POST /users HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache

{  
   "email":"santiago@konacloud.io",
   "password":"****"
}
```

### Response

```
{
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfX3YiOjAsImVtYWlsIjoic2FudGlhZ29Aa29uYWNsb3VkLmlvIiwiX2lkIjoiNTY1NjkzMzQ5NTRmNzUyMTIyMzFhZDQxIiwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.wtknVCA1ykQ7q0261TZyahgUqZ15hbDwtExcuyh75vY",
    "user": {
        "__v": 0,
        "email": "santiago@konacloud.io",
        "_id": "56569334954f75212231ad41"
    }
}
```


## Register/Login with Facebook

### Request

```
POST /users/login-with-facebook HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
x-facebook-access-token: CAACEdEose0cBAJNKSGogM4TAHOABUwVUXqxTfnw10gWZBdXf8k7AXgZC76FIbP2XolVMWxVwmK3wMBMiPmEJcM0Rrct1d671ZCSkZCozbUNAGKsYwUb1cGAfovMAcet07zCy2Rvcwh264htCA9gBaSnEQ2j5fgC104EwngunrlH37Vwwhg9zEFuV95TkmAWI6qdZCYLJiuwQeE3X41k7z
Cache-Control: no-cache

{ }

```

### Response

```
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

## Login with email

### Request

```
POST /users/login
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache

{ 
    "email" : "santiago@konacloud.io", 
    "password" : "clear300"
}

```

### Response

```
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

# SIGN IN PAGE 2

![Simulator_Screen_Shot_Nov_26__2015__2.39.26_AM](http://git.teamkona.io/whatson/backend/uploads/444661028107404a4da72bc7ddb19b4b/Simulator_Screen_Shot_Nov_26__2015__2.39.26_AM.png)


## Upload profile Picture

### Request

```
POST /bucket HTTP/1.1
Host: flipflop.dev.konabackend.com
Cache-Control: no-cache

----WebKitFormBoundaryE19zNvXGzXaLvS5C
Content-Disposition: form-data; name="file"; filename="Screen Shot 2015-11-22 at 01.26.22.png"
Content-Type: image/png


----WebKitFormBoundaryE19zNvXGzXaLvS5C
```

### Response

```
{
    "url": "bucket/565693f5a6f070c027a15bb3"
}
```

## Get places from google

### Request

```
GET /maps/api/place/textsearch/json?key=AIzaSyDJsKQ25-BKRG4EetV0SIrQep6DYA_dPR0&query=montevideo HTTP/1.1
Host: maps.googleapis.com
```

### Response

```
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

## Find country from place_id

### Request

```
GET https://maps.googleapis.com/maps/api/place/details/json?key=AIzaSyDJsKQ25-BKRG4EetV0SIrQep6DYA_dPR0&placeid=ChIJ0_c7xv-An5URmexbNS4bMms
```

### Response
```
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


## Show country from by country ID

```
GET /flags/:countryId.png
Host: flipflop.dev.konabackend.com
```

***countryId lowercase***

Example

```
GET /flags/uy.png
Host: flipflop.dev.konabackend.com
```

## Update profile with photo, birthPlace,Birthday and gender

### Request

```
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

# SIGN IN PAGE 3

![Simulator_Screen_Shot_Nov_26__2015__2.48.30_AM](http://git.teamkona.io/whatson/backend/uploads/f11f659bc59438c7f44400504d264ee4/Simulator_Screen_Shot_Nov_26__2015__2.48.30_AM.png)

## Get interests

### Request

```
GET /interests HTTP/1.1
Host: flipflop.dev.konabackend.com
Cache-Control: no-cache
```

### Response

```
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

## Get countries list

### Request

```
GET /countries HTTP/1.1
Host: flipflop.dev.konabackend.com
Cache-Control: no-cache
```

### Response

```
[
    {
        "_id": "5656612f083a63804d6f18e5",
        "flag": "bucket/56566129083a63804d6f18e3",
        "name": "Venezuela",
        "__v": 0
    },
...
```

## Update profile page 3

Actual status posible values

- LOCAL
- AIMLESSLY
- WORK_AND_TRAVEL
- VACATIONS

### Request

```
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

# Set current hostel


## List hostels

### Request

```
GET /hostels HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache
```

### Response

```
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

## Set current hostel

### Request

```
PUT /users HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.yin9vWd6ieRdyAh5N67xYyFMxtHaHDtNznq_13aDY3g
Cache-Control: no-cache

{ 
  "currentHostel" : "5656b549bee882183c175076"
}

```

## Set current position

### Request

```
PUT /users HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.yin9vWd6ieRdyAh5N67xYyFMxtHaHDtNznq_13aDY3g
Cache-Control: no-cache

{ 
  "currentPosition" : [-34.9071263, -56.1956573]
}

```

# Home

## Request

```
GET /home HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiZmF2b3VyaXRlUmVjb21tZW5kZWQiOltdLCJmYXZvdXJpdGVFdmVudHMiOltdLCJpbnRlcmVzdHMiOltdLCJjb3VudHJpZXNWaXNpdGVkIjpbXSwiY291bnRyaWVzVG9WaXNpdCI6W10sImRlc2NyaXB0aW9uIjpbXSwiY3VycmVudFBvc2l0aW9uIjpbXSwicHJvZmlsZVBob3RvcyI6W119.yin9vWd6ieRdyAh5N67xYyFMxtHaHDtNznq_13aDY3g
Cache-Control: no-cache
```

## Respose

```
{
    "plans": 0,
    "events": 3,
    "backpackers": 5
}
```

# Explore

## Get locations

![Screen_Shot_2015-11-28_at_18.31.51](http://git.teamkona.io/whatson/backend/uploads/45f418cb91d84852ced3911531a34ea0/Screen_Shot_2015-11-28_at_18.31.51.png)


### Request

```
GET /locations HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache
```

### Response

```
[
    {
        "_id": "565a15c01cfb29af65c182c2",
        "name": "Paris",
        "picture": "bucket/565a154e1585573b639023ea",
        "price": "1",
        "peopleGoing": 4,
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
        "peopleGoing": 4,
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

## Get all location attributes

```
GET /locations HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
```

## Get one location by id

```
GET /locations/:id HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
```

## Get events


### Request

```
GET /events HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Cache-Control: no-cache
```

### Response

```
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
      ]
   },
   {  
      "_id":"565cea615876c39f334f8765",
      "_createdAt":"2015-12-01T00:31:29.411Z",
      "_updatedAt":"2015-12-01T00:31:29.411Z",
      "name":"Some Event",
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
      ]
   }
]
```


## Create Plan (Event)

### Request

```
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

## Create Plan (Location)

### Request

```
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

## Get plans

```
GET /plans HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache
```

###Response

```
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

## Get plans populating events and locations

```
GET /plans?populate[]=location&populate[]=event HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJuYW1lIjoiU2FudGlhZ28gQ290dG8iLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.Z7oZw6VqhYeICzgNxOUQk01ZomRk8yw0C42891p73QI
Cache-Control: no-cache
```

### Response

```
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

# Send deviceId

IOS and android deviceId/registerId -> Push Notification

## Request

```
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


# IceBrecker

## Get users in Current Hostel

### Request

```
GET /users/current-hostel HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache
```

### Response

```
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

## Get phrases

```
GET /phrases HTTP/1.1
Host: flipflop.dev.konabackend.com
```

### Response

```
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
## Send message


### Send phrase

```
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

```
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

```
POST /messages HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache

{  
   "to":"565f1a7af386ddd84bf764aa",
   "event":"565cfa8dc2e649e9dbb29894"
}
```

### Send location

```
POST /messages HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache

{  
   "to":"565f1a7af386ddd84bf764aa",
   "location":"565f3027f386ddd84bf764b4"
}
```

### Response

```
{
    "_id": "5660cc4031cee6f980b97f38",
    "_createdAt": "2015-12-03T23:12:00.706Z",
    "_updatedAt": "2015-12-03T23:12:00.706Z",
    ...
}
```

## Get my conversations

### Request

```
GET /conversations HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache

```

### Response

```
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


## Get one conversation

```
GET /conversations/5660cc1631cee6f980b97f36 HTTP/1.1
Host: flipflop.dev.konabackend.com
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1NjU2OTMzNDk1NGY3NTIxMjIzMWFkNDEiLCJlbWFpbCI6InNhbnRpYWdvQGtvbmFjbG91ZC5pbyIsIl9fdiI6MCwiYmlydGhQbGFjZSI6eyJuYW1lIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsImNvdW50cnlDb2RlIjoiVVkifSwicHJvZmlsZUltYWdlVXJsIjoiYnVja2V0LzU2NTY5NTlhZjY2MDE0N2UzNGQxYmE0ZSIsImJpcnRoZGF5IjoiMTk4OS0wNi0yMFQwMDowMDowMC4wMDBaIiwiY3VycmVudFBsYWNlIjoiTW9udGV2aWRlbywgVXJ1Z3VheSIsInN0YXR1cyI6IlZBQ0FUSU9OUyIsImN1cnJlbnRIb3N0ZWwiOiI1NjU2YjU0OWJlZTg4MjE4M2MxNzUwNzYiLCJmYXZvdXJpdGVSZWNvbW1lbmRlZCI6W10sImZhdm91cml0ZUV2ZW50cyI6W10sImludGVyZXN0cyI6WyI1NjU2NmViOWJlZTg4MjE4M2MxNzUwNzAiLCI1NjU2NmU4YmJlZTg4MjE4M2MxNzUwNmUiLCI1NjU2NmU1YmJlZTg4MjE4M2MxNzUwNjYiXSwiY291bnRyaWVzVmlzaXRlZCI6WyI1NjU2NjBlMWJlOTc0M2E5NDk4ZWRkNjMiXSwiY291bnRyaWVzVG9WaXNpdCI6WyI1NjU2NjBiOGJlOTc0M2E5NDk4ZWRkNjAiXSwiZGVzY3JpcHRpb24iOlsiU29tZSBkZXNjcmlwdGlvbiBhYm91dCBtZSJdLCJjdXJyZW50UG9zaXRpb24iOltdLCJwcm9maWxlUGhvdG9zIjpbXX0.nYIm186irwB1x2nYC8OzPDOr6JflzOiYle4X2x3WXR0
Cache-Control: no-cache
```

### Response

```
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
