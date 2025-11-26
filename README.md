# Hello DevOps

* Készítette: Ludvány Marcell
* Neptun-kód: EV1LG9
* GitHub repo: https://github.com/Ludvi01/hello-devops

Egyszerű Node.js és Express alapú alkalmazás, amely HTTP-n elérhető, és egy rövid szöveget ad vissza.  
A projekt a feladatban előírt alap DevOps lépéseket mutatja be: build, verziókövetés trunk-based módszerrel, dockerizálás és devcontainer használata.


## Alkalmazás futtatása lokálisan

A projekt telepítése és indítása:
> npm install
> npm start

Az alkalmazás ezután a következő címen érhető el:
http://localhost:8080


## Build

A projekt nem igényel külön build folyamatot, de a feladatnak megfelelően szerepel egy build parancs:
> npm run build


## Docker használata

A Docker image elkészítése:
> docker build -t hello-devops:v1 .

A konténer futtatása:
> docker run -p 8080:8080 hello-devops:v1

A futó konténerben az alkalmazás a következő címen érhető el:
http://localhost:8080


## Docker image push (registry)

A projekt Docker image-e elérhető Docker Hub-on.
A push lépései:

A saját image tage-lése:
> docker tag hello-devops:v1 ludvi01/hello-devops:v1

Push a registrybe:
> docker push ludvi01/hello-devops:v1

Az image itt érhető el:
https://hub.docker.com/r/ludvi01/hello-devops


## Git – trunk-based development

A main branch szolgál trunkként.  
A fejlesztés külön rövid, önálló feature branchekben történt, például:
- feature/dockerize-app
- feature/devcontainer
- feature/readme

A módosítások minden esetben merge-elve lettek a main branchbe.


## Dev Container használata

A projekt tartalmaz egy .devcontainer konfigurációt, amely a gyökérben található Dockerfile-ra épül.

Használat VS Code-ban:
1. Nyisd meg a projektet VS Code-ban.
2. Parancspaletta: „Dev Containers: Reopen in Container”.
3. A konténerben a projekt telepítése és indítása:

> npm install
> npm start


A futó alkalmazás a host gépen továbbra is elérhető a http://localhost:8080 címen.
