# PRÁCTICA 1 THINKDSP

En esta práctica comenzaremos creando señales para entender sus propiedades


## Comenzamos con la importación de la librería

```
import os

if not os.path.exists('thinkdsp.py'):
    !wget https://github.com/AllenDowney/ThinkDSP/raw/master/code/thinkdsp.py
    
    
VAMOS A GENERAR UNA SEÑAL

```
from thinkdsp import CosSignal, SinSignal

cos_sig = CosSignal(freq=440, amp=1.0, offset=0)
