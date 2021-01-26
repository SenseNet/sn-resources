# sensenet as a service configuration

## Repository service
In this section we list configurations available in the repository application. As the central service is also a repository, these settings generally apply to that application too.

### Connection strings

```json
"ConnectionStrings": {
 "SnCrMsSql": "sql.server.connection"
}
```

### Authentication service

```json
"sensenet": {
 "authentication": {
   "authority": "https://authority.url",
   "AddJwtCookie": true
 }
}
```

### Central host connection
For the client repository to work correctly, it has to access the central service. Without a central host, the repository can not be used. This section contains entries for the repository itself (self host) and authentication information for the central host.

```json
"snaasRepository": {
  "Central": {
    "selfHost": "client.repository.Url",
    "CentralHost": "central.repository.Url",
    "Authentication": {
      "ClientId": "centralClientId",
      "ClientSecret": "centralClientSecret"
    }
  }
}
```

### User activity monitor
In this section we can configure the behavior of the user activity monitor module that sends statistics to the central service.

> Please note these settings are different from the ones on the central service side. 

```json
"snaasRepository": {
  "UserActivityMonitor": {
    "RegisteringFrequencyInMinutes": 123
  }
}
```

### Usage limits
The system will control content creation and repository usage limits based on these settings.

```json
"snaasRepository": {
  "limits": {
    "maxFunctionRequestsPerSecond": 123,
    "maxActionRequestsPerSecond": 123,
    "maxPayloadInBytes": 123
  }
}
```

### Registration
You can customize the user type for new users and the groups they are assigned to by default.

```json
"sensenet": {
  "Registration": {
    "Groups": [],
    "UserType": ""
  }
}
```

### Taskmanager settings
Taskmanager service takes care of various long-running background tasks, e.g. generating preview images.

```json
"sensenet": {
  "TaskManagement": {
    "Url": "https://taskmanager.service.url",
    "ApplicationUrl": "https://client.repositry.url",
    "ApplicationId": "client.repositry.id"
  }
}
```

### Logger settings
As we use Serilog for logging, messages can be sent to various log targets, depending on the environment.

TThe easiest choice is the console, if it is accessible:

```json
"Serilog": {
  "WriteTo": [
    {
      "Name": "Console"
    }
  ],
  "Properties": {
    "Application": "SNaaS.Repository.Sql.TokenAuth",
    "Repository": "client.repository.id"
  }
}
```

It's not recommended for containers, but if other options are ruled out filesystem can be used:

```json
"Serilog": {
  "WriteTo": [
     {
      "Name": "File",
      "Args": { "path": "App_Data/path/to/log.file" }
    }  
  ],
  "Properties": {
    "Application": "SNaaS.Repository.Sql.TokenAuth",
    "Repository": "client.repository.id"
  }
}
```

The most flexible option (if the service is available) is Graylog:

```json
"Serilog": {
  "WriteTo": [
    {
      "Name": "Graylog",
      "Args": {
        "hostnameOrAddress": "graylog.service.url",
        "port": "12201",
        "transportType": "Udp"
      }
    }
  ],
  "Properties": {
    "Application": "SNaaS.Repository.Sql.TokenAuth",
    "Repository": "client.repository.id"
  }
}
```

### Content naming
It is recommended to avoid some characters when creating content. These characters can be set the following way:

```json
"sensenet": {
  "contentNaming": {
    "InvalidNameCharsPattern": "[\\$&\\+,/:;=?\"<>\\#%{}|^~\\[\\u005D''`\\*\t\r\n]"
  }
}
```

### Identity management
When a user is created the system will create it's profile counterpart, unless configured otherwise:

```json
"sensenet": {
  "identityManagement": {
    "UserProfilesEnabled": true,
    "DefaultDomain": "Public"
  }
}
```

### Email service
To be able to send email notifications an external smtp server is needed. This is how it can be configured:

```json
"sensenet": {
  "Email": {
    "Server": "smtp.server.url",
    "Port": 25,
    "FromAddress": "noreply@service.address",
    "SenderName": "Sender Name",
    "Username": "SmtpUser",
    "Password": "SmtPassword"
  }
}
```

## Central service
The following settings are related to the central service powering the SNaaS architecture. Most configuration options listed in the previous section are also available here.

### Notifications
Base domain of the administrative UI to be included in notification emails.

```json
"sensenet": {
  "SNaaS": {
      "Notification": {
        "AdminUIUrl": "https://admin.ui.url"
      } 
    }
}
```

### User activity monitor
In this section we can configure the behavior of the central user activity monitor module. 

> Please note these settings are different from the ones on the repository side. 

```json
"snaasRepository": {
  "UserActivityMonitor": {
    "InactivityPeriodInDays": 123
  }
}
```


## IdentityServer
The following settings are related to the authentication service powered by IdentityServer.

### Email service
> See in the previous section.

### External authentication providers
Users can log in using various external providers, like Google or GitHub.

```json
"sensenet": {
  "Authentication": {
    "ExternalProviders": {
      "GitHub": {
        "ClientId": "githubClientId",
        "ClientSecret": "githubClientSecret"
      }
    }
  }
}
```

### Notifications
Base domain of the administrative UI to be included in notification emails.

```json
"sensenet": {
  "SNaaS": {
      "Notification": {
        "AdminUIUrl": "https://admin.ui.url"
      } 
    }
}
```

### Login page customization
The authentication service uses the following settings for login and registration page customization:

```json
"sensenet": {
  "LoginPage": {
    "DisplayDemoSection": false,
    "DisplayOtherRepositoryButton": false,
    "DisplayRegistration": true,
    "DisplayRepositoryUrl": false,
    "LoginWelcomeText": "Log in to your sensenet account.",
    "RegistrationWelcomeText": "Get started by using your GitHub or Google account, or fill out the form.",
    "ForceAgreeTerms": true
  }
}
```

### Central service connection
In order to identify the allowed clients, the authentication service needs to connect to the central service. Without the correct information from the central host, the connecting repository can not be used.

```json
"sensenet": {
  "SNaaS": {
    "CentralUrl": "central.repository.Url",
    "SelfHost": "identity.server.Url",
    "Authentication": {
      "ClientId": "centralClientId",
      "ClientSecret": "centralClientSecret"
    }
  }
}
```

### Client type templates and custom clients
The different client type templates can be configured in this section. Some of the values will come from the central service but most of them are configured here.

```json
"sensenet": {
  "Clients": {
    "toolname": {
      "AllowedGrantTypes": [
        "hybrid",
        "client_credentials"
      ],
      "RequireConsent":  false,
      "ClientSecrets": [
        {
          "Value": "toolSecret"
        }
      ],
      "RedirectUris":  [
        "https://notused"
      ],
      "PostLogoutRedirectUris":  [
        "https://notused"
      ],
      "FrontChannelLogoutUri":  "https://notused",
      "AllowedScopes": [
        "sensenet"
      ],
      "AllowOfflineAccess":  true,
      "AlwaysIncludeUserClaimsInIdToken":  true,
      "AccessTokenLifetime":  600,
      "UserName": "domain\\username"
    }
  }
}
```