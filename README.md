# End-to-End-DevOps-Project-Nodejs-Postgres
# Craete a new database :
create database postgres_db;
# Craete posts tables:
CREATE TABLE posts (
  id SERIAL PRIMARY KEY,
  title TEXT NOT NULL,
  body TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
# Insert data into poste table 
INSERT INTO posts (title, body) VALUES ('First Post','This is the first post');

INSERT INTO posts (title, body) VALUES ('Second Post','This the secon post');

INSERT INTO posts (title, body) VALUES ('Third Post','This is the third post');

# Dockerized the application 

docker build -t node-app-img .

docker run -d --name node-container -p 8000:8000 node-app-img

docker stop node-container

docker rm node-container

docker run -d --name node-container -p 8000:8000 --network host node-app-img

docker network create my-bridge-network

docker run -d --name node-container -p 8000:8000 --network my-bridge-network node-app-img

docker-compose up

