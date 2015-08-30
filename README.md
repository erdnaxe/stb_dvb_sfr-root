Root pour la Google TV de SFR
======

Si vous voulez rooter votre Google TV, vous pouvez dès maintenant suivre ces instructions.
Ce root consiste à flasher une update contenant le binaire de su,
ainsi qu'un script désactivant la réinstallation de la recovery (pour mettre un custom recovery).

## Etape 0 : Avertissement

Ce script a été testé sur ma propre Google TV par SFR, et marche très bien. Mais il se peut que sur votre Google TV par SFR, la configuration du stockage soit différent et mène ainsi à un brick lors du flash.

Ainsi, avant de flasher le zip, vérifiez que :
- Vous avez bien une **Google TV SFR-G8800**,
- Vous êtes bien sur la dernière mise à jour (4.2.2 build **JDQ39**, logiciel SFR.02412.07729),
- Vous avez une connexion stable wifi / ethernet et que votre PC et sur le même réseau (pour adb),

## Etape 1 : shell adb
Pour utiliser adb, il faut activer le mode développeur sur votre Google TV, puis activer le débogage USB.

Pour activer adb, vous avec besoin d'un terminal sur la Google TV. Vous pouvez installer celui-ci : [Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=fr).

Pour activer adb par le réseau, ouvrez un terminal sur Android et tapez : 
* setprop service.adb.tcp.port 5555
* stop adbd
* start adbd

Ensuite, connectez-vous avec un ordinateur dessus avec adb :
* adb connect <ip réseau>

Ensuite vérifier que "**adb shell mount**" contient bien "*/dev/block/mmcblk0p6 /system ext4 ro,relatime,data=ordered 0 0*".
Si le nombre après mmcblk0p change, alors NE FLASHER SURTOUT PÄS, car le script s'installerait alors autre pas que sur le système Android.

## Etape 1 : préparation d'une clé USB et boot en recovery

Téléchargez [datroot-gtv-signed.zip](datroot-gtv-signed.zip) et placez-le à la racine d'une clé USB.
Branchez cette clé USB sur le côté de la Google TV et exécuter : "**adb reboot recovery**"

## Etape 2 : Flash

Naviguez dans les menus avec la télécommande :
* Sélectionnez "*apply update from external storage*"
* Sélectionnez le fichier zip "datroot-gtv-signed.zip"
* La Google TV devrait redémarrer toute seule.

## Etape 3 : SuperSU

Il ne vous reste plus qu'installer [SuperSu](https://play.google.com/store/apps/details?id=eu.chainfire.supersu&hl=fr) dans le Play Store.
Normalement vous devriez avoir une mise à jour du binaire su disponible,
faites-là pour vérifier que le root est opérationnel.
