Profile
============

GET /profile/
-------------------------

Returns the profile stored for the current user.

Valid values for ``teamStatus`` are ``LOOKING_FOR_MEMBERS``, ``LOOKING_FOR_TEAM``, and ``NOT_LOOKING``.

Response format:
```
{
    "id": "github123456",
    "firstName": "John",
    "lastName": "Doe",
    "points": 2021,
    "timezone": "Americas UTC+8",
    "avatarUrl": "https://github.com/.../profile.jpg",
    "discord": "patrick#1234",
    "teamStatus": "LOOKING_FOR_TEAM",
    "description": "Lorem Ipsum…",
    "interests": ["C++", "Machine Learning"]
}

```

GET /profile/{id}/
-------------------------

Returns the profile stored for user that has the ID ``{id}``.

Response format:
```
{
    "id": "github123456",
    "firstName": "John",
    "lastName": "Doe",
    "points": 2021,
    "timezone": "Americas UTC+8",
    "avatarUrl": "https://github.com/.../profile.jpg",
    "discord": "patrick#1234",
    "teamStatus": "LOOKING_FOR_TEAM",
    "description": "Lorem Ipsum…",
    "interests": ["C++", "Machine Learning"]
}
```

GET /profile/list/
-------------------------

Returns all profiles that are in the database.

Response format:
```
{
    profiles: [
        {
            "id": "github123456",
            "firstName": "John",
            "lastName": "Doe",
            "points": 2021,
            "timezone": "Americas UTC+8",
            "avatarUrl": "https://github.com/.../profile.jpg",
            "discord": "patrick#1234",
            "teamStatus": "LOOKING_FOR_TEAM",
            "description": "Lorem Ipsum…",
            "interests": ["C++", "Machine Learning"]
        },
        {
            "id": "github123456",
            "firstName": "John",
            "lastName": "Doe",
            "points": 2021,
            "timezone": "Americas UTC+8",
            "avatarUrl": "https://github.com/.../profile.jpg",
            "discord": "patrick#1234",
            "teamStatus": "LOOKING_FOR_MEMBERS",
            "description": "Lorem Ipsum…",
            "interests": ["C++", "Machine Learning"]
        },
    ]
}
```


POST /profile/
-------------------

Creates a profile for the user with the `id` in the JWT token provided in the Authorization header.

Request format:
```
{
    "firstName": "John",
    "lastName": "Doe",
    "timezone": "Americas UTC+8",
    "avatarUrl": "https://github.com/.../profile.jpg",
    "discord": "patrick#1234",
    "teamStatus": "LOOKING_FOR_TEAM",
    "description": "Lorem Ipsum…",
    "interests": ["C++", "Machine Learning"]
}
```

Response format:
```
{
    "id": "github123456",
    "firstName": "John",
    "lastName": "Doe",
    "points": 2021,
    "timezone": "Americas UTC+8",
    "avatarUrl": "https://github.com/.../profile.jpg",
    "discord": "patrick#1234",
    "teamStatus": "LOOKING_FOR_TEAM",
    "description": "Lorem Ipsum…",
    "interests": ["C++", "Machine Learning"]
}
```

PUT /profile/
------------------

Updates the profile for the user with the `id` in the JWT token provided in the Authorization header.
This returns the updated profile information.

Request format:
```
{
    "firstName": "John",
    "lastName": "Doe",
    "timezone": "Americas UTC+8",
    "avatarUrl": "https://github.com/.../profile.jpg",
    "discord": "patrick#1234",
    "teamStatus": "LOOKING_FOR_TEAM",
    "description": "Lorem Ipsum…",
    "interests": ["C++", "Machine Learning"]
}
```

Response format:
```
{
    "id": "github123456",
    "firstName": "John",
    "lastName": "Doe",
    "points": 2021,
    "timezone": "Americas UTC+8",
    "avatarUrl": "https://github.com/.../profile.jpg",
    "discord": "patrick#1234",
    "teamStatus": "LOOKING_FOR_TEAM",
    "description": "Lorem Ipsum…",
    "interests": ["C++", "Machine Learning"]
}
```


DELETE /profile/
------------------

Deletes the profile for the user with the `id` in the JWT token provided in the Authorization header.
This returns the deleted profile information.

Response format:
```
{
    "id": "github123456",
    "firstName": "John",
    "lastName": "Doe",
    "points": 2021,
    "timezone": "Americas UTC+8",
    "avatarUrl": "https://github.com/.../profile.jpg",
    "discord": "patrick#1234",
    "teamStatus": "LOOKING_FOR_TEAM",
    "description": "Lorem Ipsum…",
    "interests": ["C++", "Machine Learning"]
}
```

GET /profile/leaderboard/?limit=
-------------------------

