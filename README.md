# API Documentation

## Overview

This API allows users to manage articles by performing CRUD (Create, Read, Update, Delete) operations. It supports file uploads and tagging.

## Base URL

```
http://yourdomain.com/api
```

## Authentication

All endpoints require authentication using a Bearer Token.

---

## User Endpoints

### 1. Get User by ID

**Endpoint:**

```
GET /users/{id}
```

**Response:**

```json
{
    "id": 1,
    "name": "John Doe",
    "email": "johndoe@example.com",
    "created_at": "2025-03-28T09:46:06.000000Z",
    "updated_at": "2025-03-28T09:46:06.000000Z"
}
```

**Error Response:**

```json
{
    "message": "User not found"
}
```

---

### 2. Create a New User

**Endpoint:**

```
POST /users
```

**Headers:**

```
Content-Type: application/json
```

**Body:**

```json
{
    "name": "John Doe",
    "email": "johndoe@example.com",
    "password": "securepassword"
}
```

**Response:**

```json
{
    "id": 1,
    "name": "John Doe",
    "email": "johndoe@example.com",
    "created_at": "2025-03-28T09:46:06.000000Z",
    "updated_at": "2025-03-28T09:46:06.000000Z"
}
```

### 3. Login

**Endpoint:**

```
POST /login
```

**Headers:**

```
Content-Type: application/json
```

**Body:**

```json
{
    "email": "johndoe@example.com",
    "password": "securepassword"
}
```

**Response:**

```json
{
    "token": "1|returnedbearertoken",
    "user": {
        "id": 1,
        "name": "John Doe",
        "email": "johndoe@gmail.com",
        "email_verified_at": null,
        "role": "user",
        "created_at": "2025-03-28T09:44:09.000000Z",
        "updated_at": "2025-03-28T09:44:09.000000Z"
    }
}
```

**Error Response:**

```json
{
    "message": "Invalid credentials"
}
```

---

## Articles API

### Get All Articles
**Endpoint:** `GET /api/articles`

**Response:**
```json
[
    {
        "id": 1,
        "title": "Sample Article",
        "user_id": 1,
        "slug": "sample-article-title",
        "thumbnail": "thumbnails/3X5JRGabEKM4T0EyM7nWffb09sjGNn1S3U4YvjHN.jpg",
        "description": "This is a sample description for the article.",
        "location": "Sample Location",
        "tags": ["tag1", "tag2", "tag3"],
        "content": "This is the content of the sample article.",
        "created_at": "2025-03-28T09:46:06.000000Z",
        "updated_at": "2025-03-28T09:46:06.000000Z"
    }
]
```

### Get Article by ID
**Endpoint:** `GET /api/articles/{id}`

**Response:**
```json
{
    "id": 1,
    "title": "Sample Article",
    "user_id": 1,
    "slug": "sample-article-title",
    "thumbnail": "thumbnails/3X5JRGabEKM4T0EyM7nWffb09sjGNn1S3U4YvjHN.jpg",
    "description": "This is a sample description for the article.",
    "location": "Sample Location",
    "tags": ["tag1", "tag2", "tag3"],
    "content": "This is the content of the sample article.",
    "created_at": "2025-03-28T09:46:06.000000Z",
    "updated_at": "2025-03-28T09:46:06.000000Z"
}
```

### Create Article
**Endpoint:** `POST /api/articles`

**Request (form-data):**
- `title`: string (required)
- `slug`: string (optional)
- `thumbnail`: file (optional)
- `description`: string (required)
- `location`: string (required)
- `tags[]`: array (optional)
- `content`: string (optional)

**Response:**
```json
{
    "id": 3,
    "title": "New Article",
    "user_id": 1,
    "slug": "new-article",
    "thumbnail": "thumbnails/example.jpg",
    "description": "New article description.",
    "location": "New Location",
    "tags": ["tagA", "tagB"],
    "content": "This is new article content.",
    "created_at": "2025-03-28T10:00:00.000000Z",
    "updated_at": "2025-03-28T10:00:00.000000Z"
}
```

### Update Article
**Endpoint:** `PUT /api/articles/{id}`

**Request (form-data):**
- `title`: string (optional)
- `user_id`: integer (optional)
- `slug`: string (optional)
- `thumbnail`: file (optional)
- `description`: string (optional)
- `location`: string (optional)
- `tags[]`: array (optional)
- `content`: string (optional)

**Response:**
```json
{
    "message": "Article updated successfully",
    "article": {
        "id": 1,
        "title": "Updated Article",
        "user_id": 1,
        "slug": "updated-article",
        "thumbnail": "thumbnails/updated.jpg",
        "description": "Updated article description.",
        "location": "Updated Location",
        "tags": ["tagX", "tagY"],
        "content": "This is updated article content.",
        "created_at": "2025-03-28T09:46:06.000000Z",
        "updated_at": "2025-03-28T11:00:00.000000Z"
    }
}
```

### Delete Article
**Endpoint:** `DELETE /api/articles/{id}`

**Response:**
```json
{
    "message": "Article deleted successfully"
}
```

---
