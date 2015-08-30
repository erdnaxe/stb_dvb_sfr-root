## Root pour la Google TV de SFR

Si vous voulez rooter votre Google TV, vous pouvez dès maintenant suivre ces instructions.

## Etape 1 : préparation d'une clé USB et boot en recovery

Téléchargez datroot-gtv-signed.zip et placez-le à la racine d'une clé USB.

Ensuite il faut activer le mode développeur sur votre Google TV, activer le débogage USB.

Récupérez l'IP de la Google TV et connectez-vous dessus avec adb pour la redémarrer en recovery :
* adb connect <IP>
* adb reboot recovery

## Etape 2 : Flash

Naviguez dans les menus avec la télécommande :
* apply update from external storage
* selectionnez le fichier zip datroot-gtv-signed.zip
* laissez tourner puis la Google TV va redémarrer toute seule.

## Etape 3 : SuperSU

Il ne vous reste plus qu'installer SuperSu dans le Play Store.
Normalement vous devriez avoir une mise à jour du binaire su disponible, faites-là pour vérifier que le root est opérationnel.
