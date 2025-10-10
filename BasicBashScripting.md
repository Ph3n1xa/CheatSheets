## 🏁 STRUCTURE DE BASE
**Utilité :** Squelette obligatoire pour que le script fonctionne
```Bash
#!/bin/bash                    # Shebang OBLIGATOIRE (ligne 1) - Dit quel interpréteur utiliser
# Commentaires avec #          # Documentation du code
# Exécution: chmod +x script.sh && ./script.sh
# Variables (PAS d'espaces autour du =)
variable="valeur"              # ✅ CORRECT - Stocker données
variable = "valeur"            # ❌ ERREUR (espaces interdits)
# Utilisation variables (avec $)
echo $variable                 # Afficher variable - Récupérer valeur stockée
echo ${variable}               # Forme explicite (recommandée) - Évite ambiguïtés
```
---
## 📥 ARGUMENTS & INPUT
**Utilité :** Récupérer données externes (utilisateur/commande) pour scripts flexibles
```Bash
# Arguments du script - Paramètres passés en ligne de commande
$0                             # Nom du script - Debug et messages d'erreur
$1, $2, $3                    # Arguments 1, 2, 3 - Données principales du script
$#                            # Nombre d'arguments - Validation input
$@                            # Tous arguments (array) - Traitement en boucle
$*                            # Tous arguments (string) - Logging/affichage
# Validation arguments - Éviter erreurs et guider utilisateur
if [ $# -eq 0 ]; then         # Si aucun argument
    echo "Usage: $0 <arg1> <arg2>"
    exit 1
fi
# Input utilisateur - Interactivité et saisie sécurisée
read -p "Entrez votre nom: " nom              # Prompt visible - Saisie normale
read -s -p "Mot de passe: " password          # Masqué (-s) - Sécurité
read -t 10 -p "Réponse rapide: " reponse      # Timeout 10s (-t) - Éviter blocage
```
---
## 🔤 VARIABLES & TYPES
**Utilité** **:** Stocker et manipuler données pour calculs et traitement
```Bash
# Variables simples - Stockage données de base
nom="John"                     # String - Texte et noms
age=25                        # Number - Calculs et comparaisons
active=true                   # Boolean - États et conditions
# Variables système - Informations dynamiques de l'environnement
user=$(whoami)                # Commande dans variable - Utilisateur actuel
date=$(date +%Y%m%d)          # Date formatée - Timestamping/logs
current_dir=$(pwd)            # Dossier actuel - Navigation/chemins
# Arrays (listes) - Stockage données multiples
fruits=("pomme" "banane" "orange")           # Déclaration - Listes de données
echo ${fruits[0]}                            # Premier élément (pomme) - Accès spécifique
echo ${fruits[@]}                            # Tous éléments - Traitement complet
echo ${\#fruits[@]}                           # Nombre éléments (3) - Comptage/validation
fruits+=("kiwi")                             # Ajouter élément - Extension dynamique
# Manipulation strings - Traitement et nettoyage texte
${variable\#pattern}            # Supprimer depuis début - Nettoyer préfixes
${variable%pattern}            # Supprimer depuis fin - Nettoyer suffixes
${variable/old/new}            # Remplacer première occurrence - Correction ponctuelle
${variable//old/new}           # Remplacer toutes occurrences - Nettoyage complet
${\#variable}                   # Longueur string - Validation taille
```
---
## ⚖️ CONDITIONS (IF/THEN/ELSE)
**Utilité** **:** Prendre décisions automatiques selon contexte/données
### 🚨 SYNTAXE CRITIQUE - ESPACES OBLIGATOIRES
```Bash
# ✅ CORRECT - Espaces autour des crochets - Syntaxe bash stricte
if [ condition ]; then
    # actions
elif [ autre_condition ]; then
    # autres actions
else
    # actions par défaut
fi
# ❌ ERREUR - Pas d'espaces - Cause erreurs parsing
if [condition]; then           # ERREUR
if [ condition]; then          # ERREUR
if [condition ]; then          # ERREUR
```
### 📊 TESTS DE FICHIERS
**Utilité** **:** Vérifier existence/permissions avant opérations (éviter erreurs)
```Bash
if [ -f "$file" ]; then        # Fichier existe - Traitement sécurisé
if [ -d "$dir" ]; then         # Dossier existe - Navigation sûre
if [ -r "$file" ]; then        # Lisible - Lecture autorisée
if [ -w "$file" ]; then        # Writable - Écriture autorisée
if [ -x "$file" ]; then        # Exécutable - Lancement autorisé
if [ -s "$file" ]; then        # Non vide - Contenu disponible
if [ -e "$path" ]; then        # Existe (fichier ou dossier) - Test générique
```
### 🔢 TESTS NUMÉRIQUES
**Utilité** **:** Comparaisons mathématiques pour logique métier
```Bash
if [ $num -eq 10 ]; then       # Égal (equal) - Valeur exacte
if [ $num -ne 10 ]; then       # Différent (not equal) - Exclusion
if [ $num -gt 10 ]; then       # Plus grand (greater than) - Seuils max
if [ $num -ge 10 ]; then       # Plus grand ou égal - Seuils inclusifs
if [ $num -lt 10 ]; then       # Plus petit (less than) - Seuils min
if [ $num -le 10 ]; then       # Plus petit ou égal - Limites inclusives
```
### 📝 TESTS STRINGS
**Utilité** **:** Validation et comparaison texte (passwords, statuts, etc.)
```Bash
if [ "$str" = "valeur" ]; then         # Égal (un seul =) - Correspondance exacte
if [ "$str" != "valeur" ]; then        # Différent - Exclusion valeurs
if [ -z "$str" ]; then                 # Vide (zero length) - Champs manquants
if [ -n "$str" ]; then                 # Non vide (not null) - Données présentes
# ⚠️ ATTENTION: Toujours entre guillemets pour éviter erreurs parsing!
if [ "$variable" = "test" ]; then      # ✅ CORRECT - Sécurisé
if [ $variable = "test" ]; then        # ❌ Peut causer erreurs si variable vide
```
### 🔗 CONDITIONS MULTIPLES
**Utilité** **:** Logique complexe et validation multi-critères
```Bash
# ET logique (&&) - Toutes conditions vraies
if [ $age -ge 18 ] && [ $age -le 65 ]; then
    echo "Âge de travail"
fi
# OU logique (||) - Une condition suffit
if [ "$status" = "actif" ] || [ "$status" = "en_attente" ]; then
    echo "Utilisateur valide"
fi
# Avec [[ ]] (recommandé pour conditions complexes) - Syntaxe moderne et lisible
if [[ $age -ge 18 && $age -le 65 ]]; then     # Plus lisible
    echo "Âge de travail"
fi
```
---
## 🔄 BOUCLES
**Utilité** **:** Automatiser tâches répétitives et traiter grandes quantités de données
### 🎯 FOR LOOPS
```Bash
# Range numérique - Séquences et compteurs
for i in {1..10}; do           # 1 à 10 - Itérations simples
    echo "Numéro: $i"
done
for i in {1..100..5}; do       # 1 à 100, pas de 5 - Échantillonnage
    echo $i                    # 1, 6, 11, 16... - Progression contrôlée
done
# Array/Liste - Traitement données structurées
fruits=("pomme" "banane" "orange")
for fruit in ${fruits[@]}; do
    echo "Fruit: $fruit"      # Parcours éléments - Traitement individuel
done
# Fichiers - Opérations sur ensembles de fichiers
for file in *.txt; do          # Tous fichiers .txt - Traitement par lots
    echo "Processing: $file"
done
# Style C (pour calculs) - Contrôle précis compteurs
for ((i=1; i<=10; i++)); do
    echo "Counter: $i"         # Mathématiques avancées
done
```
### ⏳ WHILE LOOPS
**Utilité :** Boucles conditionnelles et traitement continu
```Bash
# Tant que condition vraie - Logique métier dynamique
counter=1
while [ $counter -le 10 ]; do
    echo "Attempt: $counter"
    ((counter++))              # Incrémenter - Progression contrôlée
done
# Lecture fichier ligne par ligne - Parsing données volumineux
while IFS= read -r line; do
    echo "Ligne: $line"        # Traitement streaming - Économie mémoire
done < fichier.txt
# Boucle infinie (avec break) - Services et monitoring
while true; do
    read -p "Continuer? (y/n): " answer
    if [ "$answer" = "n" ]; then
        break                  # Sortir de la boucle - Contrôle utilisateur
    fi
done
```
### 🎯 CASE/SWITCH
**Utilité :** Menus et gestion multiple choix (plus lisible que if/elif)
```Bash
read -p "Choisissez (1-3): " choice
case $choice in
    1)
        echo "Option 1 choisie"
        ;;                     # Double point-virgule OBLIGATOIRE - Fin de cas
    2)
        echo "Option 2 choisie"
        ;;
    3)
        echo "Option 3 choisie"
        ;;
    *)                         # Default (tout le reste) - Gestion erreurs
        echo "Choix invalide"
        exit 1
        ;;
esac                          # case à l'envers pour fermer - Syntaxe bash
```
---
## ⚡ FONCTIONS
**Utilité :** Réutiliser code et organiser logique complexe
```Bash
# Définition fonction - Encapsulation et réutilisation
function ma_fonction() {
    local param1=$1            # Premier paramètre (local à la fonction) - Éviter conflits
    local param2=$2            # Deuxième paramètre - Portée limitée
    echo "Param1: $param1, Param2: $param2"
    return 0                   # Code de retour (0 = succès) - Gestion erreurs
}
# Alternative syntaxe (sans function) - Style moderne
ma_fonction() {
    local result=$(($1 + $2))   # Calcul local - Variables temporaires
    echo $result
}
# Appel fonction - Exécution avec paramètres
ma_fonction "hello" "world"    # Avec paramètres - Données d'entrée
result=$(ma_fonction 5 3)      # Capturer résultat - Récupération output
# Vérifier code retour - Gestion d'erreurs robuste
ma_fonction "test"
if [ $? -eq 0 ]; then         # $? = code retour dernière commande - Test succès
    echo "Fonction réussie"
fi
```
---
## 🔧 OPÉRATIONS & CALCULS
**Utilité :** Mathématiques et manipulations numériques
```Bash
# Arithmétique - Calculs de base
result=$((5 + 3))              # Addition - Sommes et totaux
result=$((10 - 2))             # Soustraction - Différences
result=$((4 * 5))              # Multiplication - Produits
result=$((20 / 4))             # Division - Quotients entiers
result=$((17 % 5))             # Modulo (reste: 2) - Tests parité/cycles
# Incrément/Décrément - Compteurs et progressions
((counter++))                  # counter = counter + 1 - Progression simple
((counter--))                  # counter = counter - 1 - Régression
((counter += 5))               # counter = counter + 5 - Bonds personnalisés
# Comparaisons dans calculs - Tests mathématiques optimisés
if ((counter > 10)); then      # Pas besoin de $ - Syntaxe directe
    echo "Counter supérieur à 10"
fi
```
---
## 📤 INPUT/OUTPUT & REDIRECTIONS
**Utilité :** Gestion flux données et logging
```Bash
# Output - Affichage et formatage
echo "Message"                 # Afficher avec newline - Messages simples
printf "Format: %s\n" "$var"   # Format contrôlé (sans newline auto) - Précision
# Redirections - Stockage et silence
command > file.txt             # Rediriger vers fichier (écrase) - Sauvegarde
command >> file.txt            # Rediriger vers fichier (ajoute) - Logging
command 2> error.log           # Erreurs vers fichier - Debug
command &> all.log             # Tout vers fichier - Logging complet
command > /dev/null 2>&1       # Silence total - Discrétion
# Pipes - Chaînage traitement données
cat file.txt | grep "pattern"  # Filtrage - Recherche dans flux
ps aux | grep nginx | wc -l    # Comptage - Statistiques
# Input depuis fichier - Lecture batch
while read line; do            # Lecture ligne par ligne - Traitement streaming
    echo $line
done < input.txt
```
---
