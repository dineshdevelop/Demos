### EDVANTUM APP


### LOGIN – POST
URL -:  http://66.235.194.119:8089/api/auth/login
    {
        mobile:'88988086334',
        password:’123456’
    }
	
Response ->
`{
    "success": true,
    "data": {
        "userId": "6149c849d7948f1ca605d7c8",
        "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjYxNDljODQ5ZDc5NDhmMWNhNjA1ZDdjOCIsInVzZXJuYW1lIjoiODg5ODgwODYzMzQiLCJyb2xlIjoic2Nob29sQWRtaW4iLCJpYXQiOjE2MzIyMjUzODMsImV4cCI6MTYzMjU4NTM4M30.-IqkUF_aGogkJoLwQVUvUojJg51d2D0Bkk8M1QjFVJA",
        "role": "schoolAdmin",
        "email": "dineshsharma.developer+90@gmail.com",
        "firstName": "School",
        "lastName": "Admin",
        "mobile": "88988086334",
        "schools": [
            {
                "_id": "613edccce6f2770619bc2988",
                "schoolName": "kids school",
                "databaseName": "kids_school"
            },
            {
                "_id": "6149bbe15064741cd6c75805",
                "schoolName": "test school",
                "databaseName": "testdb"
            }
        ]
    }
}
`

NOTE: This <b>accessToken</b> needs to be passed with all the functions below in the <b>request authorization header</b>  
Also if using Postman, please make sure to pass the contenttype as "json".

============================================================================================

### STUDENT ATTENDANCE CLASS VISE: GET

URL: http://66.235.194.119:8089/api/studentattendance/getstudentattendancebyclass
`HEADERS: {
schoolId:'613edccce6f2770619bc2988'
}`

PARAMS: - {
 date:'07-07-2018'
}

Response ->
`{
    "success": true,
    "data": [
        {
            "classId": "6139fc0b048dbae46b81ec07",
            "className": "I",
            "section": "A",
            "totalStudents": 2,
            "presentStudent": 1,
            "dateOfAttendance": "07-07-2018"
        },
        {
            "classId": "6139fc41048dbae46b81ec08",
            "className": "II",
            "section": "A",
            "totalStudents": 1,
            "presentStudent": 0,
            "dateOfAttendance": "07-07-2018"
        }
    ]
}`
=====================================================================================

### TOTAL STUDENT OF SCHOOL & PRESENT STUDENT COUNT: GET

URL: http://66.235.194.119:8089/api/studentattendance/getschooltotalattendancecount
`HEADERS: {
schoolId:'613edccce6f2770619bc2988'
}`

PARAMS: - {
 date:'07-07-2018'
}


Response ->

`{
    "success": true,
    "data": {
        "totalStudents": 2,
        "presentStudents": 1
    }
}`






===========================================================================

### For single Class students Count :GET
URL: http://66.235.194.119:8089/api/studentattendance/getclassattendacetotalcount

`HEADERS: {
schoolId:'613edccce6f2770619bc2988',
}
`



PARAMS: - {
date:'07-07-2018',
classId:"6139fc0b048dbae46b81ec07"
}

Response ->
`{
    "success": true,
    "data": [
        {
            "classId": "6139fc0b048dbae46b81ec07",
            "className": "I",
            "section": "A",
            "totalStudents": 2,
            "presentStudent": 1,
            "dateOfAttendance": "07-07-2018",
            "teacherName": "teacher A sharma"
        }
    ]
}`

===============================================================
### For Each student attendance status: GET
URL: http://66.235.194.119:8089/api/studentattendance/getlistofstudentsattendance

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
date:'08-07-2018',
classId:"6139fc0b048dbae46b81ec07"
}

Response ->
`{
    "success": true,
    "data": [
        {
            "classId": "6139fc0b048dbae46b81ec07",
            "dateOfAttendance": "08-07-2018",
            "students": [
                {
                    "_id": "6139fb00048dbae46b81ec04",
                    "firstName": "Dinesh",
                    "lastName": "sharma",
                    "statusOfAttendance": "Leave"
                },
                {
                    "_id": "6139fb38048dbae46b81ec05",
                    "firstName": "happy",
                    "lastName": "sharma",
                    "statusOfAttendance": "Absent"
                }
            ]
        }
    ]
}
`
==============================================================================================

### For single Student attendance status:GET
URL:http://66.235.194.119:8089/api/studentattendance/getstudentattandace?studentId=6139fb00048dbae46b81ec04

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
 studentId:'6139fb00048dbae46b81ec04'
}


Response ->
`{
    "success": true,
    "data": [
        {
            "_id": "613f7f7529cff6b3bcbda331",
            "dateOfAttendance": "08-07-2018",
            "statusOfAttendance": "Leave",
            "firstName": "Dinesh",
            "lastName": "sharma",
            "studentId": "6139fb00048dbae46b81ec04"
        },
        {
            "_id": "613f803b29cff6b3bcbda332",
            "dateOfAttendance": "06-07-2018",
            "statusOfAttendance": "Absent",
            "firstName": "Dinesh",
            "lastName": "sharma",
            "studentId": "6139fb00048dbae46b81ec04"
        },
        {
            "_id": "613f807029cff6b3bcbda333",
            "dateOfAttendance": "05-07-2018",
            "statusOfAttendance": "Present",
            "firstName": "Dinesh",
            "lastName": "sharma",
            "studentId": "6139fb00048dbae46b81ec04"
        }
    ]
}`
============================================================================

### Get teacher attendance count : GET
URL :http://66.235.194.119:8089/api/staffattendance/getstaffattendancecount

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
 date:'07-07-2018'
}

Response ->
`{
    "success": true,
    "data": {
        "presentTeachers": 1,
        "totalTeachers": 3
    }
}
`
=============================================================================
### Get all teachers attendaces : GET
URL :http://66.235.194.119:8089/api/staffattendance/getstaffattendancedetails

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
 date:'07-07-2018',
 role:'teacher'
}

Response ->
`
{
    "success": true,
    "data": [
        {
            "statusOfAttendance": "OnTime",
            "firstName": "teacher A",
            "lastName": "sharma",
            "userId": "6139fa55048dbae46b81ec03"
        },
        {
            "statusOfAttendance": "Leave",
            "firstName": "teacher b",
            "lastName": "sharma",
            "userId": "6147fd0f2b0cdfba428df687"
        },
        {
            "statusOfAttendance": "Absent",
            "firstName": "teacher c",
            "lastName": "sharma",
            "userId": "6147fd2e2b0cdfba428df688"
        }
    ]
}`

=============================================================================

### Get Single teacher attendace status : GET
URL :http://66.235.194.119:8089/api/staffattendance/getstaffattendancedetail

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
 userId:'6139fa55048dbae46b81ec03'
}

Response ->
`{
    "success": true,
    "data": {
        "firstName": "teacher A",
        "lastName": "sharma",
        "attendances": [
            {
                "_id": "6147fc8e2b0cdfba428df686",
                "staffId": "6139fa55048dbae46b81ec03",
                "dateAttendance": "07-07-2018",
                "timeIn": "8:00 Am",
                "photoUrl": "https://web.skype.com/",
                "longitude": "67.0",
                "latitude": "80.9",
                "statusOfAttendance": "OnTime"
            }
        ]
    }
}`

=========================================================================================


### Apply Leave's : POST
URL :http://66.235.194.119:8089/api/staffleave/applyleave

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

`body:{
    dateFrom:"04-07-2019"
    dateTo:"05-07-2019"
    timeFrom:"17:30"
    timeTo:"17:30"
    comment:"i want a leave for urgent work"
    leaveType:"fullDay"
    listOfReasons:"casual"
    staffId:"613845fc635d2596d6f5acfa"
}`

Response ->
`{
    "success": true,
    "data": {
        "leaveFrom": {
            "timeTo": null,
            "date": "2019-04-07T05:00:00.000Z",
            "timeFrom": "17:30"
        },
        "halfDay": null,
        "statusOfLeave": "Pending",
        "_id": "616eac8b9031d96d6c7662ce",
        "comment": "i want a leave for urgent work",
        "leaveType": "fullDay",
        "listOfReasons": "casual",
        "staffId": "613845fc635d2596d6f5acfa",
        "leaveTo": {
            "date": "2019-05-07T05:00:00.000Z",
            "timeTo": "17:30"
        },
        "createdAt": "2021-10-19T11:31:23.198Z",
        "updatedAt": "2021-10-19T11:31:23.198Z",
        "__v": 0
    }
}
`

