# gestion_utilisateurs
#! /bin/bash
xls2csv list.xls > converted.csv 
input="/home/info/Documents/Embauche/converted.csv"
//localisation du fichier xls

array=($(awk -F : "{print $1}" /etc/passwd ))
i=0;
//droit aux groupes

while IFS=read -r line
do
         i=0
         for item in ${array[*]}
         do

                 if ["$line" = "\"$item\""]; then
                        i=$((i+1))

                 fi
           done
           if ["si" = 0]; then
                  useradd $line
                  user11 $line
            fi
done < "$input"
