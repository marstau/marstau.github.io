---
layout: post
title: Google Colab
category: 软件工具
tags: software
keywords: AI
description: 
---

## Use Open WebUI connect DeepSeek model[More](https://github.com/Axenide/Open-WebUI-Colab/blob/main/Open_WebUI.ipynb)

```
!sudo apt-get update
!sudo apt-get install -y python3.11 python3.11-venv python3.11-dev

# Create and activate a virtual environment using Python 3.11
!python3.11 -m venv venv
!source venv/bin/activate

# Upgrade pip within the virtual environment
!venv/bin/python -m pip install --upgrade pip

# Install Open WebUI within the virtual environment
!venv/bin/pip install open-webui

# Create a script to start both servers asynchronously and expose them using localtunnel
with open('start_servers.py', 'w') as f:
    f.write('''
import subprocess
import threading
import os
import time

def start_ollama():
    subprocess.run(['ollama', 'serve'], stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)

def start_open_webui():
    subprocess.run(['venv/bin/open-webui', 'serve', '--port', '8081'], stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)

# Start servers in separate threads
threading.Thread(target=start_ollama).start()
time.sleep(5)
threading.Thread(target=start_open_webui).start()
''')
```

```
# Execute the script
!venv/bin/python start_servers.py & sleep 20; echo | ssh -o StrictHostKeyChecking=no -p 443 -R0:localhost:8081 qr@a.pinggy.io
```

反应速度没有直接连colab快

## Reference