### for shortDay leave as same apply leave request

body:`dateFrom:05-07-2019
timeFrom:17:30
timeTo:19:30
comment:i want a leave for urgent work
leaveType:shortDay
listOfReasons:short
staffId:613845fc635d2596d6f5acfa`

Response:->`
{
    "success": true,
    "data": {
        "leaveFrom": {
            "timeTo": "19:30",
            "timeFrom": "17:30"
        },
        "halfDay": null,
        "statusOfLeave": "Pending",
        "_id": "616ead759031d96d6c766305",
        "comment": "i want a leave for urgent work",
        "leaveType": "shortDay",
        "listOfReasons": "short",
        "staffId": "613845fc635d2596d6f5acfa",
        "createdAt": "2021-10-19T11:35:17.731Z",
        "updatedAt": "2021-10-19T11:35:17.731Z",
        "__v": 0
    }
}`

### for HalfDay leave as same apply leave request
body:`
datefrom:09-07-2019
comment:i want a leave for urgent work
leaveType:halfDay
listOfReasons:short
staffId:613845fc635d2596d6f5acfa
halfDay:firstHalf`

Response:->`
{
    "success": true,
    "data": {
        "leaveFrom": {
            "timeTo": null
        },
        "halfDay": "firstHalf",
        "statusOfLeave": "Pending",
        "_id": "616eaeaa9031d96d6c76630e",
        "comment": "i want a leave for urgent work",
        "leaveType": "halfDay",
        "listOfReasons": "short",
        "staffId": "613845fc635d2596d6f5acfa",
        "createdAt": "2021-10-19T11:40:26.226Z",
        "updatedAt": "2021-10-19T11:40:26.226Z",
        "__v": 0
    }
}`


### GET all staff leaves requests : GET
URL :http://66.235.194.119:8089/api/staffleave/leavesrequest

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
}

Response ->
`{
    "success": true,
    "data": [
        {
            "_id": "614bf10e77d1632dc0943b34",
            "statusOfLeave": "Panding",
            "leaveType": "casual",
            "staffId": "6139fa55048dbae46b81ec03",
            "createdAt": "2021-09-23T03:14:22.595Z",
            "updatedAt": "2021-09-29T03:35:31.223Z",
            "leaveFrom": "27-09-2021",
            "leaveTo": "26-09-2021",
            "classes": [
                {
                    "className": "I",
                    "section": "A",
                    "classTeacherUserId": "6139fa55048dbae46b81ec03"
                }
            ],
            "firstName": "teacher A",
            "lastName": "sharma",
            "role": "teacher",
            "imageUrl":""
        }
    ]
}
`


### Approve or Reject the staff leaves requests : POST

URL :http://66.235.194.119:8089/api/staffleave/updateleavestatus

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

BODY:{
    staffId:'6139fa55048dbae46b81ec03',
    statusOfLeave:'Approve' // there is three status "Panding","Approve","Reject"
}

Response:`{
    "success": true,
    "msg": "Rcord updated successfully"
}`


### Create Group -POST

URL :http://66.235.194.119:8089/api/communication/creategroup

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

BODY:{
"groupName":"east 76 test group",
"groupImage":"http://66.235.194.119:8089",
"groupUserIds":["61724b4be8511e02efcb11d4","61724b4be8511e02efcb11d4"]
},

Response:`{
    "success": true,
    "msg": "Record inserted successfully",
    "data": {
        "groupUserIds": [
            "61724b4be8511e02efcb11d4",
            "61724b4be8511e02efcb11d4"
        ],
        "_id": "6172a4f50a409d68b8a09b54",
        "groupName": "\"east 76 test group\",",
        "groupImage": "\"http://66.235.194.119:8089\",",
        "createdAt": "2021-10-22T11:48:05.538Z",
        "updatedAt": "2021-10-22T11:48:05.538Z",
        "__v": 0
    }
}`


### Upload Group profile pics & message images

URL :http://66.235.194.119:8089/api/communication

BODY:{
file:(binary)
},

Response:`{"success":true,"msg":"File uploaded!","fileUrl":"http://66.235.194.119:8089/communication/1633338113127-imgpsh_fullsize_anim (1).jpg"}`


### Get all Groups -: GET

URL :http://66.235.194.119:8089/api/communication/groups

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

Response:->`
{
    "success": true,
    "data": [
        {
            "_id": "615aa0c9eb3ab064986bd8b8",
            "groupName": "test group",
            "groupImage":"http://66.235.194.119:8089/communication/download"
        }
    ]
}`




### Get all students -: GET
URL :http://66.235.194.119:8089/api/student/getstudentslist

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

Response:->`
{
    "success": true,
    "msg": "",
    "data": [
        {
            "fatherProfile": {
                "name": "dinesh",
                "mobile": "1234567890",
                "email": "father@gmail.com",
                "userId": ""
            },
            "motherProfile": {
                "name": "seema",
                "mobile": "1234567890",
                "email": "mother@gmail.com",
                "userId": "613845fc635d2596d6f5acfa"
            },
            "address": {
                "country": "india",
                "state": "punjab",
                "city": "mohali",
                "pinCode": "177020",
                "address": "abc"
            },
            "active": true,
            "_id": "6139fb00048dbae46b81ec04",
            "firstName": "Dinesh",
            "lastName": "sharma",
            "admissionNo": "121",
            "admissinDate": "7-2-2013",
            "dob": "7-7-2009",
            "gender": "male",
            "photoUrl": "http://uiuiu",
            "mobile": 1234567890,
            "busId": "",
            "concessionId": "",
            "category": ""
        },
        {
            "fatherProfile": {
                "name": "dinesh",
                "mobile": "1234567890",
                "email": "father@gmail.com",
                "userId": ""
            },
            "motherProfile": {
                "name": "seema",
                "mobile": "1234567890",
                "email": "mother@gmail.com",
                "userId": "613845fc635d2596d6f5acfa"
            },
            "address": {
                "country": "india",
                "state": "punjab",
                "city": "mohali",
                "pinCode": "177020",
                "address": "abc"
            },
            "active": true,
            "_id": "6139fb38048dbae46b81ec05",
            "firstName": "happy",
            "lastName": "sharma",
            "admissionNo": "122",
            "admissinDate": "7-12-2013",
            "dob": "7-7-2008",
            "gender": "male",
            "photoUrl": "http://uiuiu",
            "mobile": 1234567890,
            "busId": "",
            "concessionId": "",
            "category": ""
        }
    ]
}`


### Get a students -: GET
URL :http://66.235.194.119:8089/api/student/getstudent/6139fb38048dbae46b81ec05

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

Response:->`
{
    "success": true,
    "msg": "",
    "data": {
        "_id": "6139fb38048dbae46b81ec05",
        "firstName": "happy",
        "lastName": "sharma",
        "admissionNo": "122",
        "dob": "7-7-2008",
        "gender": "male",
        "photoUrl": "http://uiuiu",
        "busId": "",
        "concessionId": "",
        "motherProfile": {
            "userId": "613845fc635d2596d6f5acfa",
            "firstName": "seema",
            "mobile": "1234567890",
            "email": "mother@gmail.com"
        },
        "fatherProfile": {
            "userId": "",
            "firstName": "dinesh",
            "mobile": "1234567890",
            "email": "father@gmail.com"
        },
        "address": {
            "country": "india",
            "state": "punjab",
            "city": "mohali",
            "pinCode": "177020",
            "address": "abc"
        },
        "classId": "614c2b7e747721550b27f04e"
    }
}`


