# **Comandos GitHub**

- **git init**: Se hace dentro de la carpeta repositorio de nuestro programa.

        $ git init
        Initialized empty Git repository in /.git/

- **git status**: Muestra el estado actual de nuestro proyecto.

        $ git status
       
    - Si falta actualizar algo:
    
            # Untracked files:
            # (use "git add <file>..." to include in what will be committed)
            # 
            # octocat.txt
            #  
            # nothing added to commit but untracked files present (use "git add" to track)

        octocat.txt aparece como untracked porque lo detecta como nuevo.
        
    - Despues de hacer el "git add" hacemos otro "git status":
    
            # On branch master
            #
            # Initial commit
            #
            # Changes to be committed:
            #   (use "git rm --cached <file>..." to unstage)
            #
            #	new file:   octocat.txt
              Success!
            
        Git dice que los cambios pueden ser "committed". Eso es porque los arquhivos añadidos estan en el Staging Area (área de prueba) pero no estan en nuestro repositorio.

- **git add < nombre_archivo >**: Indicamos a Git que comience a seguir de los cambios realizados en octocat.txt, primero debemos añadirlo a el Staging Area (área de prueba) mediante "git add".

        $ git add octocat.txt
        Nice job, you've added octocat.txt to the Staging Area
        
    - **git add -A .** : El punto representa todo lo que está dentro del directorio actual. El -A asegura que las eliminaciónes de archivos se incluyen.
    
    - **git add '*.txt'**: Podemos agregar todos los nuevos archivos usando un comodín con “git add” para agregas archivos de un tipo o con el mismo inicio del nombre. Importante usar las comillas 'Wildcard'. Revisar con "git status" si incluyo solo lo que queríamos o añadió más.

    - **git reset < nombre_archivo >**: Para eliminar un archivo o archivos desde el Staging Area (área de prueba).

- **git commit -m "Mensaje"**: Almacenar los cambios realizados, ejecutamos el comando "commit" con un mensaje que describe lo que hemos cambiado.

        $ git commit -m "Add cute octocat story"
        [master (root-commit) 20b5ccd] Add cute octocat story
        1 file changed, 1 insertion(+)
        create mode 100644 octocat.txt

    - **Staging Area**: Un lugar donde podemos agrupar archivos juntos antes de hacer el "commit" a Git.
    - **Commit**: Un "commit" es una instantánea de nuestro repositorio. De esta manera, si alguna vez necesitamos mirar hacia atrás en los cambios que hemos hecho (o si alguien más lo hace), veremos una bonita línea de tiempo de todos los cambios.
    
- **git log**: Es el registro de Git, recuerda todos los cambios (“Commits”) que hemos hecho hasta ahora, en el orden que hicimos “git commit”.

    - **git log --summary**: Muestra más información para cada "commit". Puede ver dónde se agregaron nuevos archivos por primera vez o dónde se eliminaron los archivos. Es una buena visión general de lo que está pasando en el proyecto.

- **git remote add origin < URL >**: Creamos un nuevo repositorio vacío de GitHub para enviar nuestro repositorio local al servidor GitHub (indicando donde está por la URL).

        $ git remote add origin https://github.com/try-git/try_git.git
        Success!
       
- **git push -u origin master**: El nombre de "remote" es "origin" y el nombre de la rama local ("local branch") predeterminada es "master". La opción "-u" le dice a Git que recuerde los parámetros, para que la próxima vez podamos simplemente ejecutar "git push" y Git sabrá qué hacer. Mirar "Check out Customizing Git - Git Hooks"

        $ git push -u origin master
        Branch master set up to track remote branch master from origin.
        Success!
        
- **git pull origin master**: Si el repositorio tiene cambios que no tenemos en local podemos hacer un "git pull" para comprobar si hay y descargar los cambios.


        $ git pull origin master
        Updating 3852b4d..3e70b0f
        Fast-forward
         yellow_octocat.txt |    1 +
         1 file changed, 1 insertion(+)
         create mode 100644 yellow_octocat.txt        
        Success!
    
    - **git stash**: En ocasiones antes de hacer un "git pull" puedes tener cambios que no les has hecho "commit" todavía. Una opción que tiene es almacenar los cambios utilizando el comando 'git stash' para ocultar sus cambios, y 'git stash apply' para volver a aplicar los cambios después de hacer "git pull".

