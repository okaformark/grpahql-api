# Graphql-api

## A GraphQL API to query apps, events, and stages from a dataset

## This project uses Node for the query resolvers and the `apollograpql` explorer for testing.

### The queries, variables and all the corresponding responses for the API calls are shown below.

<br />

# To Use

### With npm:

Git clone and then  
` npm install`  
<br />
<br />

# API requirements

- List all apps
- query a single app
- list all the stages
- query a single stage
- search the stages by name
- list all of the events
- query a single event
- search the events by name
- list all of the events in an app
- list all the stages in an app
- get the stage in an event
- list the events at a stage

# Queries

```
query GetApps {
  apps {
    id
    name
  }
}

query GetApp($id:String){
  app (id: $id){
    id
    name
    appStages {
      id
      name
    }
  }
}

query GetStages{
  stages {
    id
    name

  }
}

query GetStageById($id:String){
  stageById(id:$id){
    id
    name
    stageEvents(id:$id) {
      name
      description
    }
  }
}
query GetStageByName($name:String){
  stageByName(name:$name){
    id
    name
  }
}
query GetEvents{
  events {
    id
    name
    description
    startsAt
    endsAt
    stageId
  }
}

query GetEventsById($eventId:String!){
  eventById(id:$eventId) {
    id
    name
    description
    startsAt
    endsAt
    stageId
    stage(id:$eventId) {
      id
      name
    }
  }
}

query GetEventsByName($eventName:String!){
  eventByName(name:$eventName) {
    id
    name
    description
    startsAt
    endsAt
  }
}

query GetEventsByDate($startDate: Date!, $endDate:Date!){
  eventByDate(startDate: $startDate,endDate: $endDate) {
    id
    name
    description
  }
}
query GetAllEventByAppId($appId:String){
  appEvents(appId: $appId) {
    id
    appId
    name
    description
  }
}

```

<br />

# Variables

```
{
  "id":"89be560f-6905-471a-8096-102e29a84e77",
  "name":"Tizzle Stage",
  "eventId":"b4781407-da92-475e-8d87-596aee0d7f2d",
  "eventName": "Drake",
  "startDate": 1577919600,
  "endDate": 1577923200,
  "appId": "b810bf6d-d81d-4104-bc1a-3b21d5154076",
  "createAppApp": {"name":"Country Music Fest"}
}
```

# Responses

