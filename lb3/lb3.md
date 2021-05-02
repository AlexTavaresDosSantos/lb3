> M300 LB03 Dokuemntation - Arbeiten mit Docker - Levin Kuhn

# **Modul300 Dokumentation der LB03 Docker**


   
    
     
##### **Inhaltsverzeichnis**    

- [**Modul300 Dokumentation der LB03 Docker**](#modul300-dokumentation-der-lb03-docker)
- [**1 Einführung**](#1-einführung)
  - [**1.1 Einleitung**](#11-einleitung)
  - [**1.2 Befehle die bei der realisierung verwendet worden sind **](#12-Befehle die bei der realisierung verwendet worden sind)
 
- [**2 Code Dokumentation**](#2-code-dokumentation)
  - [**2.1 Dockerfile**](#)
  - [**2.2 Index Files der Webseiten**](#22-indexphp-file)
  - [**2.3 docker-compose.yml**](#23-docker-compose.yml)
 
- [**3 Erweiterungen**](#3-Erweiterungen)
- [**4 Sicherheit**](#4-Sicherheit)
- [**5 Final Test**](#5-Test hasen)
- [**6 Reflexion**](#6-Reflexion)
- [**7 Quellenverzeichnis**](#7-quellenverzeichnis)

---------------------



# **1 Einführung**  

## **1.1 Einleitung**

Im Rahmen des Moduls 300 müssen wir anhand von Docker ein Projekt umsetzen und dies dan abgeben. Ich habe für das Projekt 2 webseiten aufgestzt welche verwendet werden können um eine Offizielle Webseite bereit zu stellen und noch 1 um zum beispiel ein Intarnet zu Konfigurieren. Das ganze ist an eine MySQL angehängt und admire ist installiert worden. 

## **1.2 Befehle die bei der realisierung verwendet worden sind**

- **rmi** = *Image Löschen*
- **pull** = *Ein Repository ziehen*
- **ls** = *zeit den Inhalt eines Verzeichnis*
- **history** = *Letzte verwendete Images*
- **inspect** = *Zeigt die genau Spezifikationen eines Images*
- **kill** = *Stoppt Containner sofort*
- **create** = *Container aus einem Image erstellen*
- **build** = *erstellt ein Image*
- **start** = *mit docker start kann man ein Container starten*
- **run** = *erstellt ein Container und startet den*
- **ls**= *listet alle *LAUFENDEN* Container auf*
- **inspect** = *Detailierte Infos über Container*
- **logs** = *zeigt logs an*
- **stop** = *stoppt laufenden Container*

- **rm** = *löscht einen gestoppten container*

--------------------

# **2 Code Dokumentation**

## **2.1 Dockerfile**

 >*Mit dieser Zeile wird definiert welches image verwendet wurde*

    FROM php:7.4-apache

>*Hier werden extension installiert welche dem MySQL von nutzen sind*

    RUN  docker-php-ext-install mysqli



## **2.2 Index Files der Webseiten**

 >*Für die Hauptseite wurde folgendes html file mit folgendem inhalt erstellt. Dieses Index File kann aber beliebig angepasst werden.*

    <html>
    <head>
        <body>
            <h1>Hallo dies ist meine Webpage</h1>
        </body>
    </head>
    </html>
![Screenshots](./lb3/Screenshots/web.png)

>*Für die 2te Seite wurde folgendes html file mit folgendem inhalt erstellt. Dieses Index File kann aber beliebig angepasst werden.*

    <html>
    <head>
        <body>
            <h1>Hallo dies ist meine 2 Webseite</h1>
        </body>
    </head>
    </html>
![Screenshots](./lb3/Screenshots/web.png)
## **2.3 docker-compose.yml**
#### **2.3.3 Webseiten Konfiguration**

![Screenshots](./lb3/Screenshots/Webseitenconf.png)

Mit dem der **build** funktion kann man im docker-compose File definieren von welchem Image in diesem fall Dockerfile er das Image nehmen soll oder basierend auf welchem Dockerfile er den Image builden soll.
```
build:
        context: .
        dockerfile: Dockerfile
```
Mit dolgender Zeile definiert man den namen des Containers im Docker-compose file.
```
container_name: Webserver
```
Mit folgender Zeile definiert man die Ports
```
ports:
      - 81:80
```
Mit dieser Zeile Code kann mann seine gewünschte html Datei auf dem webserver anzeigen lassen.
```
volumes:
      - ./src:/var/www/html/
```
#### **2.3.4 Datenbank Konfiguration**  

![Screenshots](./lb3/Screenshots/DBconf.png)

Mit dieser Zeile definiert man im mysql container das root Password damit man anschliessen auf dem gewünschten definiert Port sich dan an der DB anmelden kann.
```
environment:
       MYSQL_ROOT_PASSWORD: tbz123.
```
Im gegensatz zur Webseite wird hier ein Image gepullt con mySQL dies definiert man folgender massen.
```
image: mysql
```
#### **2.3.5 Adminer Konfiguration**
 ![Screenshots](./lb3/Screenshots/adminerconf.png)
Hier wird einfach ein anderes Image verwendet
```
image: adminer
```
---------------------------

# **3 Erweiterungen**

Ich habe als erweiterung zu den Web diensten einen MySQL Container erstellt welche aber noch keine DB hat aus zeitlichen gründen nicht machbar gewesen.

---------------------------

# **4 Sicherheit**

Die DB ist mit einem Passwort versehen und so nicht leicht eindringbar.

---------------------------

# **5 Final Test**

| Test  | Beschreib     | Auswertung |
| ------- | ------------- | ---------- |
| 1       | docker-compose up -d funktioniert und alles container werden gestartet |   |
| 2       | MySQL ist über Port 8080 ereichbar und Anmeldung erfolgt mit "root" mit dem Passwort "tbz123." |        |
| 3       | Funktioniert die 2 webseite über den Port 81 | |



---------------------------

# **6 Reflexion**
Das Modul hat mir im grossen und ganzen spass gemacht. Ich konnte vieles dapei neu lernen und auch für die Zukunft einiges mit nehmen. Es ist angenehm wie viel man für dieses Modul machen muss man müsste meiner Meinung nach nur noch einwenig mehr auf Beispielen eingehen und uns nicht einfach loslassen auf Projekten. Dieses Modul sollte definitiv weiter ausgebaut werden den es hat noch luft nach oben was die 10 Tagen angeht. Ich bin aber im grossen und ganzen sehr zufrieden wie das Modul im endeffekt rausgekommen ist, ich hatte immer gute resultate und hoffe auch hier eine high mark zu erreichen. 


---------------------------

# **7 Quellenverzeichnis**
- <https://www.youtube.com/watch?v=ThpnqYpvnIM&t=649s>
- <https://www.php.net/manual/de/language.expressions.php>
- <https://hub.docker.com/>