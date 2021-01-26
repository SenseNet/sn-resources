# sensenet repository

# Central host connection

In order to the client repository can be identified, it needs to be connected to the central from where client informations can be gathered. Without central host, the repository can not be used.

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

# Taskmanager settings

Taskmanager service takes care for various tasks, e.g. generating preview.

```json
"sensenet": {
        "TaskManagement": {
          "Url": "https://taskmanager.service.url",
          "ApplicationUrl": "https://client.repositry.url",
          "ApplicationId": "client.repositry.id"
        }
      }
```

# Logger settings

The system can use various output for it's logs.

Easiest choice is console, if it is accessible:

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

It's not recommended for containers, but if other options are ruled out and filesystem can be used:

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

Flexible option if the service is available, the Graylog:

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

# Invalid characters for content naming

It's recommended to avoid some characters with content creation, these characters are can be set with:

```json
  "sensenet": {
      "contentNaming": {
        "InvalidNameCharsPattern": "[\\$&\\+,/:;=?\"<>\\#%{}|^~\\[\\u005D''`\\*\t\r\n]"
      }
    }
```

# Identity management

When a user is created the system will create it's profile counterpart, unless otherwise is set:

```json
"sensenet": {
      "identityManagement": {
        "UserProfilesEnabled": true,
        "DefaultDomain": "Public"
      }
    }
```

# Email service

To be able to send email notifications an external smtp server is needed. It's how it can be configured:

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


# identity server

# external authentication providers

Sensenet authentication can be made via external services, such as github...

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

# domain used with notifications

Base domain to be used notifications for administraion page.

```json
"sensenet": {
        "RegistrationNotification": {
            "AdminUIUrl": "https://admin.ui.url"
        }
      }
```

# login page customization

Administration page use the following settings for login customization:

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

# Central host connection

In order to the client repository can be identified, the identiti server needs to be connected to the central from where client informations can be gathered. Without central host, the repository can not be used.

```json
"sensenet": {
        "SNaaS": {
          "CentralHost": "central.repository.Url",
          "SelfHost": "identity.server.Url",
          "Authentication": {
            "ClientId": "centralClientId",
            "ClientSecret": "centralClientSecret"
          }
        }
      }
```

# custom client secret settings

Client application have to use a client secret that is configured with the repository.
(may be obsolate)

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