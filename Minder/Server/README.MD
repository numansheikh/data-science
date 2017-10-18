# Minder Predcition Server

Minder-prediction-server.0.1.0
==============================

Launching the server is simple
>> python server.py

The server will be launched by default on port 5000 of localhost.

Explanation of data:
+ No empty value
+ An empty numeric value should be replaced by NaN (case sensitive)
+ An Empty string should be ""
+ Ethnicity has too many extra quotation marks.
+ Boolean TRUE should be spelled as true
+ Boolean FALSE should be spelled as false

Structure
=========
+ Data is array of three elements
[p1_religion,
    [p1_data],
    [
        [p2_data],
        [p2_data],
           ... ,
        [p2_data]
    ]
]

Each DataRecord is an array of values given by the order of cols variable below

'p1_gender' str

'p1_data' is an array with following order
[
'p1_id' int
'p1_age' float
'p1_religiosity' float
'p1_country' str
'p1_education' str
'p1_flavour' str
'p1_language' str{...}
'p1_ethnicity' str{...}
'p1_premium' True/False
]

similarly each p2 data element has the same order
[
'p2_id' int
'p2_age' float
'p2_religiosity' float
'p2_country' str
'p2_education' str
'p2_flavour' str
'p2_language' str{...}
'p2_ethnicity' str{...}
'p2_premium' True/False
]

Request:
--------
Content-Type: application/json
URL: http://localhost:5000/api/predict
mrthod= POST

Sample JSON request data:
-----Begin Next Line-----------------
[
    "female",
    [266475,26,1.586520836,"US","graduate_degree","sunni","{Bengali}","{South Asian}",false],
    [
        [213638,NaN,NaN,"US","graduate_degree",NaN,NaN,NaN,false],
        [276866,28,NaN,"US","college_degree","sunni",NaN,NaN,false],
        [176010,28,1.932604847,"US","graduate_degree","other","{English,Arabic}","{Arab (Levant)}",false],
        [240383,29,NaN,"CA","college_degree","sunni","{Arabic,English}","{Arab (North Africa),Caucasian}",false],
        [145756,28,2,"US","graduate_degree","just_muslim","{English,Hindi,Urdu}","{South Asian}",false],
        [277169,31,NaN,"US","graduate_degree","just_muslim","{English,Urdu,Hindi}","{Other}",false],
        [22419,29,3.242074966,"US","other","just_muslim","{English,Turkish}","{Turkish}",false],
        [147738,26,NaN,"US","graduate_degree","just_muslim","{Urdu,English}","{Other}",false],
        [114554,30,4,"US","graduate_degree","just_muslim","{English}","{West African}",false],
        [143898,50,1.466302257,"US","graduate_degree","just_muslim","{English,Urdu}","{South Asian}",false],
        [207401,33,2.425076453,"US","undergraduate","just_muslim","{English,Urdu}","{South Asian}",true],
        [152951,30,2.249557886,"CA","graduate_degree","sunni","{English,Urdu}","{South Asian}",false],
        [57253,29,4,"CA","graduate_degree","shia","{English,Urdu,Pashtu}","{South Asian}",false],
        [157805,29,3.29969419,"US","undergraduate","sunni","{Urdu}","{South Asian}",false],
        [204057,28,1,"US","college_degree","other","{Urdu}","{East Asian}",false],
        [124846,28,1,"US","college_degree","just_muslim","{Arabic,English}","{Arab (North Africa)}",false],
        [72723,28,2.935897436,"US","college_degree","just_muslim","{English,Pashtu,Urdu}","{Afghan}",false],
        [150773,33,2.976131583,"CA","college_degree","sunni","{English,Urdu,Pashtu,Hindi}","{Other}",false],
        [277355,33,2.49235474,"CA","undergraduate","sunni","{Urdu,English}","{Other}",false],
        [114655,30,NaN,"US","college_degree",NaN,NaN,NaN,false]
    ]
]
-----End Above Line-----------------


Response:
---------
Content-Type: text/html; charset=utf-8
data:
-----Begin Next Line-----------------
[[213638, 276866, 176010, 240383, 145756, 277169, 22419, 147738, 114554, 143898, 207401, 152951, 57253, 157805, 204057, 124846, 72723, 150773, 277355, 114655], [0.021337379793967676, 0.03981980900795497, 0.11453240517649306, 0.0027210884353741495, 0.07339687408705813, 0.1, 0.004675675675675676, 0.17941176470588233, 0.0, 0.13333333333333333, 0.004021739130434783, 0.35, 0.0, 0.4340217391304348, 0.0, 0.005994922798720268, 0.06666666666666667, 0.0, 0.0, 0.03606490401700726]]
-----End Above Line-----------------
