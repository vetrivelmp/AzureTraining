## Azure Cache for Redis

- What is Azure Cache for Redis?
- Redis Console Commands
```
set myNum 100
GET myNum
set myStr "Atin"
GET myStr
```
- Azure Cache for Redis - ASP.Net Core
  - Refer: 288-simple-strings
  - Update cache_connectionstring

- Azure Redis Cache - Data Invalidation
  - Use below code sample:
```
public void Save(string key, string value)
{
    var ts = TimeSpan.FromMinutes(_settings.CacheTimeout);
    _cache.StringSet(key, value, ts);
}
```

- Azure Redis Cache - StackExchange package
  - Refer - "289-sql-app"
  - Install Package - "StackExchange.Redis"
  - Update redis cache connection string in CourseService.cs
  - Create SQL Database and create Course table in it
```
CREATE TABLE Course
(
   CourseID int,
   CourseName varchar(1000),
   Rating numeric(2,1)
)
```

  - Insert Data
```
INSERT INTO Course(CourseID,CourseName,Rating) VALUES(1,'AZ-204 Developing Azure solutions',4.5)
INSERT INTO Course(CourseID,CourseName,Rating) VALUES(2,'AZ-303 Architecting Azure solutions',4.6)
INSERT INTO Course(CourseID,CourseName,Rating) VALUES(3,'DP-203 Azure Data Engineer',4.7)
```
  - Take connection string of SQL Database and update connection string in appsettings.json
```
{
"ConnectionStrings": {
  "SqlConnection": "Server=tcp:servercoursesapp.database.windows.net,1433;Initial Catalog=db1;Persist Security Info=False;User ID=atingupta2005;Password=Azure@123456;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;"
  }
}
```
  - Run the project locally
  - Publish project to Azure Web app
  - Update connection string in Web App
     - SQLConnection
     - Type: SQLAzure
