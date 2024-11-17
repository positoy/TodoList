## 개요

ToDo List 앱의 백엔드는 CRUD(생성, 조회, 업데이트, 삭제) 기능을 제공하는 RESTful API를 통해 데이터 관리를 지원합니다. 이 섹션에서는 각 엔드포인트와 그 동작을 설명합니다.

## Endpoints

### 1. List 관리

1. Create List

   - Method: POST
   - URL: /api/lists
   - Request Body:

     ```js
     {
         "name": "string"
     }
     ```

   - Response:

     ```js
     {
         "id": "string",
         "name": "string",
         "createdAt": "string"
     }
     ```

2. Retrieve Lists
   - Method: GET
   - URL: /api/lists
   - Response:
   ```js
   [
     {
       id: "string",
       name: "string",
       createdAt: "string",
     },
   ];
   ```
3. Delete List
   - Method: DELETE
   - URL: /api/lists/{id}
   - Response:
     ```js
     {
         "message": "List deleted successfully"
     }
     ```

### 2. ToDo 관리

1. Create ToDo

   - Method: POST
   - URL: /api/lists/{listId}/todos
   - Request Body:

     ```js
     {
        "title": "string",
        "description": "string",
        "status": "PENDING"
     }
     ```

   - Response:

     ```js
     {
         "id": "string",
         "listId": "string",
         "title": "string",
         "description": "string",
         "status": "PENDING",
         "createdAt": "string"
     }
     ```

2. Retrieve ToDos in List

   - Method: GET
   - URL: /api/lists/{listId}/todos
   - Response:

     ```js
     [
       {
         id: "string",
         listId: "string",
         title: "string",
         description: "string",
         status: "PENDING",
         createdAt: "string",
       },
     ];
     ```

3. Update ToDo Status

   - Method: PATCH
   - URL: /api/lists/{listId}/todos/{todoId}
   - Request Body:

     ```js
     {
         "status": "IN_PROGRESS" // or "DONE"
     }
     ```

   - Response:

     ```js
     {
         "id": "string",
         "listId": "string",
         "title": "string",
         "description": "string",
         "status": "IN_PROGRESS",
         "updatedAt": "string"
     }
     ```

4. Delete ToDo

   - Method: DELETE
   - URL: /api/lists/{listId}/todos/{todoId}
   - Response:

     ```js
     {
         "message": "ToDo deleted successfully"
     }
     ```

## 상태 코드

- 200 OK: 요청 성공.
- 201 Created: 새 자원이 성공적으로 생성됨.
- 400 Bad Request: 잘못된 요청 데이터.
- 404 Not Found: 리소스를 찾을 수 없음.
- 500 Internal Server Error: 서버 오류.
