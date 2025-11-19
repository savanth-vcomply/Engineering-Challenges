# 📌 TaskHub - A Simple Task Management API Service

TaskHub is a simple lightweight task management backend service designed for small teams. It provides CRUD APIs for users to create, update, delete, and list the tasks. 





## 🚀 API List

- Create a task and assign it to a user
- Update task information 
- Delete a task
- Fetch all the tasks
- Fetch the particular task information


## 📚 Tech Stack

- *Backend*: Node.js
- *Database*: PSQL
- *Cache*: Redis
- *Auth*: JWT
- *Deployment*: Docker


## 📂 Folder Structure

```
task-hub/
├── src/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── services/
│   ├── tests/
│   └── server.js
├── Dockerfile
├── package.json
└── README.md
```


## ⚙️ Installation & Setup Instructions

### Prerequisites
- *[Node.js v18+](https://nodejs.org/en/download)*
- *[PSQL v14+](https://www.postgresql.org/download/)*
- *[Redis](https://redis.io/docs/latest/operate/oss_and_stack/install/archive/install-redis/)*
- *[Docker](https://docs.docker.com/engine/install/)*

### Setup
1. Clone the repository
```bash
git clone https://github.com/VComply/task-hub
```
2. Navigate to the repository
```bash
cd task-hub
```
3. Install dependencies
```bash
npm install
```
4. Create .env file 
```bash
touch .env
```
5. Update env variables (Reference)
```bash
APP_PORT=3000
PSQL_PORT=5432
PSQL_USER=<psql_user_name>
PSQL_PASSWORD=<psql_user_password>
PSQL_DB_NAME=<psql_db_name>
JWT_SECRET=<your_jwt_secret>
```
6. Run the server
```bash
npm run server.js
```


## 🔌 API Reference

#### 1. Create task

```http
  POST /api/v1/tasks
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `title` | `string` | **Required**. Task name |
| `description` | `string` | Optional |

#### 2. Get all tasks

```http
  GET /api/v1/tasks
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `limit` | `number` | **Optional**. Defaults to 10 |

#### 3. Get task details

```http
  GET /api/tasks/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `string` | **Required**. Id of task to fetch |

#### 4. Update task

```http
  PUT /api/v1/tasks
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `title` | `string` |  Task name |
| `description` | `string` | Task description|


#### 5. Delete task

```http
  DELETE /api/tasks/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `string` | **Required**. Id of task to delete |

## 🧪 Running Tests

To run tests, run the following command

```bash
  npm run test
```


## ❗ Troubleshooting

#### Facing an issue?

Check the logs using the below command 
```bash
tail -f *.log
```



## 🙌 Contributing

Contributions are always welcome!

👉 Please follow the below instructions

- Create a feature branch from main branch
- Commit your changes
- Submit a PR to main branch

