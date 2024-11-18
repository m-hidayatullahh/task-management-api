# Task Management API

Task Management API adalah aplikasi backend untuk mengelola tugas. API ini mencakup fitur CRUD (Create, Read, Update, Delete) dengan filtering berdasarkan status dan tanggal jatuh tempo.

---

## Table of Contents
- [Features](#features)
- [Setup Instructions](#setup-instructions)
- [Database Configuration](#database-configuration)
- [Routes Overview](#routes-overview)
- [API Endpoints](#api-endpoints)
  - [POST /api/tasks](#post-apitasks)
  - [GET /api/tasks](#get-apitasks)
  - [GET /api/tasks/:id](#get-apitasksid)
  - [PUT /api/tasks/:id](#put-apitasksid)
  - [DELETE /api/tasks/:id](#delete-apitasksid)
- [Error Handling](#error-handling)
- [Future Improvements](#future-improvements)

---

## Features
- CRUD untuk tugas.
- Filtering berdasarkan status dan tanggal jatuh tempo.
- Validasi input menggunakan `express-validator`.
- Dukungan environment: development, test, dan production.

---

## Setup Instructions

### 1. Clone Repository
```bash
git clone https://github.com/m-hidayatullahh/task-management-api
cd task-management-api
```
### 2.  Install Dependencies
```bash
npm install
```

### 3.configure Database
```json
{
  "development": {
    "username": "root",
    "password": "your_password",
    "database": "db_name",
    "host": "127.0.0.1",
    "dialect": "mysql"
  }
}
```

### 4.Ru the server
```bash
node app.js
```

### 5.Routes Overview
| Route               | Method | Deskripsi                              |
|---------------------|--------|----------------------------------------|
| /api/tasks          | POST   | Membuat tugas baru                    |
| /api/tasks          | GET    | Mengambil daftar semua tugas           |
| /api/tasks?status&dueDate | GET    | Mengambil daftar tugas dengan filter   |
| /api/tasks/:id      | GET    | Mengambil detail tugas berdasarkan ID  |
| /api/tasks/:id      | PUT    | Memperbarui detail tugas               |
| /api/tasks/:id      | DELETE | Menghapus tugas berdasarkan ID         |


### 6.Api Endpoints
METHOD : POST
##### Request Body
```json
{
  "title": "Task title",
  "description": "Task description",
  "dueDate": "2024-12-01",
  "status": "pending"
}
```

##### Response (201)
```json
{
  "id": 1,
  "title": "Task title",
  "description": "Task description",
  "dueDate": "2024-12-01",
  "status": "pending",
  "createdAt": "2024-11-18T00:00:00.000Z",
  "updatedAt": "2024-11-18T00:00:00.000Z"
}
```
### GET /api/tasks
#### Method: GET
Deskripsi: Mengambil daftar semua tugas, mendukung filter berdasarkan status dan due date.

##### Query Parameters (opsional):
- status: pending, in progress, atau completed.

- Response (200)
```json
[
    {
        "id": 1,
        "title": "Task 1",
        "description": "Description for Task 1",
        "dueDate": "2024-12-01T00:00:00.000Z",
        "status": "pending",
        "createdAt": "2024-11-18T04:57:14.000Z",
        "updatedAt": "2024-11-18T04:57:14.000Z"
    },
    {
        "id": 2,
        "title": "Task 2",
        "description": "Description for Task 2",
        "dueDate": "2024-11-25T00:00:00.000Z",
        "status": "completed",
        "createdAt": "2024-11-18T04:57:14.000Z",
        "updatedAt": "2024-11-18T04:57:14.000Z"
    },
    {
        "id": 3,
        "title": "Task 3",
        "description": "Description for Task 3",
        "dueDate": "2024-11-30T00:00:00.000Z",
        "status": "in progress",
        "createdAt": "2024-11-18T04:57:14.000Z",
        "updatedAt": "2024-11-18T04:57:14.000Z"
    }
]
```

### GET /api/tasks/:id
Method: GET
Deskripsi: Mengambil detail task berdasarkan ID

- Response(200)
```json
{
  "id": 1,
  "title": "Task title",
  "description": "Task description",
  "dueDate": "2024-12-01",
  "status": "pending",
  "createdAt": "2024-11-18T00:00:00.000Z",
  "updatedAt": "2024-11-18T00:00:00.000Z"
}
```
-Response (404)
```json
{
  "error": "Task not found"
}
```

### PUT /api/task/:id
#### Method: PUT
Deskripsi : update task berdasarkan ID
```json
{
  "status": "completed"
}
```
-Response (200)
```json
{
  "id": 1,
  "title": "Task title",
  "description": "Task description",
  "dueDate": "2024-12-01",
  "status": "completed",
  "createdAt": "2024-11-18T00:00:00.000Z",
  "updatedAt": "2024-11-18T12:00:00.000Z"
}
```

### Delete /api/task/:id
#### Method: DELETE
Deskripsi: delete task berdasarkan ID
```json
{
  "message": "Task deleted successfully"
}
```
- Response (404)
```json
{
  "error": "Task not found"
}
```

### Error Handling
- 400: Data tidak valid 
- 404: Data tidak ditemukan
- 500: Kesalahan Server


### Future Improvements
- Tambahkan autentikasi menggunakan JWT.
- Tambahkan pagination pada GET /api/tasks.
- Dokumentasikan API menggunakan Swagger.



