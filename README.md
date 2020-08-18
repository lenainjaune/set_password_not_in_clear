# set_password_not_in_clear
Permet de changer un mot de passe sans qu'il ne s'affiche sur le terminal

# Exemple changer mot de passe root sous MySQL
# basé sur : http://www.ihp.sinica.edu.tw/dashboard/docs/reset-mysql-password.html

<pre>
# Donner un nouveau mot de passe robuste à root de manière sécurisée (avec confirmation)
read -p "old pass:" -s op ; echo ; read -p "new pass:" -s np ; echo ; read -p "new pass again:" -s cp ; echo ; [ $np = $cp ] && ( set -o noglob ; mysqladmin --user=root --password="$op" password "$np" ; echo "password changed" ; np= ; set +o noglob ) || echo "E : Password mismatch !"
</pre>
Nota : np et cp doivent être des chaines de caractères identiques sinon il y a NON correspondance et on arrête le traitement, noglob sert à ne pas développer un éventuel caractère étoile dans le mot de passe, dans mysqladmin --password="$op" est le mdp actuel tandis que password "$np" est le nouveau mdp confirmé
