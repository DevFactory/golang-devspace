# DevSpace for Go environment.

* Go v1.12.1


## Getting Started

1. First install DevSpaces client application, follow the instructions [here](https://support.devspaces.io/article/22-devspaces-client-installation) to do this.

2. Clone this repository locally

3. To create a DevSpace, open a terminal then navigate to the cloned repository directory and run following command
```bash
devspaces create
```
This will open a build status window and shows you the progress of DevSpace creation. Once build is successful validated starts.

4. Once validation is completed. Run `devspaces ls` command to see the list of DevSpaces and corresponding status. Newly created DevSpace `golang` will be in "**Stopped**" status.

5. To start your DevSpace run following command
```bash
devspaces start golang
```
You will receive a notification when your DevSpace is ready to be used.

6. To get inside your DevSpace, run following command
```bash
devspaces exec golang
```

## Run Demo fasthttp Application

1. From a new terminal, clone the demo application repository
```bash
git clone https://github.com/valyala/fasthttp.git
```

2. Navigate to cloned demo application directory
```bash
cd fasthttp
```

3. To synchronization code from your local machine to your DevSpace. Run following command
```bash
devspaces bind golang
```
This will synchronize files from your current working directory to your DevSpace. It might takes some time to complete, depending on the repository size.

4. Get inside your DevSpace by running following command
```bash
devspaces exec golang
```
5. Once you're inside DevSpace, you should be able see `fasthttp` project files under `/data` directory.

6. Build application
```bash
go get -t -v ./...
go build ./...
```

7.  Run Tests
```bash
go test -v ./...
```

8. Run application.
```bash
cd  examples/fileserver
go build fileserver.go
./fileserver -addr=0.0.0.0:80 -dir=./
```

Now application is running. To get the public URL exposed by DevSpace, run following command from your local terminal `devspaces info golang`. Command will output http URL which you can open in your browser to access the application.
