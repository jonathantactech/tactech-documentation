# Creando ramas y realizando cambios
1. Hago un checkout desde release o master a una nueva rama
  - **git checkout -b <nueva rama>**
2. Realizar cambios necesarios(crear, editar, quitar archivos)
3. Realizar commit
  - **git commit -m “…”**
4. Realizar push
  - **git push**
5. Realizar un checkout desde la rama actual hacia “aux-test/<nueva rama(mismo nombre)>”
  - **git checkout -b aux-dev/<….>**
6. Estando en esta rama, tengo que hacer un merge origin:
  - **git merge origin/test**
7. Reparar conflictos si es que los hay
8. Pushear rama test
9. Luego de esto… listo, hay que hacer el PR
  - El PR lo deberán aprobar los CodeOwners(2 cuando es un pr a dev)
  - Una vez aprobado, tendrás que hacer un merge desde github(el boton verde)
  - Ahora en tu entorno local, ve a la rama test o dev, dependiendo del caso
  - **git checkout <test>**

# Deploy a test y/o producción
10. Ahora deberas realizar el calculo del diff
  - **git fetch gitlab**
  - **git log --pretty=format:'%Cred%h%Creset %C(magenta)%s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit gitlab/test...origin/test | grep 'Merge pull request'**
11. Informar por canal desplieges-svl la salida del diff
- Formato:
  *Deploy:* BFF
  *Env:* Test
  *PRs:*
  ```
  [CHANGE!]{hash} Merge pull request #{PR} from Wolox/{branch} ({time} ago) <{user}>
  ```
12. Ahora tienes que hacer:
  - **git push gitlab test:test (development:development) o git push gitlab master:master para prod** 

**OJO:**
**puede ser test o development(y al parecer solo el front usa development)**
**Si el repo usa development, entonces debe usar aux-dev**
