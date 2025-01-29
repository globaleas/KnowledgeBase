# Central Alert Repository

CAR, otherwise known as the Central Alert Repository, is a service which syndicates emergency alert information from
various sources, such as EAS_NET participant stations.

## Installation

<warning>
    Developer access to the GWES Internal GitLab is required to perform these instructions. These are being publicized
    simply for reference purposes.
</warning>

<tip>
    You may need to trust the ASP.NET developer certificate to allow the website to start up correctly.
</tip>

### Prerequisites

In order to deploy a development instance of CAR, you will need to install a few prerequisite packages and services.

* .NET 8.0 SDK
* NodeJS and NPM
* MariaDB

Additionally, to enable audio transcoding support (converting source WAV files to MP3), you will need to install the
following packages:

* FFMpeg
* `libgdiplus` (on linux systems only)

### Bare-metal Installation

1. Clone the CAR repository from the GWES GitLab
    * `$ git clone https://gitlab.example/gwes/car.git`
    * `$ cd ./car/`
2. Restore all projects in the solution
    * `$ dotnet restore`
3. Build all projects in the solution
    * `$ dotnet build -c Debug --no-restore [--self-contained]`
        * You can optionally publish the projects into single-file binaries by using `dotnet publish` instead.
4. Configure the MariaDB database
    * Create a new database called `car`
    * Create a user in the database called `root` with a secure password.
        * You must ensure that `root` has superuser permissions in the `car` database.
        * You must update the environment variables to reflect the set database password.
5. Spin up the worker host and website
    * `dotnet ./CAR.WorkerHost/bin/Debug/net8.0/(platform)-x64[/publish]/GWES.CAR.WorkerHost.dll`
        * The worker host will be responsible for migrating the database on startup, which is why it needs to be started
          *before* the website.
    * `dotnet ./CAR.Website/bin/Debug/net8.0/(platform)-x64[/publish]/GWES.CAR.Website.dll`
6. Navigate to `https://localhost:7220` to ensure the website is working correctly.
7. Place an EAS_NET formatted file in the polling directory provided by the worker host to ensure that alert ingest is
   working correctly.

