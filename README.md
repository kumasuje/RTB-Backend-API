# Back-End


REST API LIST


### End Point to POST a new user infomration (during sign UP)


Method Type : ``` POST```

```

https://raisethebar00.herokuapp.com/signUp

## Request Body in JSON Format

Name                 | Type               | Description                                            
------------         | -----------        | ----------------------------------------------------   
emailId              | String             | Email ID of user returned from FB
fullName             | String             | Full name of user - might split this field into first name last name in future 
fbUserId             | String             | FB returened User ID    
profilePic           | String             | link to the pic returned by FB                     
gender               | String             | male or female.


Mandatory Header details - 
Accept : appplication/json
Content-Type : appplication/json

```
Example - 
```
https://raisethebar00.herokuapp.com/signUp

sample request body will look like this.
{
    "emailId":"alex@iu.edu",
    "fullName":" Alex Sign",
    "fbUserId":"1461302307",
    "profilePic":"https://scontent.xx.fbcdn.net/v/t1.0-1/p50x50/10308368_10152022362232307_6238714654193480617_n.jpg?oh=51310c2327239d49076d9300c0d47b26&oe=59102909",
    "gender":"male"
}

```


Response - 
```
Status: 200 OK with newly register UserModel with all the field. 

for example - a successful resposne would look like this

{
    "userId": 9,
    "emailId": "alex@iu.edu",
    "fbUserId": "1461302307",
    "profilePic": "https://scontent.xx.fbcdn.net/v/t1.0-1/p50x50/10308368_10152022362232307_6238714654193480617_n.jpg?oh=51310c2327239d49076d9300c0d47b26&oe=59102909",
    "fullName": " Alex Sign",
    "gender": "male"
}
 ``` 
Status: 400 BAD Request with header field called error having error information.


### End point to get the list of bars. 

This endpoint gives two type of response as below 
```
1 > HTTP Response OK (200) with Json foramatted data about near by Bars in the Body. 

2 > HTTP Response Bad Request (400) with error message in header with tag error and value as "unregister user" and null body.
```
Method Type : ``` GET```

```

https://raisethebar00.herokuapp.com/bar/barsList

## Parameters

Name                 | Type               | Description                                            |
------------         | -----------        | ----------------------------------------------------   |
latitude             | String             | lattitude of location captured in the app              |
longitude            | String             | longitude of location captured in the app              |
emailid              | String             | User email id recived from facebook                     

Accept : appplication/json

```
Example - 
```
https://raisethebar00.herokuapp.com/home/barsList?latitude=39.168232&longitude=-86.533849&emailid=alex@ui.edu
```

Sucessfull Response - 
```
Status: 200 OK

[
    {
        "barId": 18,
        "ownerId": 7,
        "description": null,
        "dayOFWeek": 1,
        "name": "Kilroy's Bar & Grill",
        "address": "502 E Kirkwood Ave Bloomington, IN 47408",
        "latitude": 39.166307,
        "longitude": -86.528031,
        "phoneNumber": "(812) 339-3007",
        "barPicture": "https://raisethebarllc18.s3.amazonaws.com/c6b7efeb-01f5-42b4-a0f9-0c264a82e8db",
        "amOpenTime": "00:00:00",
        "amCloseTime": "00:00:00",
        "pmOpenTime": "00:00:00",
        "pmCloseTime": "00:00:00",
        "barLogo": "https://raisethebarllc18.s3.amazonaws.com/248ff151-5561-443b-857e-e1c468a7f16c"
    },
    {
        "barId": 19,
        "ownerId": 7,
        "description": "Outpost of a Midwestern sports-bar chain serving casual American eats in a party atmosphere.",
        "dayOFWeek": 1,
        "name": "Brother's Bar & Grill",
        "address": "215 N Walnut St Bloomington, IN 47404",
        "latitude": 39.168232,
        "longitude": -86.533849,
        "phoneNumber": "(812) 331-1000",
        "barPicture": "https://raisethebarllc19.s3.amazonaws.com/26094965-c629-4996-a6d3-7865055ff281",
        "amOpenTime": "00:00:00",
        "amCloseTime": "00:00:00",
        "pmOpenTime": "00:00:00",
        "pmCloseTime": "00:00:00",
        "barLogo": "https://raisethebarllc19.s3.amazonaws.com/130e2f7f-7bc4-4b1f-8463-1e00a19cb88e"
    }
]
```


### End point to get Special of a bars.

```https://raisethebar00.herokuapp.com/bar/barDetails/<BarId>/<DayOfWeek>```

This end point will give you details of a specific bar on a day of week in a list.

## Parameters
```
Name                 | Type               | Description                                            |
------------         | -----------        | ----------------------------------------------------   |
BarId                | Integer            | Bar Id                   
DayOfWeek            | Integer            | Day of Week ( 1 for Monday, 2 for Tuesday and so on till 7 for sunday)

Accept : appplication/json

```

Example - 
```
https://raisethebar00.herokuapp.com/bar/barDetails/18/1
```

Sucessfull Response - 
```
Status: 200 OK

[
    {
        "itemId": 8,
        "barId": 18,
        "name": "$1 Sliders",
        "price": 1,
        "quantity": "0",
        "dayOfWeek": 1,
        "tillTime": "00:00:00",
        "validFrom": null
    },
    {
        "itemId": 10,
        "barId": 18,
        "name": "$4 Long Islands",
        "price": 4,
        "quantity": "0",
        "dayOfWeek": 1,
        "tillTime": "00:00:00",
        "validFrom": null
    },
    {
        "itemId": 9,
        "barId": 18,
        "name": "$1 Well",
        "price": 1,
        "quantity": "0",
        "dayOfWeek": 1,
        "tillTime": "00:00:00",
        "validFrom": null
    },
    {
        "itemId": 11,
        "barId": 18,
        "name": "Domestic Pitchers",
        "price": 5,
        "quantity": "32oz",
        "dayOfWeek": 1,
        "tillTime": "00:00:00",
        "validFrom": "00:00:00"
    }
]
```
