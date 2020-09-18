# gestion_utilisateurs
#! /bin/bash
# convertir  le fichier.xls en csv
xls2csv list.xls > converted.csv 
# chemin qui mene au fichier.xls
input="/home/info/Documents/Embauche/converted.csv"

# utiliser pour lister les utilisateur

array=($(awk -F : "{print $1}" /etc/passwd ))


# initialisation
i=0;

# lire la ligne

while IFS=read -r line
do
         i=0
         for item in ${array[*]}
         do

                 if ["$line" = "\"$item\""]; then
                        i=$((i+1))

                 fi
           done
           #comparer

           if ["si" = 0]; then
                  useradd $line
                  user11 $line
            fi
done < "$input"
