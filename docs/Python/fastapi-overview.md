# ⚡ FastAPI Overview

**FastAPI** is a modern, high-performance web framework for building APIs with Python, based on standard Python type hints.

- **Documentation:** [https://fastapi.tiangolo.com](https://fastapi.tiangolo.com)  

---

## **Local URLs**

- API: [http://127.0.0.1:8000](http://127.0.0.1:8000)
- Docs: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
- ReDoc: [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)

FastAPI automatically updates interactive documentation for new endpoints and models.

### **Swagger UI**
- **URL:** [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
- Fully interactive: send requests directly from the browser.
- Displays all endpoints, parameters, and models.
- “Try it out” button lets you test your API instantly.
- Ideal for **development** and quick debugging.

### **ReDoc**
- **URL:** [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)
- Cleaner, more static documentation layout.
- Auto-generated from the same OpenAPI spec.
- Focused on **readability** and API reference browsing.
- Ideal for **production docs** or sharing with external developers.

| Feature | Swagger UI | ReDoc |
|----------|-------------|-------|
| **Interactivity** | ✅ Yes (“Try it out” testing) | ❌ No |
| **Design Focus** | Developer tools and testing | Clean reference documentation |
| **Best Use** | Local development and debugging | Public-facing API documentation |
| **Auto Updates** | ✅ Automatically updates as endpoints change | ✅ Automatically updates as endpoints change |
| **Customization** | Moderate (via OpenAPI options) | High (CSS/theming possible) |

---


## HTTP Methods and Parameters: When to Use Each

### Path, Query, and JSON Body Parameters

- **Path Parameters**: Use these for identifying specific resources in the URL path. They are required and part of the endpoint structure, e.g., `/items/{item_id}` where `item_id` is a path parameter to specify which item to retrieve or modify.

- **Query Parameters**: Ideal for optional data, filtering, searching, or pagination. They appear after a `?` in the URL, e.g., `/items/?q=search&limit=10`. Use them when the data isn't essential for identifying the resource but helps customize the response.

- **JSON Body Parameters**: Use for sending structured data in requests like POST, PUT, or PATCH. They are defined using Pydantic models and are perfect for creating or updating resources with multiple fields, e.g., sending a JSON object to update an item's details.

### HTTP Methods: GET, PUT, PATCH, DELETE

- **GET**: Retrieve data from the server. It's idempotent and safe (no side effects). Use for fetching resources, e.g., `GET /items/{item_id}` to get a specific item.

- **PUT**: Update or create a resource entirely. It replaces the entire resource if it exists or creates a new one. Use when you need to update all fields of a resource, e.g., `PUT /items/{item_id}` with a full JSON body.

- **PATCH**: Perform a partial update on a resource. Only the provided fields are updated. Use when you want to modify specific parts without affecting the rest, e.g., `PATCH /items/{item_id}` to change just the price.

- **DELETE**: Remove a resource from the server. Use to delete items, e.g., `DELETE /items/{item_id}`. Be cautious as this action is irreversible.

Choose the appropriate method and parameter type based on your API's needs for clarity, efficiency, and RESTful conventions.
