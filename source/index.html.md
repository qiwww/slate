---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - java
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction
  Welcome to AG Mednet Judi Imaging and Form API. <br />
  You can use our API to access Judi Imaging Measurement API endpoints, which can save and get information on imaging measurements. <br />
  You can also use our API to access Judi Form API endpoints, which can get information about form questions and save form answers to our database.

We have language bindings in Java and shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```java
API = "/weasismeasurements"
// With Java, you need to pass the correct cookie in request property
URl url = new URL(WeasisMeasurements.url);
// Connect to the web service and read the response.
HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestProperty("Content-Type", "application/json");
conn.setRequestionMethod("GET");
// Add coolies to the request
conn.setRequestProperty("Cookie" , cookie);
conn.connect();
```

```shell
API = "/weasismeasurements"
# With shell, you can just pass the correct header with each request
curl "WeasisMeasurements.url"
  -H "Authorization: cookie"
```

> Make sure to replace `WeasisMeasurements.url` with correct URL path.

> Make sure to replace `cookie` with your API key.

AG Mednet uses cookie header to allow access to the API. You can register as an AG Mednet user at our [developer portal](https://demo01.agmednet.net).

We expect for the API key to be included in all API requests to the server in a header that looks like the following:

`iPlanetDirectoryPro="cookie key"`

<aside class="notice">
You must replace <code>cookie</code> / <code>cookie key</code> with your personal API key.
</aside>


# Measurement

## Create and Update Measurement Record

```java
API = "/weasismeasurements"
URl url = new URL(WeasisMeasurements.url);
// Connect to the web service and read the response.
HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestProperty("Content-Type", "application/json");
conn.setRequestionMethod("POST");
// Add coolies to the request
conn.setRequestProperty("Cookie" , cookie);
conn.connect();

// Construct a JSON object to String "json"

// Pass String "json" to connection
OutputStream os = conn.getOutputStream();
OutputStreamWriter osw = new OutputStreamWriter(os, "UTF-8");
osw.write(json);
```

```shell
API = "/weasismeasurements"

curl = "https://demo01.agmednet.net/api/weasismeasurements"
-H "Authorization:cookie"
```
> Make sure to replace `cookie` with your API key.

This endpoint creates or updates a measurement record in database: weasis_measurement table.

### HTTP Request
`POST https://example.com/weasismeasurements`


### Sample Call
`POST https://demo01.agmednet.net/api/weasismeasurements`


### Data Parameters

> An example of data object has JSON structured like this:

```json
  {
    "value": "<graphicList>\r\n  <rectangle handle_pts_nb=\"8\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"717242438\" form_question_name=\"anotherWeasisQuestion\" form_question=\"Another Weasis Question\">\r\n     <pts class=\"java.util.ArrayList\">\r\n        <pt x=\"363.0012162490878\" y=\"218.21624908781317\"\/>\r\n        <pt x=\"406.29968377523716\" y=\"223.56774507419118\"\/>\r\n        <pt x=\"406.29968377523716\" y=\"218.21624908781317\"\/>\r\n        <pt x=\"363.0012162490878\" y=\"223.56774507419118\"\/>\r\n        <pt x=\"384.6504500121625\" y=\"218.21624908781317\"\/>\r\n        <pt x=\"384.6504500121625\" y=\"223.56774507419118\"\/>\r\n        <pt x=\"406.29968377523716\" y=\"220.89199708100216\"\/>\r\n        <pt x=\"363.0012162490878\" y=\"220.89199708100216\"\/>\r\n     <\/pts>\r\n     <paint class=\"java.awt.Color\" rgb=\"ffff00\"\/>\r\n     <label offsetX=\"0.0\" offsetY=\"0.0\"\/>\r\n  <\/rectangle>\r\n  <line handle_pts_nb=\"2\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"717242438\" form_question_name=\"weasisLength\" form_question=\"Length of Something*\" form_answer=\"Length : 323.1 pix\">\r\n     <pts class=\"java.util.ArrayList\">\r\n        <pt x=\"157.69837022622232\" y=\"92.2128435903673\"\/>\r\n        <pt x=\"479.7611286791535\" y=\"118.48382388713208\"\/>\r\n     <\/pts>\r\n     <paint class=\"java.awt.Color\" rgb=\"ffff00\"\/>\r\n     <label offsetX=\"0.0\" offsetY=\"0.0\"\/>\r\n  <\/line>\r\n  <threePointsCircle handle_pts_nb=\"3\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"717242438\" form_question_name=\"weasisArea\" form_question=\"Area of something?\" form_answer=\"Area : 5,763.4 pix\">\r\n     <pts class=\"java.util.ArrayList\">\r\n        <pt x=\"148.9413767939674\" y=\"166.16078812940887\"\/>\r\n        <pt x=\"188.34784723911457\" y=\"230.378739965945\"\/>\r\n        <pt x=\"210.72683045487716\" y=\"222.5947458039406\"\/>\r\n     <\/pts>\r\n     <paint class=\"java.awt.Color\" rgb=\"ffff00\"\/>\r\n     <label offsetX=\"0.0\" offsetY=\"0.0\"\/>\r\n  <\/threePointsCircle>\r\n<\/graphicList>",
    "studyId": 734515440,
    "userAccountId": 717242438,
    "userRole": "Adjudicator"
  }
```

Parameter | type | Default | Description
--------- | ------ | ------- | -----------
value | text | N/A | measurement graphics in text format 
studyId | integer | N/A | study ID
userAccountId | integer | N/A | user account ID
userRole | text | N/A | user role's role name


<aside class="notice">
  Data is JSON structured.
</aside>



## Get a Specific Measurement Record by Rest ID

```java
API = "/weasismeasurements/{restId}"
URL url = new URL("https://demo01.agmednet.net/api/weasismeasurements/FBYVKDH4");
// Connect to the web service and read the response.
HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestProperty("Content-Type", "application/json");
conn.setRequestionMethod("GET");
// Add coolies to the request
conn.setRequestProperty("Cookie" , cookie);
conn.connect();
```

```shell
API = "/weasismeasurements/{restId}"

curl = "http://demo01.agmednet.net/api/weasismeasurements/FBYVKDH4"
-H "Authorization: cookie"
```

> Make sure to replace `cookie` with your API key.

This endpoint retrieves a specific measurement record in weasis_measurement table by rest Id.


### HTTP Request

`GET https://example.com/weasismeasurements/{restId}`

### Sample call
`Get https://demo01.agmednet.net/api/weasismeasurements/FBYVKDH4`


### URL Parameters

Parameter | Description
--------- | -----------
restId | The rest ID of the measurement record to retrieve


### Success Response Parameters

<aside class="success">
  returns weasis measurement object
</aside>

> An example of a return object has JSON structure as: 

```json
{
   "id": 62990033,
   "restId": "QB3Q8QDY",
   "value": "<graphicList>    <line handle_pts_nb=\"2\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"2041002\" user_role=\"reviewer\" form_question_name=\"cevaReviewer\" form_question=\"Length of Something*\" form_answer=\"Length : 195 mm\">       <pts class=\"java.util.ArrayList\">          <pt x=\"299.99421128798843\" y=\"189.14037626628075\"/>          <pt x=\"418.08393632416784\" y=\"34.00289435600579\"/>       </pts>       <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>       <label offsetX=\"0.0\" offsetY=\"0.0\"/>    </line>    <ellipse handle_pts_nb=\"8\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"2041002\" user_role=\"reviewer\" form_question_name=\"cevaComments\" form_question=\"Area of something?\" form_answer=\"Area : 17,447.3 mm2\">       <pts class=\"java.util.ArrayList\">          <pt x=\"169.16931982633864\" y=\"302.5991316931983\"/>          <pt x=\"320.2547033285094\" y=\"449.63241678726484\"/>          <pt x=\"320.2547033285094\" y=\"302.5991316931983\"/>          <pt x=\"169.16931982633864\" y=\"449.63241678726484\"/>          <pt x=\"244.712011577424\" y=\"302.5991316931983\"/>          <pt x=\"244.712011577424\" y=\"449.63241678726484\"/>          <pt x=\"320.2547033285094\" y=\"376.11577424023153\"/>          <pt x=\"169.16931982633864\" y=\"376.11577424023153\"/>       </pts>       <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>       <label offsetX=\"0.0\" offsetY=\"0.0\"/>    </ellipse> </graphicList>",
   "studyId": 59602037,
   "userAccountId": 2041002,
   "userFirstName": "Chair",
   "userLastName": "Man",
   "userRole": "reviewer",
   "invalidInput": null
}
```

Parameter | Type | Defualt | Description
--------- | ---- | ------- | -----------
id | integer | N/A | The ID of the measurement record
restId | text | N/A | The rest ID of the measurement record
value | text | N/A | The value of measurement 
studyId | integer | N/A | The ID of the study
userAccountId | integer | N/A | The ID of the user account
userFirstName | text | N/A | The first name of the user account
userLastName | text | N/A | The last name of the user account
userRole | text | N/A | The user role name of the current user
invalidInput | text | null | Invalid input


## Get a Specific Measurement Record by Study ID and User Role

```java
API = "weasismeasurements/study/{studyId}/userrole/{userRole}"

URL url = new URL("https://demo01.agmednet.net/api/weasismeasurements/study/756788442/userrole/committeeChair");
// Connect to the web service and read the response.
HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestProperty("Content-Type", "application/json");
conn.setRequestionMethod("GET");
// Add coolies to the request
conn.setRequestProperty("Cookie" , cookie);
conn.connect();
```

```shell
api = "weasismeasurements/study/{studyId}/userrole/{userRole}"

curl "https://demo01.agmednet.net/api/weasismeasurements/study/756788442/useraccount/718789438/userrole/committeeChair"
  -H "Authorization: cookie"
```



This endpoint retrieves a speicific measurement record by given study id and user role name, based on user account id in the system.

### HTTP Request

`GET http://example.com/weasismeasurements/study/{studyId}/userrole/{userRole}`

### Sample Call
`GET https://demo01.agmednet.net/api/weasismeasurements/study/756788442/userrole/committeeChair`

### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
studyId | integer | The ID of the study
userRole | text | The role name of the user role


### Success Response 

> An example of a return object has JSON structure as: 

```json
{
   "id": 62968033,
   "restId": "X08MVTY9",
   "value": "<graphicList>\n   <ellipse handle_pts_nb=\"8\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"2000\" user_role=\"reviewer\" form_question_name=\"cevaComments\" form_question=\"Area of something?\" form_answer=\"Area : 8,656 mm2\">\n      <pts class=\"java.util.ArrayList\">\n         <pt x=\"191.74529667149056\" y=\"352.96092619392186\"/>\n         <pt x=\"428.50361794500725\" y=\"435.739507959479\"/>\n         <pt x=\"428.50361794500725\" y=\"352.96092619392186\"/>\n         <pt x=\"191.74529667149056\" y=\"435.739507959479\"/>\n         <pt x=\"310.1244573082489\" y=\"352.96092619392186\"/>\n         <pt x=\"310.1244573082489\" y=\"435.739507959479\"/>\n         <pt x=\"428.50361794500725\" y=\"394.35021707670046\"/>\n         <pt x=\"191.74529667149056\" y=\"394.35021707670046\"/>\n      </pts>\n      <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>\n      <label offsetX=\"0.0\" offsetY=\"0.0\"/>\n   </ellipse>\n   <line handle_pts_nb=\"2\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"2000\" user_role=\"reviewer\" form_question_name=\"cevaReviewer\" form_question=\"Length of Something*\" form_answer=\"Length : 292.7 mm\">\n      <pts class=\"java.util.ArrayList\">\n         <pt x=\"206.21707670043412\" y=\"225.0303907380608\"/>\n         <pt x=\"452.2373371924747\" y=\"66.41968162083937\"/>\n      </pts>\n      <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>\n      <label offsetX=\"0.0\" offsetY=\"0.0\"/>\n   </line>\n</graphicList>",
   "studyId": 59602037,
   "userAccountId": 2000,
   "userFirstName": "The",
   "userLastName": "Reviewer",
   "userRole": "reviewer",
   "invalidInput": null
}
```

Parameter | Type | Defualt | Description
--------- | ---- | ------- | -----------
id | integer | N/A | The ID of the measurement record
restId | text | N/A | The rest ID of the measurement record
value | text | N/A | The value of measurement 
studyId | integer | N/A | The ID of the study
userAccountId | integer | N/A | The ID of the user account
userFirstName | text | N/A | The first name of the user account
userLastName | text | N/A | The last name of the user account
userRole | text | N/A | The user role name of the current user
invalidInput | text | null | Invalid input

## Get Measurement Records List by Study ID

```java
API = "weasismeasurements/study/{studyId}"

URL url = new URL("https://demo01.agmednet.net/api/weasismeasurements/study/756788442");
// Connect to the web service and read the response.
HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestProperty("Content-Type", "application/json");
conn.setRequestionMethod("GET");
// Add coolies to the request
conn.setRequestProperty("Cookie" , cookie);
conn.connect();
```

```shell
API = "weasismeasurements/study/{studyId}"

curl "https://demo01.agmednet.net/api/weasismeasurements/study/756788442"
  -H "Authorization: cookie"
```


This endpoint retrieves a list of measurement records by given study id.

### HTTP Request

`GET http://example.com/weasismeasurements/study/{studyId}`

### Sample Call

`GET https://demo01.agmednet.net/api/weasismeasurements/study/756788442`


### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
studyId | integer | The ID of the study


### Success Response:

<aside class="success">
  This API call retrives a list of weasis measurement objects. 
</aside>

Structure of weasis measurement object demonstrates below:  

> An example of a return obect has JSON structure as:

```json
[
    {
        "id": 62968033,
        "restId": "X08MVTY9",
        "value": "<graphicList>\n   <ellipse handle_pts_nb=\"8\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"2000\" user_role=\"reviewer\" form_question_name=\"cevaComments\" form_question=\"Area of something?\" form_answer=\"Area : 8,656 mm2\">\n      <pts class=\"java.util.ArrayList\">\n         <pt x=\"191.74529667149056\" y=\"352.96092619392186\"/>\n         <pt x=\"428.50361794500725\" y=\"435.739507959479\"/>\n         <pt x=\"428.50361794500725\" y=\"352.96092619392186\"/>\n         <pt x=\"191.74529667149056\" y=\"435.739507959479\"/>\n         <pt x=\"310.1244573082489\" y=\"352.96092619392186\"/>\n         <pt x=\"310.1244573082489\" y=\"435.739507959479\"/>\n         <pt x=\"428.50361794500725\" y=\"394.35021707670046\"/>\n         <pt x=\"191.74529667149056\" y=\"394.35021707670046\"/>\n      </pts>\n      <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>\n      <label offsetX=\"0.0\" offsetY=\"0.0\"/>\n   </ellipse>\n   <line handle_pts_nb=\"2\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"2000\" user_role=\"reviewer\" form_question_name=\"cevaReviewer\" form_question=\"Length of Something*\" form_answer=\"Length : 292.7 mm\">\n      <pts class=\"java.util.ArrayList\">\n         <pt x=\"206.21707670043412\" y=\"225.0303907380608\"/>\n         <pt x=\"452.2373371924747\" y=\"66.41968162083937\"/>\n      </pts>\n      <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>\n      <label offsetX=\"0.0\" offsetY=\"0.0\"/>\n   </line>\n</graphicList>",
        "studyId": 59602037,
        "userAccountId": 2000,
        "userFirstName": "The",
        "userLastName": "Reviewer",
        "userRole": "reviewer",
        "invalidInput": null
    },
    {
        "id": 63107033,
        "restId": "HZ4JX49G",
        "value": "<graphicList>\n   <line handle_pts_nb=\"2\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"2041002\" user_role=\"committeeChair\" form_question_name=\"cevaReviewer\" form_question=\"Length of Something*\" form_answer=\"Length : 5.3 mm\">\n      <pts class=\"java.util.ArrayList\">\n         <pt x=\"32.84515195369028\" y=\"310.1244573082489\"/>\n         <pt x=\"33.71345875542692\" y=\"304.91461649782923\"/>\n      </pts>\n      <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>\n      <label offsetX=\"0.0\" offsetY=\"0.0\"/>\n   </line>\n</graphicList>",
        "studyId": 59602037,
        "userAccountId": 2041002,
        "userFirstName": "Chair",
        "userLastName": "Man",
        "userRole": "committeeChair",
        "invalidInput": null
    },
    {
        "id": 61794033,
        "restId": "2M6YL16G",
        "value": "<graphicList>    <line handle_pts_nb=\"2\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"4000\" user_role=\"reviewer\" form_question_name=\"cevaReviewer\" form_question=\"Length of Something*\" form_answer=\"Length : 303.7 mm\">       <pts class=\"java.util.ArrayList\">          <pt x=\"112.43560057887117\" y=\"40.37047756874096\"/>          <pt x=\"433.13458755426916\" y=\"137.62083936324169\"/>       </pts>       <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>       <label offsetX=\"0.0\" offsetY=\"0.0\"/>    </line>    <rectangle handle_pts_nb=\"8\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"4000\" user_role=\"reviewer\" form_question_name=\"cevaComments\" form_question=\"Area of something?\" form_answer=\"Area : 15,238 mm2\">       <pts class=\"java.util.ArrayList\">          <pt x=\"183.06222865412445\" y=\"352.3820549927641\"/>          <pt x=\"348.61939218523884\" y=\"444.42257597684517\"/>          <pt x=\"348.61939218523884\" y=\"352.3820549927641\"/>          <pt x=\"183.06222865412445\" y=\"444.42257597684517\"/>          <pt x=\"265.84081041968165\" y=\"352.3820549927641\"/>          <pt x=\"265.84081041968165\" y=\"444.42257597684517\"/>          <pt x=\"348.61939218523884\" y=\"398.4023154848046\"/>          <pt x=\"183.06222865412445\" y=\"398.4023154848046\"/>       </pts>       <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>       <label offsetX=\"0.0\" offsetY=\"0.0\"/>    </rectangle> </graphicList>",
        "studyId": 59602037,
        "userAccountId": 4000,
        "userFirstName": "Adjudicator",
        "userLastName": "One",
        "userRole": "reviewer",
        "invalidInput": null
    },
    {
        "id": 62512033,
        "restId": "DW77S8FZ",
        "value": "<graphicList>    <line handle_pts_nb=\"2\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"5000\" user_role=\"reviewer\" form_question_name=\"cevaReviewer\" form_question=\"Length of Something*\" form_answer=\"Length : 411 mm\">       <pts class=\"java.util.ArrayList\">          <pt x=\"63.814761215629495\" y=\"18.952243125904488\"/>          <pt x=\"459.18379160636755\" y=\"131.2532561505065\"/>       </pts>       <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>       <label offsetX=\"0.0\" offsetY=\"0.0\"/>    </line>    <rectangle handle_pts_nb=\"8\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"5000\" user_role=\"reviewer\" form_question_name=\"cevaComments\" form_question=\"Area of something?\" form_answer=\"Area : 1,574.9 mm2\">       <pts class=\"java.util.ArrayList\">          <pt x=\"245.00144717800285\" y=\"367.4327062228654\"/>          <pt x=\"273.94500723589005\" y=\"421.84659913169315\"/>          <pt x=\"273.94500723589005\" y=\"367.4327062228654\"/>          <pt x=\"245.00144717800285\" y=\"421.84659913169315\"/>          <pt x=\"259.47322720694643\" y=\"367.4327062228654\"/>          <pt x=\"259.47322720694643\" y=\"421.84659913169315\"/>          <pt x=\"273.94500723589005\" y=\"394.6396526772793\"/>          <pt x=\"245.00144717800285\" y=\"394.6396526772793\"/>       </pts>       <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>       <label offsetX=\"0.0\" offsetY=\"0.0\"/>    </rectangle> </graphicList>",
        "studyId": 59602037,
        "userAccountId": 5000,
        "userFirstName": "Adjudicator",
        "userLastName": "Two",
        "userRole": "reviewer",
        "invalidInput": null
    },
    {
        "id": 62990033,
        "restId": "QB3Q8QDY",
        "value": "<graphicList>    <line handle_pts_nb=\"2\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"2041002\" user_role=\"reviewer\" form_question_name=\"cevaReviewer\" form_question=\"Length of Something*\" form_answer=\"Length : 195 mm\">       <pts class=\"java.util.ArrayList\">          <pt x=\"299.99421128798843\" y=\"189.14037626628075\"/>          <pt x=\"418.08393632416784\" y=\"34.00289435600579\"/>       </pts>       <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>       <label offsetX=\"0.0\" offsetY=\"0.0\"/>    </line>    <ellipse handle_pts_nb=\"8\" thickness=\"1.0\" fill=\"false\" label_visible=\"true\" class_id=\"0\" user_id=\"2041002\" user_role=\"reviewer\" form_question_name=\"cevaComments\" form_question=\"Area of something?\" form_answer=\"Area : 17,447.3 mm2\">       <pts class=\"java.util.ArrayList\">          <pt x=\"169.16931982633864\" y=\"302.5991316931983\"/>          <pt x=\"320.2547033285094\" y=\"449.63241678726484\"/>          <pt x=\"320.2547033285094\" y=\"302.5991316931983\"/>          <pt x=\"169.16931982633864\" y=\"449.63241678726484\"/>          <pt x=\"244.712011577424\" y=\"302.5991316931983\"/>          <pt x=\"244.712011577424\" y=\"449.63241678726484\"/>          <pt x=\"320.2547033285094\" y=\"376.11577424023153\"/>          <pt x=\"169.16931982633864\" y=\"376.11577424023153\"/>       </pts>       <paint class=\"java.awt.Color\" rgb=\"ffff00\"/>       <label offsetX=\"0.0\" offsetY=\"0.0\"/>    </ellipse> </graphicList>",
        "studyId": 59602037,
        "userAccountId": 2041002,
        "userFirstName": "Chair",
        "userLastName": "Man",
        "userRole": "reviewer",
        "invalidInput": null
    }
]

```


Parameter | Type | Default | Description 
--------- | ---- | ------- | ------------
id | integer | N/A | The ID of the measurement record
restId | text | N/A | The rest ID of the measurement record
value | text | N/A | The value of measurement 
studyId | integer | N/A | The ID of the study
userAccountId | integer | N/A | The ID of the user account
userFirstName | text | N/A | The first name of the user account
userLastName | text | N/A | The last name of the user account
userRole | text | N/A | The user role name of the current user
invalidInput | text | null | Invalid input

## Get if A User Is Weasis Privilege User

```java
API = "weasismeasurements/study/{studyId}"

URL url = new URL("https://demo01.agmednet.net/api/weasismeasurements/study/756788442");
// Connect to the web service and read the response.
HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestProperty("Content-Type", "application/json");
conn.setRequestionMethod("GET");
// Add coolies to the request
conn.setRequestProperty("Cookie" , cookie);
conn.connect();
```

```shell
api = "weasismeasurements/userrole/{userRole}/eventinstance/{eventInstanceRestId}/userstatues"

curl "https://demo01.agmednet.net/api/weasismeasurements/userrole/committeeChair/eventinstance/1Q45G9KL/userstatues"
  -H "Authorization: cookie"
```


> The above command returns JSON structured like this:

```json
true
```

This endpoint retrieves the value of true or false if a user has permission to view all related measurements by given user role and event instance rest id. 

### HTTP Request

`GET http://example.com/api/weasismeasurements/userrole/{userRole}/eventinstance/{eventInstanceRestId}/userstatue`

### Sample Call

`GET https://demo01.agmednet.net/api/weasismeasurements/userrole/committeeChair/eventinstance/1Q45G9KL/userstatues`

### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
userRole | text | The user role name of the user
eventInstanceRestId | text | The rest ID of the event instance

### Success Response:

Parameter | Type | Default | Description
--------- | ---- | ------- | ------------
privilegeUser | text | false | If the user has permission to view all related measurements 

## Get if A User Is Weasis user

```java
API = "weasismeasurements/userrole/{userRole}/eventinstance/{eventInstanceRestId/weasisuser"

URL url = new URL("https://demo01.agmednet.net/api/weasismeasurements/userrole/committeeChair/eventinstance/1Q45G9KL/weasisuser");
// Connect to the web service and read the response.
HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestProperty("Content-Type", "application/json");
conn.setRequestionMethod("GET");
// Add coolies to the request
conn.setRequestProperty("Cookie" , cookie);
conn.connect();
```

```shell
api = "weasismeasurements/userrole/{userRole}/eventinstance/{eventInstanceRestId}/weasisuser"

curl "https://demo01.agmednet.net/api/weasismeasurements/userrole/committeeChair/eventinstance/1Q45G9KL/weasisuser"
  -H "Authorization: cookie"
```


> The above command returns JSON structured like this:

```json
true 
```

This endpoint retrieves the value of true or false if a user has permission to make measurements by given user role and event instance rest id.

### HTTP Request

`GET http://example.com/api/weasismeasurements/userrole/{userRole}/eventinstance/{eventInstanceRestId}/weasisuser`

### Sample Call

`GET https://demo01.agmednet.net/api/weasismeasurements/userrole/committeeChair/eventinstance/1Q45G9KL/weasisuser`

### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
userRole | text | The user role name of the user
eventInstanceRestId | text | The rest ID of the event instance

### Success Response:

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
weasisUser | text | false | If the user has permission to make measurements



# Form

## Get Weasis Related Form Questions 

```java
API = "weasismeasurements/userrole/{userRole}/eventinstance/{eventInstanceRestId/weasisuser"

URL url = new URL("https://demo01.agmednet.net/api/weasismeasurements/userrole/committeeChair/eventinstance/1Q45G9KL/weasisuser");
// Connect to the web service and read the response.
HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestProperty("Content-Type", "application/json");
conn.setRequestionMethod("GET");
// Add coolies to the request
conn.setRequestProperty("Cookie" , cookie);
conn.connect();
```

```shell
api = "weasismeasurements/eventinstance/{eventInstanceRestId}/userrole/{userRole}"

curl "https://demo01.agmednet.net/api/weasismeasurements/eventinstance/1Q45G9KL/userrole/committeeChair"
  -H "Authorization: cookie"
```


> The above command returns JSON structured like this:

```json
{
   "formId": 59621033,
   "nameQuestionOrNameAnswerMap": {
       "cevaComments": "Area of something?",
       "cevaReviewer": "Length of Something*"
   },
   "phase": 1,
   "invalidInput": null
}
```

This endpoint retrieves a list of form questions required Weasis to answer by given event instance rest id and user role. 

### HTTP Request

`GET http://example.com/api/weasismeasurements/eventinstance/{eventInstanceRestId}/userrole/{userRole}`

### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
eventInstanceRestId| text | The rest ID of the event instance
userRole | text | The role name of the user role


### Success Response 

Parameter | Type | Defualt | Description
--------- | ---- | ------- | -----------
formId | ingeter | N/A | The ID of form related to the event instance and user role
nameQuestionMap | Map<text, text> | N/A | The map between question name and question value
phase | integer | 0 | The phase of the form
invalidInput | text | null | Invalid input

<aside class="notice">
  Form question name is unique. You could consider it as ID.
</aside>


## Create and Update Form Question Result

```java
API = "weasismeasurements/userrole/{userrole}/eventinstance/{eventInstanceRestId}"

URL url = new URL("https://demo01.agmednet.net/api/weasismeasurements/userrole/committeeChair/eventinstance/1Q45G9KL");
// Connect to the web service and read the response.
HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestProperty("Content-Type", "application/json");
conn.setRequestionMethod("POST");
// Add coolies to the request
conn.setRequestProperty("Cookie" , cookie);
conn.connect();
```

```shell
api = "weasismeasurements/userrole/{userRole}/eventinstance/{eventInstanceRestId}"

curl "https://demo01.agmednet.net/api/weasismeasurements/userrole/committeeChaireventinstance/1Q45G9KL/userrole/committeeChair"
  -H "Authorization: cookie"
```


This endpoint creats or updates form question result by given user account id, user role and event instance rest id.

### HTTP Request

`POST http://example.com/api/weasismeasurements/userrole/{userRole}eventinstance/{eventInstanceRestId}`

### Sample Call

`POST https://demo01.agmednet.net/api/weasismeasurements/userrole/committeeChair/eventinstance/1Q45G9KL`


### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
eventInstanceRestId| text | The rest ID of the event instance
userRole | text | The role name of the user role
eventInstanceRestId | text | The rest ID of the event instacne


### Data Parameters

> An example of data object has JSON structure as:

```json
{
   "formId": 59621033,
   "nameQuestionOrNameAnswerMap": {
       "cevaComments": "Area: 1,547.7 mm2",
       "cevaReviewer": "Length: 72.2 mm"
   },
   "phase": 1,
   "invalidInput": null
}
ss
```

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
formId| integer | N/A | The ID of the form
nameQuestionOrNameAnswerMap | Map<text, text> | N/A | The map between form question name and form question answer
phase | integer | 0 | The pase of the form
invalidInput | text | null | Invalid input 



<aside class="notice">
  Form question name is unique. You could consider it as ID.
</aside>

