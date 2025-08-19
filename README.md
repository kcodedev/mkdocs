# MK Docs read me

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install --break-system-packages -r requirements.txt
mkdocs serve
deactivate
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