### Get teaching staff list :GET 
URL:http://66.235.194.119:8089/api/staffmember/getstaffmembers //principal //teacher

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`


Response-:>
    `{
    "success": true,
    "msg": "",
    "data": [
        {
            "address": {
                "country": "Italy",
                "state": "Bihar",
                "city": "Chandigarh",
                "pinCode": "177020",
                "address": "lklkl"
            },
            "userRoles": {
                "userRole": "principal"
            },
            "teachingStaff": true,
            "markAttendance": true,
            "accessToModules": [],
            "active": true,
            "schoolIds": [],
            "_id": "613845fc635d2596d6f5acfa",
            "firstName": "Ajay",
            "lastName": "Sharma",
            "mobile": "8898808633",
            "email": "principal@gmail.com",
            "password": "$2a$10$eH3QxWi/9GiC2jDhG1uktu94PYGyvcfdE2fhqvewTwM5LevSrKMfq",
            "classes": []
        },
        {
            "address": {
                "country": "Italy",
                "state": "Bihar",
                "city": "Chandigarh",
                "pinCode": "177020",
                "address": "lklkl"
            },
            "userRoles": {
                "userRole": "teacher"
            },
            "teachingStaff": true,
            "markAttendance": true,
            "accessToModules": [],
            "active": true,
            "schoolIds": [],
            "_id": "6139fa55048dbae46b81ec03",
            "firstName": "teacher A",
            "lastName": "sharma",
            "mobile": "88988086389",
            "email": "teacherA@gmail.com",
            "password": "$2a$10$eH3QxWi/9GiC2jDhG1uktu94PYGyvcfdE2fhqvewTwM5LevSrKMfq",
            "classes": []
        },
        {
            "address": {
                "country": "Italy",
                "state": "Bihar",
                "city": "Chandigarh",
                "pinCode": "177020",
                "address": "lklkl"
            },
            "userRoles": {
                "userRole": "teacher"
            },
            "teachingStaff": true,
            "markAttendance": true,
            "accessToModules": [],
            "active": true,
            "schoolIds": [],
            "_id": "6147fd0f2b0cdfba428df687",
            "firstName": "teacher b",
            "lastName": "sharma",
            "mobile": "88988086381",
            "email": "teacherB@gmail.com",
            "password": "$2a$10$eH3QxWi/9GiC2jDhG1uktu94PYGyvcfdE2fhqvewTwM5LevSrKMfq",
            "classes": []
        },
        {
            "address": {
                "country": "Italy",
                "state": "Bihar",
                "city": "Chandigarh",
                "pinCode": "177020",
                "address": "lklkl"
            },
            "userRoles": {
                "userRole": "teacher"
            },
            "teachingStaff": true,
            "markAttendance": true,
            "accessToModules": [],
            "active": true,
            "schoolIds": [],
            "_id": "6147fd2e2b0cdfba428df688",
            "firstName": "teacher c",
            "lastName": "sharma",
            "mobile": "88988086382",
            "email": "teacherC@gmail.com",
            "password": "$2a$10$eH3QxWi/9GiC2jDhG1uktu94PYGyvcfdE2fhqvewTwM5LevSrKMfq",
            "classes": []
        }
    ]
}`


### Get teaching staff user detail  :GET 
URL:http://66.235.194.119:8089/api/staffmember/getstaff/613845fc635d2596d6f5acfa

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

Response:->`
{
    "success": true,
    "msg": "",
    "data": {
        "_id": "613845fc635d2596d6f5acfa",
        "markAttendance": true,
        "accessToModules": [],
        "active": true,
        "firstName": "Ajay",
        "lastName": "Sharma",
        "mobile": "8898808633",
        "email": "principal@gmail.com",
        "password": "$2a$10$eH3QxWi/9GiC2jDhG1uktu94PYGyvcfdE2fhqvewTwM5LevSrKMfq",
        "userRoles": {
            "userRole": "principal"
        },
        "address": {
            "country": "Italy",
            "state": "Bihar",
            "city": "Chandigarh",
            "pinCode": "177020",
            "address": "lklkl"
        },
        "subjectHead_id": "",
        "classTeacherUserId": "",
        "floorId": ""
    }
}`

### Get Non teaching staff list :GET 

URL:http://66.235.194.119:8089/api/staffmember/getnonteachingstaffmembers //driver //helper //parent 


`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`


Response:->`
{
    "success": true,
    "msg": "",
    "data": [
        {
            "userRoles": {
                "userRole": "parent"
            },
            "teachingStaff": false,
            "markAttendance": false,
            "accessToModules": [],
            "active": true,
            "schoolIds": [
                "614a151d99d0400304c419c4"
            ],
            "_id": "61554ed901632d1e4e26a5c9",
            "firstName": "dasdsad",
            "lastName": "asdasdsad",
            "mobile": "2234324",
            "email": "d@d.com",
            "classes": [],
            "createdAt": "2021-09-30T05:44:57.910Z",
            "updatedAt": "2021-09-30T05:48:02.812Z",
            "__v": 0
        },
        {
            "userRoles": {
                "userRole": "parent"
            },
            "teachingStaff": false,
            "markAttendance": false,
            "accessToModules": [],
            "active": true,
            "schoolIds": [
                "614a151d99d0400304c419c4"
            ],
            "_id": "61554ed901632d1e4e26a5cd",
            "firstName": "sfsdfds",
            "lastName": "dfsdf",
            "mobile": "34234",
            "email": "m@m.com",
            "classes": [],
            "createdAt": "2021-09-30T05:44:57.919Z",
            "updatedAt": "2021-09-30T05:48:02.824Z",
            "__v": 0
        },
        {
            "userRoles": {
                "userRole": "parent"
            },
            "teachingStaff": false,
            "markAttendance": false,
            "accessToModules": [],
            "active": true,
            "schoolIds": [
                "614a151d99d0400304c419c4"
            ],
            "_id": "615c27c567df4679ce2cbb16",
            "firstName": "DD",
            "lastName": "DD",
            "mobile": "121212",
            "email": "d@d.com",
            "classes": [],
            "createdAt": "2021-10-05T10:24:05.043Z",
            "updatedAt": "2021-10-05T10:24:05.043Z",
            "__v": 0
        },
        {
            "userRoles": {
                "userRole": "parent"
            },
            "teachingStaff": false,
            "markAttendance": false,
            "accessToModules": [],
            "active": true,
            "schoolIds": [
                "614a151d99d0400304c419c4"
            ],
            "_id": "615c27c567df4679ce2cbb19",
            "firstName": "MM",
            "lastName": "MM",
            "mobile": "2121212",
            "email": "m@mm.com",
            "classes": [],
            "createdAt": "2021-10-05T10:24:05.051Z",
            "updatedAt": "2021-10-05T10:24:05.051Z",
            "__v": 0
        },
        {
            "address": {
                "country": "Italy",
                "state": "Bihar",
                "city": "Chandigarh",
                "pinCode": "177020",
                "address": "lklkl"
            },
            "userRoles": {
                "userRole": "driver",
                "addedByUserId": ""
            },
            "teachingStaff": false,
            "markAttendance": true,
            "accessToModules": [],
            "active": true,
            "schoolIds": [
                "6149bbe15064741cd6c75805",
                "613edccce6f2770619bc2988"
            ],
            "_id": "615d132b223fc8faacdc5e00",
            "firstName": "happy",
            "lastName": "sharma",
            "mobile": "88988086334",
            "email": "dineshsharma.developer+94@gmail.com",
            "password": "$2a$10$sVxz5jDW0ks6NnLuXzjYIOZSBAN6gSnOGycCTd5Mn.zZkFCuDXA.m",
            "classes": []
        },
        {
            "address": {
                "country": "Italy",
                "state": "Bihar",
                "city": "Chandigarh",
                "pinCode": "177020",
                "address": "lklkl"
            },
            "userRoles": {
                "userRole": "helper",
                "addedByUserId": ""
            },
            "teachingStaff": false,
            "markAttendance": true,
            "accessToModules": [],
            "active": true,
            "schoolIds": [
                "6149bbe15064741cd6c75805",
                "613edccce6f2770619bc2988"
            ],
            "_id": "615d13b1223fc8faacdc5e01",
            "firstName": "rahul",
            "lastName": "sharma",
            "mobile": "88988086335",
            "email": "dineshsharma.developer+97@gmail.com",
            "password": "$2a$10$sVxz5jDW0ks6NnLuXzjYIOZSBAN6gSnOGycCTd5Mn.zZkFCuDXA.m",
            "classes": []
        }
    ]
}`




### Get Non teaching staff user detail  :GET 
URL:http://66.235.194.119:8089/api/staffmember/getnonteachingstaffmember/61554ed901632d1e4e26a5c9

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

Response:->`
{
    "success": true,
    "msg": "",
    "data": {
        "_id": "615d132b223fc8faacdc5e00",
        "teachingStaff": false,
        "markAttendance": true,
        "accessToModules": [],
        "active": true,
        "schoolIds": [
            "6149bbe15064741cd6c75805",
            "613edccce6f2770619bc2988"
        ],
        "firstName": "happy",
        "lastName": "sharma",
        "mobile": "88988086334",
        "email": "dineshsharma.developer+94@gmail.com",
        "password": "$2a$10$sVxz5jDW0ks6NnLuXzjYIOZSBAN6gSnOGycCTd5Mn.zZkFCuDXA.m",
        "userRoles": {
            "userRole": "driver",
            "addedByUserId": ""
        },
        "address": {
            "country": "Italy",
            "state": "Bihar",
            "city": "Chandigarh",
            "pinCode": "177020",
            "address": "lklkl"
        }
    }
}
}`


### Send Message for Group :POST
URL :http://66.235.194.119:8089/api/communication/sendmessage

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

body:`
"message":"hello  sir, i am comming"
"groupId":"615ace17d9ab5d796f9ecc99"
"senderId":"613845fc635d2596d6f5acfa"
`

Response : -> `
{
    "success": true,
    "msg": "Message sent successfully",
    "data": {
        "userIds": [],
        "_id": "616e4cb4f8e33d388499ad84",
        "groupId": "615ace17d9ab5d796f9ecc99",
        "message": "hello  sir, i am comming",
        "senderId": "613845fc635d2596d6f5acfa",
        "createdAt": "2021-10-19T04:42:28.821Z",
        "updatedAt": "2021-10-19T04:42:28.821Z",
        "__v": 0
    }
}`


### Send Message for users :POST
URL :http://66.235.194.119:8089/api/communication/sendmessage

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

body:`
"message":"hello  sir, i am comming"
"userIds":["6149c849d7948f1ca605d7c8"],
"senderId":"613845fc635d2596d6f5acfa"
`

Response : -> `
{
    "success": true,
    "msg": "Message sent successfully",
    "data": {
        "userIds": [6149c849d7948f1ca605d7c8],
        "_id": "616e4cb4f8e33d388499ad84",
        "message": "hello sir, i am comming",
        "senderId": "613845fc635d2596d6f5acfa",
        "createdAt": "2021-10-19T04:42:28.821Z",
        "updatedAt": "2021-10-19T04:42:28.821Z",
        "__v": 0
    }
}`


### Get group joind users :GET

URL :http://66.235.194.119:8089/api/communication/getjoinedgroupusers

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
 groupId:'615ace17d9ab5d796f9ecc99'
}

Response :->`
{
    "success": true,
    "data": {
        "users": [
            {
                "userRoles": {
                    "userRole": "parent"
                },
                "teachingStaff": false,
                "markAttendance": false,
                "accessToModules": [],
                "active": true,
                "schoolIds": [
                    "614a151d99d0400304c419c4"
                ],
                "primary": false,
                "_id": "61554ed901632d1e4e26a5c9",
                "firstName": "dasdsad",
                "lastName": "asdasdsad",
                "mobile": "2234324",
                "email": "d@d.com",
                "classes": [],
                "createdAt": "2021-09-30T05:44:57.910Z",
                "updatedAt": "2021-09-30T05:48:02.812Z",
                "__v": 0
            },
            {
                "address": {
                    "address": "",
                    "city": "sd",
                    "pinCode": "3234324",
                    "state": "Delhi",
                    "country": "India"
                },
                "userRoles": {
                    "userRole": "Peon"
                },
                "teachingStaff": false,
                "markAttendance": true,
                "accessToModules": [],
                "active": true,
                "schoolIds": [
                    "614a151d99d0400304c419c4"
                ],
                "primary": false,
                "_id": "615c2b7167df4679ce2cbb73",
                "firstName": "ttt",
                "lastName": "ttt",
                "mobile": "34324",
                "email": "tt@t.com",
                "classes": [],
                "createdAt": "2021-10-05T10:39:45.526Z",
                "updatedAt": "2021-10-05T10:40:34.054Z",
                "__v": 0
            }
        ],
        "group": {
            "groupStudentsIds": [],
            "groupUserIds": [
                "615c2b7167df4679ce2cbb73",
                "61554ed901632d1e4e26a5c9"
            ],
            "_id": "615ace17d9ab5d796f9ecc99",
            "groupName": "test group",
            "groupImage": "http://66.235.194.119",
            "createdAt": "2021-10-04T09:49:11.218Z",
            "updatedAt": "2021-10-04T09:49:11.218Z",
            "__v": 0
        }
    }
}`



### Get group Messages

URL:http://66.235.194.119:8089/api/communication/getmessages

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
 groupId:'615ace17d9ab5d796f9ecc99'
}

Response `{
    "success": true,
    "data": [
        {
            "userIds": [],
            "_id": "616e4b89b6e1b22506eadaac",
            "groupId": "615ace17d9ab5d796f9ecc99",
            "message": "hello  sir , i am comming",
            "senderId": "613845fc635d2596d6f5acfa",
            "createdAt": "2021-10-19T04:37:29.133Z",
            "updatedAt": "2021-10-19T04:37:29.133Z",
            "__v": 0
        },
        {
            "userIds": [],
            "_id": "616e4cb4f8e33d388499ad84",
            "groupId": "615ace17d9ab5d796f9ecc99",
            "message": "hello  sir, i am comming",
            "senderId": "613845fc635d2596d6f5acfa",
            "createdAt": "2021-10-19T04:42:28.821Z",
            "updatedAt": "2021-10-19T04:42:28.821Z",
            "__v": 0
        }
    ]
}`


### Teacher api List 

###Login API Credentials - We can use same login api

## Login Credentials:  
    mobile:88988086389
    password:123456




### Classes List - GET
URL:http://66.235.194.119:8089/api/class/getclasses

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
}

Response:->`
{
    "success": true,
    "msg": "",
    "data": [
        {
            "_id": "614c2b5c747721550b27f048",
            "students": [],
            "className": "1",
            "section": "A",
            "classTeacherUserId": "612cad0e25c22a23e8067b59",
            "subjects": [],
            "createdAt": "2021-09-23T07:23:08.297Z",
            "updatedAt": "2021-09-23T07:23:08.297Z",
            "__v": 0,
            "subject_docs": []
        },
        {
            "_id": "614c2b72747721550b27f04b",
            "students": [],
            "className": "1",
            "section": "B",
            "classTeacherUserId": "612cad0e25c22a23e8067b59",
            "subjects": [],
            "createdAt": "2021-09-23T07:23:30.752Z",
            "updatedAt": "2021-09-23T07:23:30.752Z",
            "__v": 0,
            "subject_docs": []
        },
        {
            "_id": "614c2b7e747721550b27f04e",
            "students": [
                "6139fb38048dbae46b81ec05",
                "6139fa55048dbae46b81ec03"
            ],
            "className": "I",
            "section": "A",
            "classTeacherUserId": "6139fa55048dbae46b81ec03",
            "subjects": [
                {
                    "subjectId": "6138a8061ddbd9b41f04406c",
                    "teacherUserId": "61389a1e1ddbd9b41f04406b",
                    "timeFrom": "12:00 AM",
                    "timeTo": "2:00 PM",
                    "daysOfWeek": [
                        "monday"
                    ]
                }
            ],
            "createdAt": "2021-09-23T07:23:42.016Z",
            "updatedAt": "2021-09-23T07:23:42.016Z",
            "__v": 0,
            "dateFrom": "02-04-2021",
            "dateTo": "02-08-2021",
            "subject_docs": []
        }
    ],
    "teacherData": [
        {
            "address": {
                "address": "asdad",
                "city": "Chd",
                "pinCode": "160022",
                "state": "Punjab",
                "country": "India"
            },
            "userRoles": {
                "userRole": "Teacher"
            },
            "teachingStaff": true,
            "markAttendance": true,
            "accessToModules": [
                "false",
                "classTeacher",
                "false",
                "false"
            ],
            "active": true,
            "schoolIds": [
                "614a151d99d0400304c419c4"
            ],
            "primary": false,
            "_id": "6154b05501632d1e4e26a423",
            "firstName": "Sheena",
            "lastName": "Bajaj",
            "mobile": "12121212",
            "email": "s@s.com",
            "photoUrl": "1632940057931-reuse.jpg",
            "classes": [],
            "createdAt": "2021-09-29T18:28:37.844Z",
            "updatedAt": "2021-09-30T06:09:18.436Z",
            "__v": 0
        },
        {
            "address": {
                "address": "Test",
                "city": "Chd",
                "pinCode": "232323",
                "state": "Chandigarh",
                "country": "India"
            },
            "userRoles": {
                "userRole": "Teacher"
            },
            "teachingStaff": true,
            "markAttendance": true,
            "accessToModules": [],
            "active": true,
            "schoolIds": [
                "614a151d99d0400304c419c4"
            ],
            "primary": false,
            "_id": "615c2a7767df4679ce2cbb5b",
            "firstName": "manju",
            "lastName": "sharma",
            "mobile": "12121212",
            "email": "m@m.com",
            "photoUrl": "1633429967376-recycle.jpg",
            "classes": [
                {
                    "_id": "615c2a7767df4679ce2cbb5c",
                    "id": "614cc249852881295be71ad8",
                    "name": "I-A",
                    "subject": [
                        {
                            "_id": "615c2a7767df4679ce2cbb5d",
                            "label": "English",
                            "value": "614cb778852881295be71925"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb5e",
                            "label": "Hindi",
                            "value": "614cb783852881295be71930"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb5f",
                            "label": "Maths",
                            "value": "614cb7ae852881295be7194f"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb60",
                            "label": "SST",
                            "value": "6151760ff212b73b2da25cf3"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb61",
                            "label": "Comp",
                            "value": "6151761ef212b73b2da25cfe"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb62",
                            "label": "Science",
                            "value": "6151762df212b73b2da25d09"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb63",
                            "label": "Computer",
                            "value": "6156e25ae0ef9c39d70e0531"
                        }
                    ]
                },
                {
                    "_id": "615c2a7767df4679ce2cbb64",
                    "id": "614cc249852881295be71ad8",
                    "name": "I-A",
                    "subject": [
                        {
                            "_id": "615c2a7767df4679ce2cbb65",
                            "label": "English",
                            "value": "614cb778852881295be71925"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb66",
                            "label": "Hindi",
                            "value": "614cb783852881295be71930"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb67",
                            "label": "Maths",
                            "value": "614cb7ae852881295be7194f"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb68",
                            "label": "SST",
                            "value": "6151760ff212b73b2da25cf3"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb69",
                            "label": "Comp",
                            "value": "6151761ef212b73b2da25cfe"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb6a",
                            "label": "Science",
                            "value": "6151762df212b73b2da25d09"
                        },
                        {
                            "_id": "615c2a7767df4679ce2cbb6b",
                            "label": "Computer",
                            "value": "6156e25ae0ef9c39d70e0531"
                        }
                    ]
                }
            ],
            "createdAt": "2021-10-05T10:35:35.196Z",
            "updatedAt": "2021-10-05T10:35:35.196Z",
            "__v": 0
        }
    ]
}`


### Time Table for principal - GET 

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

URL:http://66.235.194.119:8089/api/class/getclass/61726edf699acc5f2c9393d1

RESPONSE:`{
    "success": true,
    "msg": "",
    "data": {
        "_id": "61726edf699acc5f2c9393d1",
        "className": "XII",
        "section": "A",
        "subjects": [
            {
                "_id": "617a79befc49391e29845d01",
                "subjectId": "6139fb65048dbae46b81ec06"
            },
            {
                "_id": "617a79befc49391e29845d02",
                "subjectId": "6172419007acfe2e1a1f08f0"
            },
            {
                "_id": "617a79befc49391e29845d03",
                "subjectId": "61728d38af17723dbe47b27a"
            },
            {
                "_id": "617a79befc49391e29845d04",
                "subjectId": "6172419c07acfe2e1a1f08fb"
            },
            {
                "_id": "617a79befc49391e29845d05",
                "subjectId": "617691d64db2f363ae0ce4e4"
            }
        ],
        "updatedAt": "2021-10-28T10:55:09.699Z",
        "__v": 20,
        "createdAt": "2021-10-28T10:25:04.034Z",
        "students": [],
        "timeTable": [
            {
                "_id": "617a804c5cc3fb320101901e",
                "dayName": "Monday",
                "subjectsTiming": [
                    {
                        "_id": "617a818d5cc3fb320101909d",
                        "subjectId": "6139fb65048dbae46b81ec06",
                        "timeFrom": "09:00",
                        "timeTo": "09:59",
                        "subjectsTiming": {
                            "_id": "617a818d5cc3fb320101909d",
                            "subjectId": "6139fb65048dbae46b81ec06",
                            "subjectName": "science",
                            "timeFrom": "09:00",
                            "timeTo": "09:59",
                            "firstName": "teacher A",
                            "lastName": "sharma",
                            "email": "teacherA@gmail.com",
                            "teacherId": "6139fa55048dbae46b81ec03"
                        }
                    },
                    {
                        "_id": "617a818d5cc3fb320101909e",
                        "subjectId": "61728d38af17723dbe47b27a",
                        "timeFrom": "10:00",
                        "timeTo": "10:59",
                        "subjectsTiming": {
                            "_id": "617a818d5cc3fb320101909e",
                            "subjectId": "61728d38af17723dbe47b27a",
                            "firstName": "teacher A",
                            "lastName": "sharma",
                            "email": "teacherA@gmail.com",
                            "teacherId": "6139fa55048dbae46b81ec03",
                            "subjectName": "hindi",
                            "timeFrom": "10:00",
                            "timeTo": "10:59"
                        }
                    },
                    {
                        "_id": "617a818d5cc3fb320101909f",
                        "subjectId": "6172419c07acfe2e1a1f08fb",
                        "timeFrom": "11:00",
                        "timeTo": "11:59",
                        "subjectsTiming": {
                            "_id": "617a818d5cc3fb320101909f",
                            "subjectId": "6172419c07acfe2e1a1f08fb",
                            "firstName": "teacher A",
                            "lastName": "sharma",
                            "email": "teacherA@gmail.com",
                            "teacherId": "6139fa55048dbae46b81ec03",
                            "subjectName": "math",
                            "timeFrom": "11:00",
                            "timeTo": "11:59"
                        }
                    },
                    {
                        "_id": "617a818d5cc3fb32010190a0",
                        "subjectId": "6172419007acfe2e1a1f08f0",
                        "timeFrom": "12:00",
                        "timeTo": "12:59",
                        "subjectsTiming": {
                            "_id": "617a818d5cc3fb32010190a0",
                            "subjectId": "6172419007acfe2e1a1f08f0",
                            "firstName": "teacher A",
                            "lastName": "sharma",
                            "email": "teacherA@gmail.com",
                            "teacherId": "6139fa55048dbae46b81ec03",
                            "subjectName": "english",
                            "timeFrom": "12:00",
                            "timeTo": "12:59"
                        }
                    },
                    {
                        "_id": "617a818d5cc3fb32010190a1",
                        "subjectId": "617691d64db2f363ae0ce4e4",
                        "timeFrom": "02:00",
                        "timeTo": "02:59",
                        "subjectsTiming": {
                            "_id": "617a818d5cc3fb32010190a1",
                            "subjectId": "617691d64db2f363ae0ce4e4",
                            "firstName": "teacher A",
                            "lastName": "sharma",
                            "email": "teacherA@gmail.com",
                            "teacherId": "6139fa55048dbae46b81ec03",
                            "subjectName": "art",
                            "timeFrom": "02:00",
                            "timeTo": "02:59"
                        }
                    }
                ]
            }
        ],
        "subject_docs": [
            {
                "_id": "6139fb65048dbae46b81ec06",
                "subjectName": "science",
                "subjectHeadUserId": "6139fa55048dbae46b81ec03",
                "teachers": [
                    "6139fa55048dbae46b81ec03"
                ]
            },
            {
                "_id": "6172419007acfe2e1a1f08f0",
                "teachers": [],
                "subjectName": "english",
                "createdAt": "2021-10-22T04:44:00.959Z",
                "updatedAt": "2021-10-22T04:44:00.959Z",
                "__v": 0
            },
            {
                "_id": "6172419c07acfe2e1a1f08fb",
                "teachers": [
                    "6139fa55048dbae46b81ec03"
                ],
                "subjectName": "math",
                "createdAt": "2021-10-22T04:44:12.348Z",
                "updatedAt": "2021-10-22T04:44:12.348Z",
                "__v": 0,
                "subjectHeadUserId": "6139fa55048dbae46b81ec03"
            },
            {
                "_id": "61728d38af17723dbe47b27a",
                "teachers": [],
                "subjectName": "hindi",
                "createdAt": "2021-10-22T10:06:48.429Z",
                "updatedAt": "2021-10-22T10:06:48.429Z",
                "__v": 0
            },
            {
                "_id": "617691d64db2f363ae0ce4e4",
                "teachers": [],
                "subjectName": "art",
                "createdAt": "2021-10-25T11:15:34.578Z",
                "updatedAt": "2021-10-28T10:21:26.502Z",
                "__v": 0
            }
        ]
    }
}`



### For teacher time table : GET
URL:http://66.235.194.119:8089/api/class/getteachertimetable

PARAMS:{teacherId:6139fa55048dbae46b81ec03}

RESPONSE:`{
    ""success"": true,
    ""data"": [     {
            ""students"": [],
            ""_id"": ""61724b4be8511e02efcb11d4"",
            ""className"": ""Preparatory"",
            ""section"": ""A"",
            ""subjects"": [
                {
                    ""_id"": ""61728de8af17723dbe47b2ba"",
                    ""subjectId"": ""6139fb65048dbae46b81ec06"",
                    ""daysOfWeek"": []
                },
                {
                    ""_id"": ""61728de8af17723dbe47b2bb"",
                    ""subjectId"": ""6172419c07acfe2e1a1f08fb"",
                    ""daysOfWeek"": []
                },
                {
                    ""_id"": ""61728de8af17723dbe47b2bc"",
                    ""subjectId"": ""61728d38af17723dbe47b27a"",
                    ""daysOfWeek"": []
                },
                {
                    ""_id"": ""61728de8af17723dbe47b2bd"",
                    ""subjectId"": ""6172419007acfe2e1a1f08f0"",
                    ""daysOfWeek"": []
                }
            ],
            ""timeTable"": [
                {
                    ""dayName"": ""Tuesday"",
                    ""subjectsTiming"": [
                        {
                            ""_id"": ""617693644db2f363ae0ce506"",
                            ""subjectId"": ""6139fb65048dbae46b81ec06"",
                            ""subjectName"": ""science"",
                            ""timeFrom"": ""17:52"",
                            ""timeTo"": ""17:52"",
                            ""teacher"": {
                                ""firstName"": ""teacher A"",
                                ""lastName"": ""sharma"",
                                ""_id"": ""6139fa55048dbae46b81ec03"",
                                ""email"": ""teacherA@gmail.com""
                            }
                        },
                        {
                            ""_id"": ""617693644db2f363ae0ce507"",
                            ""subjectId"": ""6172419c07acfe2e1a1f08fb"",
                            ""subjectName"": ""math"",
                            ""timeFrom"": ""18:54"",
                            ""timeTo"": ""18:55"",
                            ""teacher"": {
                                ""firstName"": ""teacher A"",
                                ""lastName"": ""sharma"",
                                ""_id"": ""6139fa55048dbae46b81ec03"",
                                ""email"": ""teacherA@gmail.com""
                            }
                        }
                    ]
                }
            ],
            ""createdAt"": ""2021-10-22T05:25:31.373Z"",
            ""updatedAt"": ""2021-10-22T10:09:44.134Z"",
            ""__v"": 0
        },
        {
            ""students"": [],
            ""_id"": ""61726edf699acc5f2c9393c1"",
            ""className"": ""Preparatory"",
            ""section"": ""A"",
            ""subjects"": [
                {
                    ""_id"": ""61728de8af17723dbe47b2ba"",
                    ""subjectId"": ""6139fb65048dbae46b81ec06"",
                    ""daysOfWeek"": []
                },
                {
                    ""_id"": ""61728de8af17723dbe47b2bb"",
                    ""subjectId"": ""6172419c07acfe2e1a1f08fb"",
                    ""daysOfWeek"": []
                },
                {
                    ""_id"": ""61728de8af17723dbe47b2bc"",
                    ""subjectId"": ""61728d38af17723dbe47b27a"",
                    ""daysOfWeek"": []
                },
                {
                    ""_id"": ""61728de8af17723dbe47b2bd"",
                    ""subjectId"": ""6172419007acfe2e1a1f08f0"",
                    ""daysOfWeek"": []
                }
            ],
            ""updatedAt"": ""2021-10-25T11:22:12.495Z"",
            ""__v"": 2,
            ""createdAt"": ""2021-10-25T11:16:10.927Z"",
            ""timeTable"": [
                {
                    ""_id"": ""617691fa4db2f363ae0ce4f4"",
                    ""dayName"": ""Tuesday"",
                    ""subjectsTiming"": [
                        {
                            ""_id"": ""617693644db2f363ae0ce506"",
                            ""subjectId"": ""6139fb65048dbae46b81ec06"",
                            ""subjectName"": ""science"",
                            ""timeFrom"": ""17:52"",
                            ""timeTo"": ""17:52"",
                            ""teacher"": {
                                ""firstName"": ""teacher A"",
                                ""lastName"": ""sharma"",
                                ""_id"": ""6139fa55048dbae46b81ec03"",
                                ""email"": ""teacherA@gmail.com""
                            }
                        },
                        {
                            ""_id"": ""617693644db2f363ae0ce507"",
                            ""subjectId"": ""6172419c07acfe2e1a1f08fb"",
                            ""subjectName"": ""math"",
                            ""timeFrom"": ""18:54"",
                            ""timeTo"": ""18:55"",
                            ""teacher"": {
                                ""firstName"": ""teacher A"",
                                ""lastName"": ""sharma"",
                                ""_id"": ""6139fa55048dbae46b81ec03"",
                                ""email"": ""teacherA@gmail.com""
                            }
                        }
                    ]
                }
            ]
        },
        {
            ""students"": [],
            ""_id"": ""61726edf699acc5f2c9393d1"",
            ""className"": ""XII"",
            ""section"": ""A"",
            ""subjects"": [
                {
                    ""_id"": ""617a79befc49391e29845d01"",
                    ""subjectId"": ""6139fb65048dbae46b81ec06""
                },
                {
                    ""_id"": ""617a79befc49391e29845d02"",
                    ""subjectId"": ""6172419007acfe2e1a1f08f0""
                },
                {
                    ""_id"": ""617a79befc49391e29845d03"",
                    ""subjectId"": ""61728d38af17723dbe47b27a""
                },
                {
                    ""_id"": ""617a79befc49391e29845d04"",
                    ""subjectId"": ""6172419c07acfe2e1a1f08fb""
                },
                {
                    ""_id"": ""617a79befc49391e29845d05"",
                    ""subjectId"": ""617691d64db2f363ae0ce4e4""
                }
            ],
            ""updatedAt"": ""2021-10-28T10:55:09.699Z"",
            ""__v"": 20,
            ""createdAt"": ""2021-10-28T10:25:04.034Z"",
            ""timeTable"": [
                {
                    ""_id"": ""617a804c5cc3fb320101901e"",
                    ""dayName"": ""Monday"",
                    ""subjectsTiming"": [
                        {
                            ""_id"": ""617a818d5cc3fb320101909d"",
                            ""subjectId"": ""6139fb65048dbae46b81ec06"",
                            ""subjectName"": ""science"",
                            ""timeFrom"": ""09:00"",
                            ""timeTo"": ""09:59"",
                            ""teacher"": {
                                ""firstName"": ""teacher A"",
                                ""lastName"": ""sharma"",
                                ""_id"": ""6139fa55048dbae46b81ec03"",
                                ""email"": ""teacherA@gmail.com""
                            }
                        },
                        {
                            ""_id"": ""617a818d5cc3fb320101909e"",
                            ""subjectId"": ""61728d38af17723dbe47b27a"",
                            ""subjectName"": ""hindi"",
                            ""timeFrom"": ""10:00"",
                            ""timeTo"": ""10:59"",
                            ""teacher"": {
                                ""firstName"": ""teacher A"",
                                ""lastName"": ""sharma"",
                                ""_id"": ""6139fa55048dbae46b81ec03"",
                                ""email"": ""teacherA@gmail.com""
                            }
                        },
                        {
                            ""_id"": ""617a818d5cc3fb320101909f"",
                            ""subjectId"": ""6172419c07acfe2e1a1f08fb"",
                            ""subjectName"": ""math"",
                            ""timeFrom"": ""11:00"",
                            ""timeTo"": ""11:59"",
                            ""teacher"": {
                                ""firstName"": ""teacher A"",
                                ""lastName"": ""sharma"",
                                ""_id"": ""6139fa55048dbae46b81ec03"",
                                ""email"": ""teacherA@gmail.com""
                            }
                        },
                        {
                            ""_id"": ""617a818d5cc3fb32010190a0"",
                            ""subjectId"": ""6172419007acfe2e1a1f08f0"",
                            ""subjectName"": ""english"",
                            ""timeFrom"": ""12:00"",
                            ""timeTo"": ""12:59"",
                            ""teacher"": {
                                ""firstName"": ""teacher A"",
                                ""lastName"": ""sharma"",
                                ""_id"": ""6139fa55048dbae46b81ec03"",
                                ""email"": ""teacherA@gmail.com""
                            }
                        },
                        {
                            ""_id"": ""617a818d5cc3fb32010190a1"",
                            ""subjectId"": ""617691d64db2f363ae0ce4e4"",
                            ""subjectName"": ""art"",
                            ""timeFrom"": ""02:00"",
                            ""timeTo"": ""02:59"",
                            ""teacher"": {
                                ""firstName"": ""teacher A"",
                                ""lastName"": ""sharma"",
                                ""_id"": ""6139fa55048dbae46b81ec03"",
                                ""email"": ""teacherA@gmail.com""
                            }
                        }
                    ]
                }
            ]
        }
    ]
   
}`

### List Of Holidays - GET

URL:http://66.235.194.119:8089/api/holiday/getholidays

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
}

Response:->`
{
    "success": true,
    "msg": "",
    "data": [
        {
            "_id": "61723f1807acfe2e1a1f0896",
            "festival": "Dewali",
            "dateFrom": "2021-11-04",
            "dateTo": "2021-11-08",
            "createdAt": "2021-10-22T04:33:28.961Z",
            "updatedAt": "2021-10-22T04:33:28.961Z",
            "__v": 0
        },
        {
            "_id": "61723f4007acfe2e1a1f089e",
            "festival": "Holi",
            "dateFrom": "2022-03-14",
            "dateTo": "2022-03-23",
            "createdAt": "2021-10-22T04:34:08.287Z",
            "updatedAt": "2021-10-22T04:34:08.287Z",
            "__v": 0
        }
    ]
}`


### Fees Structure - GET

URL:http://66.235.194.119:8089/api/feedata/getfeedatalist

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
}

Response:->`
{
    "success": true,
    "msg": "",
    "data": [
        {
            "_id": "6172409207acfe2e1a1f08b3",
            "className": "I",
            "session": "2021",
            "feesDetails": [
                {
                    "_id": "6172409207acfe2e1a1f08b4",
                    "particular": "One Month",
                    "amount": 2000
                },
                {
                    "_id": "6172409207acfe2e1a1f08b5",
                    "particular": "Dresses",
                    "amount": 60000
                }
            ],
            "totalAmount": 62000,
            "createdAt": "2021-10-22T04:39:46.463Z",
            "updatedAt": "2021-10-22T04:39:46.463Z",
            "__v": 0
        }
    ]
}`


### Exam Schedule - GET

URL: http://66.235.194.119:8089/api/examschedule/getexamschedulebyclassname

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS: - {
className:"Preparatory"
}

Response:->`{
    "success": true,
    "data": [
        {
            "_id": "61728e0caf17723dbe47b2da",
            "classIds": [
                "61724b4be8511e02efcb11d4",
                "61726edf699acc5f2c9393c1"
            ],
            "className": "Preparatory",
            "term": "617264f1216eaa2388f4a5ec",
            "subjects": {
                "_id": "61728e0caf17723dbe47b2db",
                "timeOfExam": {
                    "from": "2021-10-25T13:13:00.000Z",
                    "to": "2021-10-25T16:16:00.000Z"
                },
                "subjectId": "6172419007acfe2e1a1f08f0",
                "dateOfExam": "2021-10-25T00:00:00.000Z"
            },
            "addedByUserId": "6149c849d7948f1ca605d7c8",
            "createdAt": "2021-10-22T10:10:20.245Z",
            "updatedAt": "2021-10-22T10:10:43.520Z",
            "__v": 0,
            "subjectsData": {
                "_id": "6172419007acfe2e1a1f08f0",
                "teachers": [],
                "subjectName": "english",
                "createdAt": "2021-10-22T04:44:00.959Z",
                "updatedAt": "2021-10-22T04:44:00.959Z",
                "__v": 0
            }
        }
    ]
}`

### School Diary
### Create HomeWork - POST
URL:http://66.235.194.119:8089/api/schooldiary/createhomework 

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

BODY:
    `{
    "file":["http://66.235.194.119:8089/api/schooldiary/createhomework.docx","http://66.235.194.119:8089/api/schooldiary/createhomework2.docx"],
    "userId":"6139fa55048dbae46b81ec03",
    "classId":"61726edf699acc5f2c9393c1",
    "homeWorkTitle":"new homework",
    "subjectId":"6172419c07acfe2e1a1f08fb",
    "description":"here we can add the work description"
  }`


Response:`{
    "success": true,
    "data": {
        "file": [
            "http://66.235.194.119:8089/api/schooldiary/createhomework.docx",
            "http://66.235.194.119:8089/api/schooldiary/createhomework2.docx"
        ],
        "_id": "6179f52333c95e69074e3f36",
        "userId": "6139fa55048dbae46b81ec03",
        "classId": "61726edf699acc5f2c9393c1",
        "homeWorkTitle": "new homework",
        "subjectId": "6172419c07acfe2e1a1f08fb",
        "description": "here we can add the work description",
        "createdAt": "2021-10-28T00:56:03.440Z",
        "updatedAt": "2021-10-28T00:56:03.440Z",
        "__v": 0
    }
}
`

### Home Work List - GET

URL:http://66.235.194.119:8089/api/schooldiary/createhomework 

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

PARAMS:{userId:"6139fa55048dbae46b81ec03"}

RESPONSE:`{
    "success": true,
    "data": [
        {
            "_id": "6177a6fdb8397d2c7c7e1db5",
            "homeWorkTitle": "lession one ",
            "userId": "6139fa55048dbae46b81ec03",
            "file": "http://66.235.194.119:8089/api/s",
            "classId": "61726edf699acc5f2c9393cd",
            "createdAt": "2021-10-26T06:58:05.922Z",
            "updatedAt": "2021-10-26T06:58:05.922Z",
            "__v": 0
        },
        {
            "_id": "6177a79ab8397d2c7c7e1dfe",
            "homeWorkTitle": "lession two",
            "userId": "6139fa55048dbae46b81ec03",
            "file": "http://66.235.194.119:8089/api/file.dosx",
            "classId": "61726edf699acc5f2c9393cd",
            "createdAt": "2021-10-26T07:00:42.921Z",
            "updatedAt": "2021-10-26T07:00:42.921Z",
            "__v": 0
        },{
        "file": [
            "http://66.235.194.119:8089/api/schooldiary/createhomework.docx",
            "http://66.235.194.119:8089/api/schooldiary/createhomework2.docx"
        ],
        "_id": "6179f52333c95e69074e3f36",
        "userId": "6139fa55048dbae46b81ec03",
        "classId": "61726edf699acc5f2c9393c1",
        "homeWorkTitle": "new homework",
        "subjectId": "6172419c07acfe2e1a1f08fb",
        "description": "here we can add the work description",
        "createdAt": "2021-10-28T00:56:03.440Z",
        "updatedAt": "2021-10-28T00:56:03.440Z",
        "__v": 0
    }
    ]
}`

### CreateComplaint - POST

URL:http://66.235.194.119:8089/api/schooldiary/createcomplaint

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`