- **git diff < etiqueta >**: Muestra las diferencias entre dos estados.
    - **git diff HEAD**: Sirve para echar un vistazo a lo que es diferente de nuestro último commit, por eso ponemos el puntero HEAD (HEAD es un puntero que mantiene la posición dentro de todos los commits diferentes. Por defecto apunta al commit más reciente)

            $ git diff HEAD
            diff --git a/octocat.txt b/octocat.txt
            index 7d8d808..e725ef6 100644
            --- a/octocat.txt
            +++ b/octocat.txt
            @@ -1 +1 @@
            -A Tale of Two Octocats
            +[mA Tale of Two Octocats and an Octodog        
            Success!
        
    - **git diff --staged**: Buscamos los cambios dentro de los archivos que ya se han añadido con "git add". Puede ser útil para antes de hacer un "git commit" para ver una visión general de los cambios y valorar si hacer un "commit" o hacer las modificaciones en varios.
    
            $ git diff --staged
            diff --git a/octofamily/octodog.txt b/octofamily/octodog.txt
            new file mode 100644
            index 0000000..cfbc74a
            --- /dev/null
            +++ b/octofamily/octodog.txt
            @@ -0,0 +1 @@
            +[mwoof
            Success!
            
- **git checkout -- < nombre_archivo >**: Los archivos se pueden cambiar de nuevo a cómo estaban en el último commit de nombre_archivo. Los "--" no son necesarios, pero es recomendable hacerlos porque si hay una rama (branch) con ese nombre seguirá funcionando.

        $ git checkout -- octocat.txt
        Success!
    
- **git branch < nombre_rama >**: Crea una copia del código a la que se le pueden hacer "commits" separados de la rama principal. Luego pueden fusionar esta rama con la rama principal.
        
        $ git branch clean_up
        Success!

    - **Branching (Derivación)**: Las ramas son lo que naturalmente sucede cuando se desea trabajar en múltiples funciones al mismo tiempo. Se separa el código en dos ramas y cuando estén listas se pueden fusionar la rama principal de nuevo y empujarlo (push) al servidor remoto.

- **git checkout < nombre_rama >**: Después de crear una rama tendremos dos ramas, una nombrada "master" y la nueva. Con este comando cambiamos de rama.

        $ git checkout clean_up
        Switched to branch 'clean_up'
        Success!

    - **git checkout -b < nombre_nueva_rama >**: Crea y accede a la rama en el mismo comando. Es lo mismo que hacer:

            $ git branch new_branch
            $ git checkout new_branch
            
- **git rm '*.txt'**:
que no sólo eliminará los archivos reales del disco, sino que también realizará la eliminación de los archivos para nosotros.

        $ git rm '*.txt'
        rm 'blue_octocat.txt'
        rm 'octocat.txt'
        rm 'octofamily/baby_octocat.txt'
        rm 'octofamily/momma_octocat.txt'
        rm 'red_octocat.txt'
        
        Success!
        
- **Unión de ramas**
    - Nos movemos a la rama principal:
    
            git checkout master
            
        git merge < rama_a_unir >
        
            $ git merge clean_up
            Updating 3852b4d..ec6888b
            Fast-forward
             blue_octocat.txt             |    1 -
             octocat.txt                  |    1 -
             octofamily/baby_octocat.txt  |    1 -
             octofamily/momma_octocat.txt |    1 -
             red_octocat.txt              |    1 -
             5 files changed, 5 deletions(-)
             delete mode 100644 blue_octocat.txt
             delete mode 100644 octocat.txt
             delete mode 100644 octofamily/baby_octocat.txt
             delete mode 100644 octofamily/momma_octocat.txt
             delete mode 100644 red_octocat.txt
            
            Success!
           
        Eliminar rama unida:
        
            git branch -d clean_up
            
        Esta función solo se puede eliminar ramas que se han fusionado. Si se quiere eliminar una rama porque se desecho la idea habra que añadir -f para forzar la eliminación o emplear -D que convina -d y -f en un solo comando.
        
            git branch -D clean_up

        Solo falta hacer el push            
                
            git push
            