```
{
  "data": {
    "apps": [
      {
        "id": "b810bf6d-d81d-4104-bc1a-3b21d5154076",
        "name": "HipHopFest 2020"
      }
    ]
  }
}

{
  "data": {
    "app": null
  }
}

{
  "data": {
    "stages": [
      {
        "id": "a4087686-ee6c-49d8-a4f0-d67f5931df3a",
        "name": "Rizzle Stage"
      },
      {
        "id": "89be560f-6905-471a-8096-102e29a84e77",
        "name": "Tizzle Stage"
      },
      {
        "id": "a6bb97dc-224c-4f8f-9af7-fd8b5731840f",
        "name": "Fo’shizzle Stage"
      }
    ]
  }
}


{
  "data": {
    "stageById": {
      "id": "89be560f-6905-471a-8096-102e29a84e77",
      "name": "Tizzle Stage",
      "stageEvents": [
        {
          "name": "Kendrick Lamar",
          "description": "Kendrick Lamar Duckworth is an American rapper and songwriter. Raised in Compton, California, Lamar embarked on his musical career as a teenager under the stage name K-Dot, releasing a mixtape that garnered local attention and led to his signing with indie record label Top Dawg Entertainment (TDE)"
        },
        {
          "name": "Future",
          "description": "Nayvadius DeMun Wilburn, known professionally as Future, is an American rapper, singer, songwriter, and record producer."
        }
      ]
    }
  }
}

{
  "data": {
    "stageById": {
      "id": "89be560f-6905-471a-8096-102e29a84e77",
      "name": "Tizzle Stage",
      "stageEvents": [
        {
          "name": "Kendrick Lamar",
          "description": "Kendrick Lamar Duckworth is an American rapper and songwriter. Raised in Compton, California, Lamar embarked on his musical career as a teenager under the stage name K-Dot, releasing a mixtape that garnered local attention and led to his signing with indie record label Top Dawg Entertainment (TDE)"
        },
        {
          "name": "Future",
          "description": "Nayvadius DeMun Wilburn, known professionally as Future, is an American rapper, singer, songwriter, and record producer."
        }
      ]
    }
  }
}


{
  "data": {
    "events": [
      {
        "id": "b4781407-da92-475e-8d87-596aee0d7f2d",
        "name": "Kanye West",
        "description": "Kanye Omari West is an American rapper, singer, songwriter, record producer, fashion designer, and entrepreneur.",
        "startsAt": 1577916000,
        "endsAt": 1577919600,
        "stageId": "a4087686-ee6c-49d8-a4f0-d67f5931df3a"
      },
      {
        "id": "b471f99a-0942-4e4f-be26-344fe5f7e88d",
        "name": "Drake",
        "description": "Aubrey Drake Graham is a Canadian rapper, singer, songwriter, record producer, actor, and entrepreneur. Drake initially gained recognition as an actor on the teen drama television series Degrassi: The Next Generation in the early 2000s.",
        "startsAt": 1577919600,
        "endsAt": 1577923200,
        "stageId": "a4087686-ee6c-49d8-a4f0-d67f5931df3a"
      },
      {
        "id": "0161c438-21ca-4112-a166-91cff2a3e1b3",
        "name": "Kendrick Lamar",
        "description": "Kendrick Lamar Duckworth is an American rapper and songwriter. Raised in Compton, California, Lamar embarked on his musical career as a teenager under the stage name K-Dot, releasing a mixtape that garnered local attention and led to his signing with indie record label Top Dawg Entertainment (TDE)",
        "startsAt": 1577916000,
        "endsAt": 1577919600,
        "stageId": "89be560f-6905-471a-8096-102e29a84e77"
      },
      {
        "id": "4867d1ca-cabe-485f-aef8-daac15c1f998",
        "name": "Future",
        "description": "Nayvadius DeMun Wilburn, known professionally as Future, is an American rapper, singer, songwriter, and record producer.",
        "startsAt": 1577919600,
        "endsAt": 1577923200,
        "stageId": "89be560f-6905-471a-8096-102e29a84e77"
      },
      {
        "id": "d4cec773-c287-4efe-aca5-4274accb6656",
        "name": "J. Cole",
        "description": "Jermaine Lamarr Cole, better known by his stage name J. Cole, is an American hip hop recording artist and record producer.",
        "startsAt": 1577923200,
        "endsAt": 1577930400,
        "stageId": "a6bb97dc-224c-4f8f-9af7-fd8b5731840f"
      }
    ]
  }
}


{
  "data": {
    "eventById": {
      "id": "b4781407-da92-475e-8d87-596aee0d7f2d",
      "name": "Kanye West",
      "description": "Kanye Omari West is an American rapper, singer, songwriter, record producer, fashion designer, and entrepreneur.",
      "startsAt": 1577916000,
      "endsAt": 1577919600,
      "stageId": "a4087686-ee6c-49d8-a4f0-d67f5931df3a",
      "stage": null
    }
  }
}


{
  "data": {
    "eventByName": {
      "id": "b471f99a-0942-4e4f-be26-344fe5f7e88d",
      "name": "Drake",
      "description": "Aubrey Drake Graham is a Canadian rapper, singer, songwriter, record producer, actor, and entrepreneur. Drake initially gained recognition as an actor on the teen drama television series Degrassi: The Next Generation in the early 2000s.",
      "startsAt": 1577919600,
      "endsAt": 1577923200
    }
  }
}


{
  "data": {
    "appEvents": [
      {
        "id": "b4781407-da92-475e-8d87-596aee0d7f2d",
        "appId": "b810bf6d-d81d-4104-bc1a-3b21d5154076",
        "name": "Kanye West",
        "description": "Kanye Omari West is an American rapper, singer, songwriter, record producer, fashion designer, and entrepreneur."
      },
      {
        "id": "b471f99a-0942-4e4f-be26-344fe5f7e88d",
        "appId": "b810bf6d-d81d-4104-bc1a-3b21d5154076",
        "name": "Drake",
        "description": "Aubrey Drake Graham is a Canadian rapper, singer, songwriter, record producer, actor, and entrepreneur. Drake initially gained recognition as an actor on the teen drama television series Degrassi: The Next Generation in the early 2000s."
      },
      {
        "id": "0161c438-21ca-4112-a166-91cff2a3e1b3",
        "appId": "b810bf6d-d81d-4104-bc1a-3b21d5154076",
        "name": "Kendrick Lamar",
        "description": "Kendrick Lamar Duckworth is an American rapper and songwriter. Raised in Compton, California, Lamar embarked on his musical career as a teenager under the stage name K-Dot, releasing a mixtape that garnered local attention and led to his signing with indie record label Top Dawg Entertainment (TDE)"
      },
      {
        "id": "4867d1ca-cabe-485f-aef8-daac15c1f998",
        "appId": "b810bf6d-d81d-4104-bc1a-3b21d5154076",
        "name": "Future",
        "description": "Nayvadius DeMun Wilburn, known professionally as Future, is an American rapper, singer, songwriter, and record producer."
      },
      {
        "id": "d4cec773-c287-4efe-aca5-4274accb6656",
        "appId": "b810bf6d-d81d-4104-bc1a-3b21d5154076",
        "name": "J. Cole",
        "description": "Jermaine Lamarr Cole, better known by his stage name J. Cole, is an American hip hop recording artist and record producer."
      }
    ]
  }
}



```
