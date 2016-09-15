###My use rsync to ignore .git folder

    ```
    rsync --delete --exclude .git/ -a somefolder anotherfolder
    ```
