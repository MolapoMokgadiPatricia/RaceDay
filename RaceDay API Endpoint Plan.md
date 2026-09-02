### **RaceDay API Endpoint Plan**



###### **Authentication**



|HTTP Method|Route|<br />Description|<br />Role Required|Request Body|<br />Expected Response|
|-|-|-|-|-|-|
|POST|/api/auth/register|<br />Creates a new User account with either the Organiser or Participant role.|None|{ firstName, lastName, email, password, role, phoneNumber }|201 Created, <br />400 Bad Request, <br />409 Conflict|
|POST|/api/auth/login|Authenticates a User using email and password.|None|<br />{ email, password }|200 OK, 401 Unauthorized|





###### **User**



|<br />HTTP Method|Route|Description|<br />Role Required|Request Body|<br />Expected Response|
|-|-|-|-|-|-|
|GET|/api/users/me|Retrieves the logged-in user's information.|Any|<br />None|<br />200 OK, <br />401 Unauthorized|
|PUT|/api/users/me|Updates User details such as name and phone number.|Any|<br />{ firstName, lastName, phoneNumber }|200 OK, <br />400 Bad Request, 401 Unauthorized|





###### **Participant**



|HTTP Method|Route|<br />Description|Role Required|<br />Request Body|Expected Response|
|-|-|-|-|-|-|
|GET|/api/participants/me|<br />Retrieves the logged-in participant's profile.|Participant|None|<br />200 OK|
|PUT|/api/participants/me|Updates participant profile information.|Participant|<br />{ dateOfBirth, emergencyContactName, emergencyContactPhone, profilePictureUrl }|200 OK, <br />400 Bad Request|





##### **Organiser**



|HTTP Method|Route|Description|Role Required|Request Body|Expected Response|
|-|-|-|-|-|-|
|GET|/api/organisers/me|Retrieves the logged-in organiser's profile.|Organiser|None|200 OK|
|PUT|/api/organisers/me|Updates the organisation name.|Organiser|<br />{ organisationName }|200 OK, <br />400 Bad Request<br /><br />|





###### **Event**



|HTTP Method|Route|Description|Role Required|Request Body|Expected Response|
|-|-|-|-|-|-|
|GET|/api/events|Lists all events.|None|None|200 OK|
|GET|/api/events/{id}|Retrieves a specific event.|None|None|200 OK, 404 Not Found|
|POST|/api/events|<br />Creates a new event.|Organiser|{ name, description, eventDate, location, distanceKm, eventType, bannerImageUrl }|201 Created, 400 Bad Request, 403 Forbidden|
|PUT|<br />/api/events/{id|Updates an existing event.|Organiser|{ name, description, eventDate, location, distanceKm, eventType, bannerImageUrl }|200 OK, 403 Forbidden, 404 Not Found|
|DELETE|<br />/api/events/{id}|Deletes an event.|Organiser|None|204 No Content, 403 Forbidden, 404 Not Found|







###### **Category**



|HTTP Method|Route|Description|Role Required|Request Body|Expected Response|
|-|-|-|-|-|-|
|GET|/api/events/{eventId}/categories|Lists all categories for an event.|None|None|200 OK, 404 Not Found|
|POST|/api/events/{eventId}/categories|Creates a category for an event.|Organiser|{ name, minAge, maxAge, distanceKm }|201 Created, <br />403 Forbidden, 404 Not Found|
|PUT|<br />/api/categories/{id}|Updates a category.|Organiser|{ name, minAge, maxAge, distanceKm }|200 OK, <br />403 Forbidden, 404 Not Found|
|DELETE|/api/categories/{id}|<br />Deletes a category.|Organiser|None|204 No Content, 403 Forbidden, 404 Not Found|







###### **Enrolment**



|HTTP Method|Route|Description|Role Required|Request Body|Expected Response|
|-|-|-|-|-|-|
|POST|/api/events/{eventId}/enrolments|Enrols a participant into a selected category for an event.|Participant|{ categoryId }|201 Created,<br />400 Bad Request, 404 Not Found, 409 Conflict|
|GET|/api/events/{eventId}/enrolments|Lists all enrolments for an event.|Organiser|None|200 OK, <br />403 Forbidden|
|GET|/api/participants/me/enrolments|Displays the participant's enrolments.|Participant|None|<br />200 OK|
|PUT|/api/enrolments/{id}|Updates an enrolment status.|Organiser|{ status }|<br />200 OK, <br />403 Forbidden, 404 Not Found|





###### **Result**



|HTTP Method|Route|Description|Role Required|Request Body|Expected Response|
|-|-|-|-|-|-|
|POST|/api/enrolments/{enrolmentId}/result|Records a participant's finish time and finishing position.|Organiser|{ finishTime, finishPosition }|201 Created, <br />400 Bad Request, 403 Forbidden, 404 Not Found|
|GET|/api/results/{id}|<br />Retrieves a specific race result.|Any|None|200 OK, <br />404 Not Found|
|GET|<br />/api/participants/me/results|Displays the logged-in participant's race results.|Participant|<br />None|200 OK|



