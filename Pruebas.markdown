Entrar al github en consola:

    ssh -T git@github.com
    
Configurarar proyecto:

    git config --global user.name "Firstname Lastname"
    
    git config --global user.email "your_email@youremail.com"
    
Movernos al directorio donde tenemos el proyecto con cd

Dentro de la carpeta poner:
    
    git init

Añadimos todo (Mejor archivo a archivo):
    git add . 

Creamos el primer comit

    git commit -m "Instruccions basicas Git"
  
Cramos un repositorio dentro de Github

Conectar nuestro repositorio local con el github.
    git remote add origin <url>
    
Realizamos un push
    
    git push origin master


Primer uso de Git Bash

1. **git init**: Todo lo que se escriba dentro de la carpeta va a estar dentro del .git. Allí va el historial de versiones y está oculto dentro de la carpeta. Solo se ejecuta una vez.

2. **git add**: Lleva el control de los archivos que se agregan luego de escribir ese comando.
    - **git add .** : Es para todo agregar pero no es recomendable.

3. **git commit**: Comando que indica que esta lista alguna funcionalidad para que sea una versión del código.

4. **git commit — m “Mi primer commit”**: Se repite n veces cada vez se cambia el código. Se tiene que detallar muy bien lo que se pone en el comentario es una buena práctica para que nuestro equipo colaborativo nos pueda entender y solucionar errores en caso sucediera.
    Cuando coinciden las líneas entre una persona y la otra pueden ocurrir conflictos.

5. **Push**: Básicamente lo que realiza un push es publicar lo que se encuentra en nuestro servidor local y llevarlo al servidor remoto de Github

6. **Pull**: Trae los cambios de nuestro repositorio remoto y los actualiza al repositorio local.

5. git remote add origin [URL DEL REPOSITORIO EN GITHUB]

6. git push origin master : Es el nombre que se le pone al repositorio remoto al que se conecta.



##Fuentes:
- https://github.com/Hispano/Guia-sobre-Git-Github-y-Metodologia-de-Desarrollo-de-Software-usando-Git-y-Github
- https://guides.github.com/activities/hello-world/#what
- https://medium.com/@sthefany/primeros-pasos-con-github-7d5e0769158c
- https://try.github.io/levels/1/challenges/13

Ignorar archivos:
- http://aprendegit.com/ignorando-ficheros-en-git-parte-i-formas-de-ignorar-ficheros/