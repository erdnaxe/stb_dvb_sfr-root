## Root pour la Google TV de SFR

Si vous voulez rooter votre Google TV, vous pouvez d�s maintenant suivre ces instructions.

## Etape 1 : pr�paration d'une cl� USB et boot en recovery

T�l�chargez datroot-gtv-signed.zip et placez-le � la racine d'une cl� USB.

Ensuite il faut activer le mode d�veloppeur sur votre Google TV, activer le d�bogage USB.

R�cup�rez l'IP de la Google TV et connectez-vous dessus avec adb pour la red�marrer en recovery :
* adb connect <IP>
* adb reboot recovery

## Etape 2 : Flash

Naviguez dans les menus avec la t�l�commande :
* apply update from external storage
* selectionnez le fichier zip datroot-gtv-signed.zip
* laissez tourner puis la Google TV va red�marrer toute seule.

## Etape 3 : SuperSU

Il ne vous reste plus qu'installer SuperSu dans le Play Store.
Normalement vous devriez avoir une mise � jour du binaire su disponible, faites-l� pour v�rifier que le root est op�rationnel.
