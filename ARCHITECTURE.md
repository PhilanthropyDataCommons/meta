# Architecture

The PDC is built using the following technologies:

| Component | Technology |
|-----------|------------|
| API ([service](https://github.com/PhilanthropyDataCommons/service)) | TypeScript (Node.js) |
| Authentication | [Keycloak](https://github.com/keycloak/keycloak/) |
| SDK Generation ([sdk](https://github.com/PhilanthropyDataCommons/sdk)) | Swagger Codegen |
| Document storage | S3 |
| Data storage | PostgreSQL |
| Client interfaces ([front end](https://github.com/PhilanthropyDataCommons/front-end)) | TypeScript (React) |

The PDC API provides the ability for third parties to read and write data using whatever technology they prefer.

## Diagrams

### Ecosystem Overview

This high level overview shows the general vision for the PDC as well as the types of clients and applications that might exist in the PDC ecosystem.

```mermaid
graph TD
    subgraph External Data
        External_Apis[Third Party / GMS APIs]
        External_Data[(Third Party / GMS Data Dumps)]
    end
    subgraph Clients
        Scrapers[[API Scrapers]]
        ETLs[[Data File ETL]]
        UX{{Philanthropy Data Commons Front End}}
        Integrations[[Integrated Third Parties]]
    end
    subgraph PDC Service
        API[Philanthropy Data Commons API]
        Database[(Data Store)]
        Filestore[(File Store)]
    end

    API<--->Database
    API<--->Filestore
    Scrapers--->API
    ETLs--->API
    UX<--->API
    Integrations<--->API
    External_Apis--->Scrapers
    External_Data--->ETLs
```

### Data Flow

```mermaid
flowchart LR
    subgraph service
        api[Node.js]
        database[PostgreSQL]
    end
	subgraph authentication
		auth[Keycloak]
	end
    subgraph frontend
        client[React]
    end
    client -- HTTP GET --> api
    api -- SQL Query --> database
    database -. Result Set .-> api
    api -. JSON .-> client
    client -- Auth Req --> auth
    auth -. Auth grant .-> client
```
