# udacity-firebase-ios

Work through of Udacity Firebase Course by Google

## Friendly Chat App

* Real-time chat application

## Firebase

* [Firebase Pods](https://firebase.google.com/docs/ios/setup#available_pods)

### Firebase Database Security Rules

* Example of fine tuning access
Database values
```
{
 "chat": {
   "messages": {
     "-KS3PV-iwUZp5wkNq70s": {
       "name": "person1",
       "text": "hey!"
     },
     "-KS3PXhIhs8J_inrExy4": {
       "name": "person2",
       "text": "what’s up?"
     }
   }
 },
 "special_chat": {
   "messages": {
     "-KR-DwqtKzlWGxSn9P0y": {
       "name": "person1",
       "text": "Want to go to the movies?"
     },
     "-KR4tIpWmNn-EYxquSrw": {
       "name": "person3",
       "text": "Yeah! Let’s meet at 7."
     }
   }
 },
 "users": {
   "uid1": {
     "paid": true
   },
   "uid2": {
     "paid": false
   },
   "uid3": {
     "paid": true
   }
 }
}
```
Database security Rules
```
{
 "rules": {
   "chat" : {
     "messages" : {
       ".read": "auth != null",
       ".write": "auth != null"
     }
   },
   "special_chat" : {
     "messages": {
       ".read":
       "root.child('users').child(auth.uid).child('paid').val() === true",
       ".write":
       "root.child('users').child(auth.uid).child('paid').val() === true"
     }
   }
 }
}
```

* Validating input

`".validate": "newData.isString() && newData.val().length() < 100"`

Unlike .read and .write rules, data must adhere to all validation rules to be allowed.

* Further Reading: [Firebase Database Security](https://firebase.google.com/docs/database/security/)

### Firebase Authentication

* Further Reading: [Firebase UI: Authentication](https://github.com/firebase/FirebaseUI-iOS/tree/master/FirebaseAuthUI)
* Apple URL Schemes: [URL Schemes Apple Documentation](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html)