BODY:`{
"studentId":["6139fb38048dbae46b81ec05","6139fb00048dbae46b81ec04"],
"userId":"6139fa55048dbae46b81ec03",
"classId":"61726edf699acc5f2c9393cd",
"complaintDescription":"amit was not done the work",
"title":"new complaint "
}`

RESPONSE:`{
    "success": true,
    "data": {
        "studentId": [
            "6139fb38048dbae46b81ec05",
            "6139fb00048dbae46b81ec04"
        ],
        "_id": "61791e710b668c707316a23e",
        "userId": "6139fa55048dbae46b81ec03",
        "classId": "61726edf699acc5f2c9393cd",
        "complaintDescription": "amit was not done the work",
        "title": "new complaint ",
        "createdAt": "2021-10-27T09:40:01.530Z",
        "updatedAt": "2021-10-27T09:40:01.530Z",
        "__v": 0
    },
    "request": {
        "studentId": [
            "6139fb38048dbae46b81ec05",
            "6139fb00048dbae46b81ec04"
        ],
        "userId": "6139fa55048dbae46b81ec03",
        "classId": "61726edf699acc5f2c9393cd",
        "complaintDescription": "amit was not done the work",
        "title": "new complaint "
    }
}`

### Complaints List - GET

URL:http://66.235.194.119:8089/api/schooldiary/getcomplaint

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`


RESPONSE:`{
    "success": true,
    "data": [
        {
            "_id": "6177c9d6163ceb78495a694d",
            "studentId": [
                "6139fb38048dbae46b81ec05",
                "6139fb00048dbae46b81ec04"
            ],
            "userId": "6139fa55048dbae46b81ec03",
            "classId": "61726edf699acc5f2c9393cd",
            "complaintDescription": "amit was not done the work",
            "students": [
                {
                    "firstName": "Dinesh",
                    "lastName": "sharma",
                    "dob": "7-7-2009",
                    "photoUrl": "http://uiuiu"
                },
                {
                    "firstName": "happy",
                    "lastName": "sharma",
                    "dob": "7-7-2008",
                    "photoUrl": "http://uiuiu"
                }
            ]
        },
        {
            "_id": "61791e710b668c707316a23e",
            "studentId": [
                "6139fb38048dbae46b81ec05",
                "6139fb00048dbae46b81ec04"
            ],
            "userId": "6139fa55048dbae46b81ec03",
            "classId": "61726edf699acc5f2c9393cd",
            "complaintDescription": "amit was not done the work",
            "title": "new complaint ",
            "students": [
                {
                    "firstName": "Dinesh",
                    "lastName": "sharma",
                    "dob": "7-7-2009",
                    "photoUrl": "http://uiuiu"
                },
                {
                    "firstName": "happy",
                    "lastName": "sharma",
                    "dob": "7-7-2008",
                    "photoUrl": "http://uiuiu"
                }
            ]
        }
    ]
}`

### Notice Board - GET

URL:http://66.235.194.119:8089/api/schooldiary/getnoticeboard

`HEADERS: {
schoolId:"613edccce6f2770619bc2988",
}`


PARAMS:{
 userId:'6139fa55048dbae46b81ec03'
}

RESPONSE`{
    "success": true,
    "data": [
        {
            "_id": "6177c9d6163ceb78495a694d",
            "studentId": [
                "6139fb38048dbae46b81ec05",
                "6139fb00048dbae46b81ec04"
            ],
            "userId": "6139fa55048dbae46b81ec03",
            "classId": "61726edf699acc5f2c9393cd",
            "complaintDescription": "amit was not done the work",
            "homeworks": [
                {
                    "_id": "6177a6fdb8397d2c7c7e1db5",
                    "homeWorkTitle": "lession one ",
                    "userId": "6139fa55048dbae46b81ec03",
                    "file": "http://66.235.194.119:8089/api/s",
                    "classId": "61726edf699acc5f2c9393cd",
                    "createdAt": "2021-10-26T06:58:05.922Z",
                    "updatedAt": "2021-10-26T06:58:05.922Z",
                    "__v": 0
                },
                {
                    "_id": "6177a79ab8397d2c7c7e1dfe",
                    "homeWorkTitle": "lession two",
                    "userId": "6139fa55048dbae46b81ec03",
                    "file": "http://66.235.194.119:8089/api/file.dosx",
                    "classId": "61726edf699acc5f2c9393cd",
                    "createdAt": "2021-10-26T07:00:42.921Z",
                    "updatedAt": "2021-10-26T07:00:42.921Z",
                    "__v": 0
                }
            ],
            "students": [
                {
                    "firstName": "Dinesh",
                    "lastName": "sharma",
                    "dob": "7-7-2009",
                    "photoUrl": "http://uiuiu"
                },
                {
                    "firstName": "happy",
                    "lastName": "sharma",
                    "dob": "7-7-2008",
                    "photoUrl": "http://uiuiu"
                }
            ]
        }
    ]
}`


### Get School Terms
URL:http://66.235.194.119:8089/api/school/getschool
PARAMS:{id:613edccce6f2770619bc2988}
RESPONSE:`{
    "success": true,
    "msg": "",
    "data": {
        "_id": "613edccce6f2770619bc2988",
        "schoolName": "kids school",
        "databaseName": "kids_school",
        "address": {
            "allowedRadius": 50,
            "country": "India",
            "state": "Punjab",
            "city": "Chandigarh",
            "pinCode": "160062",
            "address": "Mohali Pind Rd, Sector 51, Sahibzada Ajit Singh Nagar, Chandigarh 160062",
            "longitude": "30.7029° N",
            "latitude": "76.7375° E"
        },
        "colorScheme": {
            "schoolLogo": "1631018253646-yps-logo.png",
            "backgroundColor": "#5144a6",
            "fontColor": "#ffffff"
        },
        "adminInfo": {
            "firstName": "schoolAdmin A",
            "lastName": "sharma",
            "email": "shivam76east+8@gmail+1.com",
            "mobile": "88988086389",
            "password": "$2a$10$eH3QxWi/9GiC2jDhG1uktu94PYGyvcfdE2fhqvewTwM5LevSrKMfq"
        },
        "schoolTime": [
            {
                "classIds": [
                    "61802cc85a3e191abcc65cbc",
                    "61724b4be8511e02efcb11d4",
                    "614c2b7e747721550b27f04e",
                    "614c2b72747721550b27f04b",
                    "614c2b5c747721550b27f048"
                ],
                "satHolidays": [
                    "1",
                    "2"
                ],
                "_id": "617264f1216eaa2388f4a5eb",
                "enteryTime": "09:00",
                "halfTime": "12:30"
            }
        ],
        "feeSchedules": [
            {
                "months": [
                    {
                        "label": "April",
                        "value": "4"
                    },
                    {
                        "label": "May",
                        "value": "5"
                    },
                    {
                        "label": "June",
                        "value": "6"
                    }
                ],
                "_id": "617264f1216eaa2388f4a5ea",
                "lastFeeDate": "2021-04-15"
            }
        ],
        "session": {
            "startsFromMonth": 4,
            "endsOnMonth": 3
        },
        "leaves": {
            "casual": 12,
            "sick": 6,
            "short": 6,
            "shortLeaveTime": 2
        },
        "termsExams": [
            {
                "classIds": [
                    "61802cc85a3e191abcc65cbc",
                    "61726edf699acc5f2c9393c1",
                    "61724b50e8511e02efcb11dd",
                    "61724b4be8511e02efcb11d4",
                    "614c2b7e747721550b27f04e",
                    "614c2b72747721550b27f04b",
                    "614c2b5c747721550b27f048"
                ],
                "_id": "617264f1216eaa2388f4a5ec",
                "term": "1"
            },
            {
                "classIds": [
                    "61802cc85a3e191abcc65cbc",
                    "61726edf699acc5f2c9393d1",
                    "61726edf699acc5f2c9393d0",
                    "614c2b72747721550b27f04b",
                    "614c2b5c747721550b27f048"
                ],
                "_id": "617264f1216eaa2388f4a5ed",
                "term": "2"
            },
            {
                "classIds": [
                    "61802cc85a3e191abcc65cbc",
                ],
                "_id": "617264f1216eaa2388f4a5ee",
                "term": "3"
            },
            {
                "classIds": [
                    "61802cc85a3e191abcc65cbc",
                    "61726edf699acc5f2c9393d1",
                ],
                "_id": "617264f1216eaa2388f4a5ef",
                "term": "4"
            }
        ]
    }
}`


### Contact Us for Mobile Appp : POST
URL : http://66.235.194.119:8089/api/edvantum/createcontact

BODY:`{
    name:"Mukesh sharma",
    mobile:"8988086334",
    message:"this is test record"
}`

RESPONSE:`{
    "success": true,
    "msg": "Record inserted successfully",
    "data": {
        "_id": "6190937345664d5e7ea4fe0f",
        "name": "Mukesh sharma",
        "email": "support@edvantum.com",
        "mobile": "8988086334",
        "message": "this is test record",
        "createdAt": "2021-11-14T04:41:23.431Z",
        "updatedAt": "2021-11-14T04:41:23.431Z",
        "__v": 0
    }
}`

### Support API : GET
URL:http://66.235.194.119:8089/api/edvantum/support

Response : `{
    "success": true,
    "data": {
        "_id": "619094e370bc574b1bc9205f",
        "email": "support@edvantum.com",
        "AppName": "Edvantum",
        "alternateEmail": "adminSupport@gmail.com",
        "alternateMobile": "8988090000",
        "address": "Mohali Punjab"
    }
}`