**Public endpoint.**

Returns a list of profiles sorted by points descending. If a ``limit`` parameter is provided, it will return the first ``limit`` profiles. Otherwise, it will return all of the profiles.

Response format:
```
{
    profiles: [
        {
            "id": "github123456",
            "firstName": "John",
            "lastName": "Doe",
            "points": 2021,
        },
        {
            "id": "github123456",
            "firstName": "John",
            "lastName": "Doe",
            "points": 2021,
        },
    ]
}
```

GET /profile/search/?teamStatus=value&interests=value,value,value&limit=value
-------------------------

Returns a list of profiles matching the filter conditions. 

``teamStatus`` is a string matching the user's team status. Valid values for ``teamStatus`` are ``LOOKING_FOR_MEMBERS``, ``LOOKING_FOR_TEAM``, and ``NOT_LOOKING``.

interests is a comma-separated string representing the user's interests.

- i.e if the user's interests are ["C++", "Machine Learning"], you can filter on this by sending ``interests="C++,Machine Learning"``

If a ``limit`` parameter is provided, it will return the first matching ``limit`` profiles. Otherwise, it will return all of the matched profiles.

Any users with the TeamStatus "NOT_LOOKING" will be removed.

Response format:
```
{
    profiles: [
        {
            "id": "github123456",
            "firstName": "John",
            "lastName": "Doe",
            "points": 2021,
            "timezone": "Americas UTC+8",
            "avatarUrl": "https://github.com/.../profile.jpg",
            "discord": "patrick#1234",
            "teamStatus": "LOOKING_FOR_TEAM",
            "description": "Lorem Ipsum…",
            "interests": ["C++", "Machine Learning"]
        },
        {
            "id": "github123456",
            "firstName": "John",
            "lastName": "Doe",
            "points": 2021,
            "timezone": "Americas UTC+8",
            "avatarUrl": "https://github.com/.../profile.jpg",
            "discord": "patrick#1234",
            "teamStatus": "LOOKING_FOR_TEAM",
            "description": "Lorem Ipsum…",
            "interests": ["C++", "Machine Learning"]
        },
    ]
}
```

GET /profile/filtered/?teamStatus=value&interests=value,value,value&limit=value
-------------------------

**Internal use only.**

Returns a list of profiles matching the filter conditions. 

teamStatus is a string matching the user's team status.

interests is a comma-separated string representing the user's interests.

- i.e if the user's interests are ["C++", "Machine Learning"], you can filter on this by sending ``interests="C++,Machine Learning"``

If a ``limit`` parameter is provided, it will return the first matching ``limit`` profiles. Otherwise, it will return all of the matched profiles.

Response format:
```
{
    profiles: [
        {
            "id": "github123456",
            "firstName": "John",
            "lastName": "Doe",
            "points": 2021,
            "timezone": "Americas UTC+8",
            "avatarUrl": "https://github.com/.../profile.jpg",
            "discord": "patrick#1234",
            "teamStatus": "LOOKING_FOR_TEAM",
            "description": "Lorem Ipsum…",
            "interests": ["C++", "Machine Learning"]
        },
        {
            "id": "github123456",
            "firstName": "John",
            "lastName": "Doe",
            "points": 2021,
            "timezone": "Americas UTC+8",
            "avatarUrl": "https://github.com/.../profile.jpg",
            "discord": "patrick#1234",
            "teamStatus": "NOT_LOOKING",
            "description": "Lorem Ipsum…",
            "interests": ["C++", "Machine Learning"]
        },
    ]
}
```

POST /profile/event/checkin/
----------------------------

Validates the status of an event that the user is trying to check into.
This is an internal endpoint hit during the checkin process (when the user posts a code to the event service).
The response is a status string, and throws an error (except the case when the user is already checked in).
In the case that the user has already been checked, status is set to "Event already redeemed" and a 200 status code is still used.

Request format:
```
{
    "id": "github123456",
    "eventID": "52fdfc072182654f163f5f0f9a621d72"
}

```


Response format:
```
{
    "status": "Success"
}
```

POST /profile/points/award/
----------------------------

Takes a struct with a profile and a certain number of points to increment their score by, and returns this profile upon completion.

Request format:
```
{
    "id": "github123456",
    "points": 10
}

```


Response format:
```
{
    "id": "github123456",
    "firstName": "John",
    "lastName": "Doe",
    "points": 2021,
    "timezone": "Americas UTC+8",
    "avatarUrl": "https://github.com/.../profile.jpg",
    "discord": "patrick#1234",
    "teamStatus": "LOOKING_FOR_TEAM",
    "description": "Lorem Ipsum…",
    "interests": ["C++", "Machine Learning"]
    "points": 10
}
```
