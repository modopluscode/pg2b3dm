# pg2b3dm

Tool for converting from PostGIS to b3dm tiles. This software is a partial port of py3dtiles (https://github.com/Oslandia/py3dtiles) 
for generating b3dm tiles.

Differences to py3dtiles:

- 2* performance improvement;

- loading geometries in batches in memory instead of full datataset;

- fixed glTF warnings;

- add styling options;

- Docker support.

To run this tool there must be a PostGIS table available containing polyhedralsurface geometries.

## Command line options

```
 -H, --host        Required. Database host

  -D, --database    Required. Database name

  -c, --column      Required. Geometry column

  -t, --table       Required. Database table

  -u, --user        Required. Database user

  -p, --password    Required. Database password

  --help            Display this help screen.

  --version         Display version information.
  ```

## Run from Docker

Docker image: https://hub.docker.com/r/geodan/pg2b3dm

Building image:

```
$ docker build -t geodan/pg2b3dm .
```

Running image:

Sample on Windows: 

```
$ docker run -v C:/Users/bertt/tiles:/app/tiles -it geodan/pg2b3dm
```

Sample on Linux:

```
$ docker run -v $(pwd)/output:/app/output -it geodan/pg2b3dm -H my_host -u my_user -p my_password -D my_database -t my_table -c my_geometry_column
```

## Run from source

Requirement: Install .NET Core 2.2 SDK 

https://dotnet.microsoft.com/download/dotnet-core/2.2

```
$ git clone https://github.com/Geodan/pg2b3dm.git

$ cd src/pg2b3dm

$ dotnet build

$ dotnet run

```