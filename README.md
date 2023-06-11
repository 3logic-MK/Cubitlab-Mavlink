[![Build Status](https://github.com/mavlink/mavlink/workflows/Test%20and%20deploy/badge.svg)](https://github.com/mavlink/mavlink/actions?query=branch%3Amaster)

## MAVLink ##

MAVLink -- Micro Air Vehicle Message Marshalling Library.

MAVLink is a very lightweight, header-only message library for communication between drones and/or ground control stations. It consists primarily of message-set specifications for different systems ("dialects") defined in XML files, and Python tools that convert these into appropriate source code for [supported languages](https://mavlink.io/en/#supported_languages). There are additional Python scripts providing examples and utilities for working with MAVLink data.

> **Tip** MAVLink is very well suited for applications with very limited communication bandwidth. Its reference implementation in C is highly optimized for resource-constrained systems with limited RAM and flash memory. It is field-proven and deployed in many products where it serves as interoperability interface between components of different manufacturers.

Key Links:
* [Documentation/Website](https://mavlink.io/en/) (mavlink.io/en/)
* [Discussion/Support](https://mavlink.io/en/#support) (Slack)
* [Contributing](https://mavlink.io/en/contributing/contributing.html)
* [License](https://mavlink.io/en/#license)


## 3logic instruction ##

Scaricare il repository git ed effettuare il checkout della versione Cubitlab:  
```
git clone git@github.com:3logic-MK/Cubitlab-Mavlink.git --recursive  
git checkout cubitlab
```
### Generazione libreria per Python ###

Spostarsi nella cartella **message_definitions** e scegliere il template corretto:
```
cd message_definitions/v1.0
cp VERONTE.python.xml VERONTE.xml
```
modificare il file **common.xml** eliminando la riga:
```
<include>VERONTE.xml</include>
```
Tornare nella cartella principale ed utilizzare mavgen per generare la libreria contenente il dialetto:
```
python3 -m pymavlink.tools.mavgen --lang=Python --wire-protocol=2.0 --output=VERONTE.py message_definitions/v1.0/VERONTE.xml
```
Copiare la libreria VERONTE.py appena generata con mavgen nele cartelle pymavlink/dialects/v20 e pymavlink/dialects/v10
```
cp VERONTE.py pymavlink/dialects/v10
cp VERONTE.py pymavlink/dialects/v20
```
Utilizzare la cartella pymavlink appena creata all'interno dei propri progetti.  
  
  
  

### Generazione libreria per C/C++ ###

Spostarsi nella cartella **message_definitions**e  scegliere il template corretto:
```
cd message_definitions/v1.0
cp VERONTE.c.xml VERONTE.xml
```

to be completed...
