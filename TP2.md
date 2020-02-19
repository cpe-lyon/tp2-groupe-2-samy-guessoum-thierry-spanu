# TP2: Admin Système

## Exo 1: Variable

1. **printenv $PATH** ou **cho $PATH** --> affiche ou se trouve les commandes

2. **cd $HOME**-> ramène dans le répertoire personnel

3. 
   **LANG** --> spécifier la langue  au programme pour s'adapter à l'utilisateur.
   
   **PWD** --> variable qui spécifie le réperoire courant, afin de savoir ou l'on se trouve.
   
   **OLDPWD** --> variable qui spécifie le précédent répertoire courant ou l'on se trouvait.
   
   **SHELL** --> Contient ou se trouve les ressources nécéssaires pour le shell.
   
   **_** --> contient le dernier argument qui a été rentré. Si l'on écris cd .. --> ".." sera affiché.
   
4. **my_var="test"** puis **echo $my_var** , on crée puis on affiche la variable.

5. bash --> cette commande permet d'utiliser l'environnement bash. La variable **my_var** n'existe plus car cette variable est **local**.
   Pour quitter, il faut faire **exit**

6. **my_var**="test" --> on crée notre variable 

   **export my_var** on l'ajoute dans le .bashrc.
   
   **source ~/.bashrc** --> Elle devient variable environnement car on recharge le bashrc qui contient les variables.
   
   La variable est donc utilisable dans le bash.
   

7. **export NOMS="Samy Thierry"** --> on crée une variable d'environnement.

   **source ~/.bashrc** --> on charge le bashrc.
  
   **echo $NOMS** --> affiche bien nos deux noms. Donc c'est fonctionnel.
  
  
8. **echo "Bonjour à vous deux,"$NOMS** --> affiche biens la phrases avec nos deux prénoms.

9. **unset** --> permet de supprimer une variable. L'espace mémoire est donc libéré.
   
   Une variable vide occupe un espace mémoire, elle ne contient simplement rien.

10. **echo "\$HOME = "$HOME** --> **$HOME = /home/linux**

    "\" Permet d'afficher le nom de la variable et non son contenu.
    
## EXO 2: Contrôle de MDP

1.

