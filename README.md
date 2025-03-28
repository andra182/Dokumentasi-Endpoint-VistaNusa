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

---

## Endpoints

### 1. Get All Posts

**Endpoint:**

```
GET /posts
```

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

---

### 2. Get a Single Post

**Endpoint:**

```
GET /posts/{id}
```

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

---

### 3. Create a New Post

**Endpoint:**

```
POST /posts
```

**Headers:**

```
Content-Type: multipart/form-data
```

**Body (form-data):**

```
title: (string)
slug: (string)
user_id: (integer)
description: (string)
location: (string)
tags[]: (string, multiple values allowed)
content: (string)
thumbnail: (file)
```

**Response:**

```json
{
    "message": "Post created successfully",
    "post": {
        "id": 1,
        "title": "Sample Article",
        "slug": "sample-article-title",
        "user_id": 1,
        "thumbnail": "thumbnails/filename.jpg",
        "description": "This is a sample description for the article.",
        "location": "Sample Location",
        "tags": ["tag1", "tag2", "tag3"],
        "content": "This is the content of the sample article.",
        "created_at": "2025-03-28T09:46:06.000000Z",
        "updated_at": "2025-03-28T09:46:06.000000Z"
    }
}
```

---

