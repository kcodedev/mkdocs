# MK Docs read me

## Setup

```bash
# first time set up
python3 -m venv .venv
source .venv/bin/activate
pip install --break-system-packages -r requirements.txt
mkdocs serve
```

```bash
# activate and deactivate venv
source .venv/bin/activate
deactivate
```

```bash
# Solving "OSError: [Errno 98] Address already in use"
lsof -i :8000
# Then kill the process using that port
kill 1234
```

```powershell
# create a virtual environment
python -m venv venv
# activate a virtual environment
.\.venv\Scripts\Activate
# install requirements if not installed
pip install -r requirements.txt
# start the mkdocs server
mkdocs serve
# deactivate the virtual environment when done
deactivate
```
