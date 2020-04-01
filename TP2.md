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

Écrivez un script testpwd.sh qui demande de saisir un mot de passe et vérifie s’il correspond ou non au
contenu d’une variable PASSWORD dont le contenu est codé en dur dans le script. Le mot de passe saisi par
l’utilisateur ne doit pas s’afficher.

```bash

#!/bin/bash

PASSWORD="mdp"

read -sp "Entrer votre mot de passe :" mdp

if [ $mdp = $PASSWORD ]; then

echo "ok"

else

echo "nok"

fi

```

## EXO 3

Ecrivez un script qui prend un paramètre et utilise la fonction suivante pour vérifier que ce paramètre est un nombre réel :


```bash

#!/bin/bash

function is_number()
{

re='^[+-]?[0-9]+([.][0-9]+)?$'

if ! [[ $1 =~ $re ]] ; then

return 1

else

return 0

fi

}

is_number $1

if [ $? = 1 ]; then

echo "Error"

fi
```

## EXO 4

Écrivez un script qui vérifie l’existence d’un utilisateur dont le nom est donné en paramètre du script. Si le script est appelé sans nom d’utilisateur, il affiche le message : ”Utilisation : nom_du_script nom_utilisateur”,où nom_du_script est le nom de votre script récupéré automatiquement (si vous changez le nom de votre script, le message doit changer automatiquement)


```bash
#!/bin/bash

if [ -z "$1" ]; then

echo "Utilisation" $0 "nom_utilisateur"


else

test=$(grep $1 /etc/passwd)

if [ $? = 0 ]; then
echo "ok"

else

echo "nok"

fi

fi
```

## EXO 5

Écrivez un programme qui calcule la factorielle d’un entier naturel passé en paramètre (on supposera que l’utilisateur saisit toujours un entier naturel).

```bash

#!/bin/bash

i=1
final=1
for i in $(seq 1 $1); do

final=$(( $final * i ))


done

echo $final

```

## EXO 6 

Écrivez un script qui génère un nombre aléatoire entre 1 et 1000 et demande à l’utilisateur de le deviner. Le programme écrira ”C’est plus !”, ”C’est moins !” ou ”Gagné !” selon les cas (vous utiliserez $RANDOM).

```bash 

#!/bin/bash

nb_rand=$(( $RANDOM % 1000 + 1 ))

read -p "Entrer un nombre entre 1 et 1000 : " nb

while [ $nb != $nb_rand ]

do

	if [ $nb -gt $nb_rand ]; then

		echo "c'est moins !"
		read -p "Nouvelle prop : " nb

	else
		echo "c'est plus !"
		read -p "Nouvelle prop : " nb
	fi
done

echo "Bravo ! "

```

## EXO 7


1. Écrivez un script qui prend en paramètres trois entiers (entre -100 et +100) et affiche le min, le max et la moyenne. Vous pouvez réutiliser la fonction de l’exercice 3 pour vous assurer que les paramètres sont bien des entiers.
2. Généralisez le programme à un nombre quelconque de paramètres (pensez à SHIFT)


```bash

; Contributors : Maxence & Alexis Défossé 

#!/bin/bash

MIN=$1
MAX=$1
MOY=0
MEM=0

nb_val=$#

for i in $(seq 1 $#)
do
	
	if [[ $1 -gt 100 || $1 -lt "-100" ]]; then
		echo "Mauvais paramètre"
		exit 1
		
	else
	
	if [ $1 -lt $MIN ]; then
	
	MIN=$1;	

	elif [ $1 -gt $MAX ]; then
	
	MAX=$1;

	fi


	MEM=$(($MEM+$1))
	
	shift
	
	fi
	
done
	moy=$(($MEM/$nb_val))
	echo "Valeur moyenne: "$moy
	echo "Valeur max: "$MAX
	echo "Valeur min: "$MIN

```

3. Modifiez votre programme pour que les notes ne soient plus données en paramètres, mais saisies et
stockées au fur et à mesure dans un tableau

```bash

; Contributors : Maxence & Alexis Défossé 

#!/bin/bash


 
MIN=$1
MAX=$1
MOY=0
MEM=0
bool=1
 
nb_val=$1
 
for i in $(seq 1 $1);do
 
read -p "Choisissez une valeur:" var
 
    if [[ $var -gt 100 || $var -lt "-100" ]]; then
        echo "Mauvais paramètre"
        exit 1
       
    else
  
    if [ $var -lt $MIN ]; then
   
    MIN=$var;   
 
    else
   
    MAX=$var;
 
    fi
 
 
    MEM=$(($MEM+$var))
 
   
    shift
   
    fi
   
 
 
 
done
    moy=$(($MEM/$nb_val))
    echo "Valeur moyenne: "$moy
    echo "Valeur max: "$MAX
    echo "Valeur min: "$MIN

```
