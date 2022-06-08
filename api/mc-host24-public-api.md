# MC-HOST24 Public API

#### Authentication

Authentication to API Access

{% swagger method="post" path="" baseUrl="https://mc-host24.de/api/v1/token" summary="Get an API token" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {
    "api_token": "string"
  },
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://mc-host24.de/api/v1/logout" summary="Logout and invalidate the api token" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {},
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

#### Minecraft Server

Manage your Minecraftserver

{% swagger method="get" path="" baseUrl="https://mc-host24.de/api/v1/minecraftServer" summary="Get all minecraft server" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": [
    {
      "id": 0,
      "service_id": 0,
      "service_ordered_at": 0,
      "expire_at": 0,
      "expired_at": 0,
      "product_name": "string",
      "multicraft_id": 1,
      "address": "128.0.0.138",
      "memory": 1024,
      "online": true,
      "players_online": 5,
      "players_max": 10,
      "cpu_usage": 27,
      "mem_usage": 80
    }
  ],
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://mc-host24.de/api/v1/minecraftServer/ID/status" summary="Get the status of the minecraft server" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {
    "id": 0,
    "service_id": 0,
    "service_ordered_at": 0,
    "expire_at": 0,
    "expired_at": 0,
    "product_name": "string",
    "multicraft_id": 1,
    "address": "128.0.0.138",
    "memory": 1024,
    "online": true,
    "players_online": 5,
    "players_max": 10,
    "cpu_usage": 27,
    "mem_usage": 80
  },
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://mc-host24.de/api/v1/minecraftServer/ID/start" summary="Start the minecraft server" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {},
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://mc-host24.de/api/v1/minecraftServer/ID/stop" summary="Stop the Minecraft Server" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {},
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://mc-host24.de/api/v1/minecraftServer/ID/restart" summary="Restart the Minecraft Server" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {},
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://mc-host24.de/api/v1/minecraftServer/ID/backups" summary="List minecraft server backup" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {
    "status": "done",
    "time": "1624206633.5025601",
    "message": "string",
    "file": "world.zip",
    "ftp": "123.123.123.123:21",
    "type": "world"
  },
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://mc-host24.de/api/v1/minecraftServer/ID/backups" summary="Start new minecraft server backup" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {},
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

#### Teamspeak Server&#x20;

Manage your Teamspeakserver

{% swagger method="get" path="" baseUrl="https://mc-host24.de/api/v1/teamspeak" summary="Get all teamspeak server" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": [
    {
      "id": 0,
      "service_id": 0,
      "service_ordered_at": 0,
      "expire_at": 0,
      "expired_at": 0,
      "product_name": "string",
      "servername": "TeamSpeak3 Server by MC-Host24.de",
      "ip_address": "s03.ts3clan.de",
      "port": 9987,
      "slots": 100,
      "current_slots": 27,
      "online": true
    }
  ],
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="https://mc-host24.de/api/v1/teamspeak/ID/status" summary="Get teamspeak server status" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {
    "id": 0,
    "service_id": 0,
    "service_ordered_at": 0,
    "expire_at": 0,
    "expired_at": 0,
    "product_name": "string",
    "servername": "TeamSpeak3 Server by MC-Host24.de",
    "ip_address": "s03.ts3clan.de",
    "port": 9987,
    "slots": 100,
    "current_slots": 27,
    "online": true
  },
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://mc-host24.de/api/v1/teamspeak/ID/start" summary="Start teamspeak server" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {},
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://mc-host24.de/api/v1/teamspeak/ID/stop" summary="Stop teamspeak server" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {},
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="https://mc-host24.de/api/v1/teamspeak/ID/restart" summary="Restart teamspeak server" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {},
  "status": "SUCCESS",
  "meta": {
    "warnings": [
      "string"
    ],
    "errors": [
      "string"
    ],
    "success": [
      "string"
    ]
  },
  "success": true,
  "messages": [
    "string"
  ],
  "reload_datatables": false,
  "reload": false
}
```
{% endswagger-response %}
{% endswagger %}
