# Simple Go Todo REST APP
RESTful API for simple todo application written in Go.

## Project structure
```
├── app
│   ├── app.go
│   ├── handlers     
│   │   ├── common.go
│   │   └── tasks.go
│   └── models
│       ├── sql
│       │   └── init.sql
│       ├── db.gp
│       └── todo.go
├── config
│   └── config.go
└── main.go
```

## Instalation

### Docker Compose
```
docker-compose up
```
Server should be running on `localhost:8000`, with hot reloading on.

### Locally
Download this project
```bash
go get github.com/senanito85/golang-todo
cd $GOPATH/src/github.com/senanito85/golang-todo
```

Install requirements using [glide](https://github.com/Masterminds/glide)
```
glide install
```

Create user and database
```bash
psql -c "CREATE USER tododb WITH PASSWORD 'tododb'"
psql -c "ALTER USER tododb CREATEDB"
psql -c "CREATE DATABASE tododb WITH OWNER tododb"
```

Run SQL to create tables and relations.
```bash
psql -Utododb -dtododb -h127.0.0.1 -f app/models/sql/*
```

Build and run
```bash
go build
./go-todo-app
```
Server should be running on `localhost:8000`.


## Usage

### Get request to list all

curl http://localhost:8000/todo 

### POST request to add new item

curl --header "Content-Type: application/json" --request POST  --data '{"title":"Go to gym","content":"Run for an hour"}' http://localhost:8000/todo/create

### Retrieve specific item

curl http://localhost:8000/todo/2




