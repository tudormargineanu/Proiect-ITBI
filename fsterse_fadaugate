#!/bin/bash

grep "^-" $1 > vf_typescript_original.txt
grep "^-" $2 > vf_typescript_modificat.txt


echo -e "\033[31mFisiere sterse: \033[0m"
for fisier in $(awk '{print $9}' "vf_typescript_original.txt") ;
do
rezultat=$(grep -w "$fisier" vf_typescript_modificat.txt)
if [[ ! -n $rezultat ]]; then
echo -e "\033[32m$fisier\033[0m"
fi
done
echo "############################"

######################################

echo -e "\033[31mFisiere adaugate:\033[0m"
for fisier in $(awk '{print $9}' "vf_typescript_modificat.txt") ;
do
rezultat=$(grep -w "$fisier" vf_typescript_original.txt)
if [[ ! -n $rezultat ]]; then
echo -e "\033[32m$fisier\033[0m"
fi
done
echo "############################"
echo -e "\033[31mModificatii: \033[0m"
echo ""
######################################

for fisier in $(awk '{print $9}' "vf_typescript_original.txt") ;
do
aparitie_fisier=0
rezultat=$(grep -w "$fisier" vf_typescript_modificat.txt)
#adauga proprietatile fisierului nou in variabila rezultat
cuvinte_rezultat=($rezultat)

if [[ -n $rezultat ]]; then    
#verifica daca exista fisierul; daca variabila rezultat e goala sau nu

original=$(grep -w "$fisier" vf_typescript_original.txt)
#adauga proprietatile fisierului vechi in variabila original

c=0
for i in $original
do
if [[ $i != ${cuvinte_rezultat[$c]} ]]; then
if [[ $aparitie_fisier == 0 ]]; then
echo -e "\033[32m$fisier\033[0m"
echo ""
echo -ne "\033[33mmodificare \033[0m"
aparitie_fisier=1
fi
case "$c" in
0)
echo -e "\033[33mpermisiune din $i in ${cuvinte_rezultat[$c]}\033[0m" ;;
1)
echo -e "\033[33mnumar de linkuri din $i in ${cuvinte_rezultat[$c]}\033[0m" ;;
2)
echo -e "\033[33mproprietar fisier din $i in ${cuvinte_rezultat[$c]}\033[0m" ;;
3)
echo -e "\033[33mgrup fisierdin $i in ${cuvinte_rezultat[$c]}\033[0m" ;;
4)
echo -e "\033[33mdimensiune fisier din $i in ${cuvinte_rezultat[$c]}\033[0m" ;;
S*)
continue ;;
esac
fi
((c++))
done

fi
if [[ $aparitie_fisier == 1 ]]; then
echo "############################"
aparitie_fisier=0
fi
done

> vf_typescript_original.txt
> vf_typescript_modificat.txt
vftext=0
lin=2
for i in $(awk '{print $3}' typescript_original.txt) ;
do

if [[ ! "$i" =~ ^[0-9]+$ && $vftext == 1 ]]; then
break
fi
if [[ $vftext == 1 ]]; then
awk -v n=$lin 'NR==n {print $0}' typescript_original.txt >> vf_typescript_original.txt

fi
if [ $i = "Used" ]; then
vftext=1
fi
((lin++))
done
vftext=0
lin=2
for i in $(awk '{print $3}' typescript_modificat.txt) ;
do

if [[ ! "$i" =~ ^[0-9]+$ && $vftext == 1 ]]; then
break
fi
if [[ $vftext == 1 ]]; then
awk -v n=$lin 'NR==n {print $0}' typescript_modificat.txt >> vf_typescript_modificat.txt

fi
if [ $i = "Used" ]; then
vftext=1
fi
((lin++))
done


echo -e "\033[31mSpatiu: \033[0m"
i=1
while read -r linie; do
linie=($linie)
if [[ ${linie[2]} != $(awk -v n=$i 'NR==n {print $3}' vf_typescript_modificat.txt) ]]; then

echo -en "\033[32m${linie[0]}\033[0m si-a schimbat spatiul din \033[33m${linie[2]} KB\033[0m in \033[33m$(awk -v n=$i 'NR==n {print $3}' vf_typescript_modificat.txt) KB\033[0m "

echo -e "si au mai ramas \033[33m$(awk -v n=$i 'NR==n {print $4}' vf_typescript_modificat.txt) KB\033[0m in loc de \033[33m${linie[3]} KB\033[0m"
fi



((i++))
done < vf_typescript_original.txt
