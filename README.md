# MK Docs read me

## Setup on Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install --break-system-packages -r requirements.txt
```

## Start the server (defaults to port 8000)
```
mkdocs serve
mkdocs serve -a 0.0.0.0:8001
```

## After first setup, remember to start the venv
```bash
source .venv/bin/activate
deactivate
```

## Windows
```powershell
# create a virtual environment
python -m venv venv
# activate a virtual environment
.\venv\Scripts\Activate
# install requirements if not installed
pip install -r requirements.txt
# start the mkdocs server
mkdocs serve
# deactivate the virtual environment when done
deactivate
```
