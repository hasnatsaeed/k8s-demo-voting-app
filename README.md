# k8s-demo-voting-app
A demo application for Kubernetes learning

## Run the app in Kubernetes ##

The folder ```k8s-demo-voting-app``` contains the yaml specifications of the Voting App's services.

Run the following command to create the deployments and services objects:
```

$ kubectl create -f k8s-demo-voting-app/
deployment "db" created
service "db" created
deployment "redis" created
service "redis" created
deployment "result" created
service "result" created
deployment "vote" created
service "vote" created
deployment "worker" created

```

The vote interface is then available on port 31000 on each host of the cluster, the result one is available on port 31001.

## Architecture ##

![architecture diagram](docs/architecture.png)

* A front-end web app in Python or ASP.NET Core which lets you vote between two options
* A Redis or NATS queue which collects new votes
* A .NET Core, Java or .NET Core 2.1 worker which consumes votes and stores them in…
* A Postgres or TiDB database backed by a Docker volume
* A Node.js or ASP.NET Core SignalR webapp which shows the results of the voting in real time

## Note ##

The voting application only accepts one vote per client. It does not register votes if a vote has already been submitted from a client.
