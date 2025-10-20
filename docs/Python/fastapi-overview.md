# ⚡ FastAPI Overview

**FastAPI** is a modern, high-performance web framework for building APIs with Python, based on standard Python type hints.

- **Documentation:** [https://fastapi.tiangolo.com](https://fastapi.tiangolo.com)  
- **Source Code:** [https://github.com/fastapi/fastapi](https://github.com/fastapi/fastapi)

---

## 🧱 Core Dependencies

FastAPI is built on:

- **Starlette** — Web framework toolkit.  
- **Pydantic** — Data validation and settings management.

---

## 🧩 Example Application

**main.py**
```python
from typing import Union
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Hello": "World"}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}
```

### Run the Server
```bash
fastapi dev main.py
```

**Local URLs**

- API: [http://127.0.0.1:8000](http://127.0.0.1:8000)
- Docs: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
- ReDoc: [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)

---

## Example Upgrade – Add a Request Body

```python
from typing import Union
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class Item(BaseModel):
    name: str
    price: float
    is_offer: Union[bool, None] = None

@app.put("/items/{item_id}")
def update_item(item_id: int, item: Item):
    return {"item_name": item.name, "item_id": item_id}
```

FastAPI automatically updates interactive documentation for new endpoints and models.

---

## Interactive API Docs

FastAPI provides two built-in documentation interfaces powered by OpenAPI:

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

## 📦 Optional Dependencies

### Installed with `"fastapi[standard]"`

- **email-validator** — Email validation (Pydantic)  
- **httpx** — Testing client (Starlette)  
- **jinja2** — Templates (Starlette)  
- **python-multipart** — Form parsing  
- **uvicorn[standard]** — ASGI server  
- **fastapi-cli[standard]** — Command-line tools and deployment support

### Additional Optional Packages

- **pydantic-settings** — Settings management  
- **pydantic-extra-types** — Additional data types  
- **orjson** — Fast JSON responses  
- **ujson** — Ultra-fast JSON parsing

---

