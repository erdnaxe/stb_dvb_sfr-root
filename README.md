Root pour le stb_dvb_sfr
======

Le stb_dvb_sfr, plus connu sous le nom de **décodeur Google Play de SFR** est une Google Tv qui est maintenant plus supportée.

# Informations

Ces informations peuvent être utiles pour un futur développement d'une rom (CyanogenMod...) sur le décodeur.

* [Table des partitions et leur contenu extrait des logs de la recovery](RECOVERY_FILESYSTEM_TABLE.md),
* [Accès à une partie du code source](http://opensource.lge.com/fileMgr/download/op/SZ930T-HF/5360) sous license opensource (ne sert à rien pour une custom rom).

# Root du décodeur

Si vous voulez rooter votre décodeur, vous pouvez dès maintenant suivre ces instructions.
Ce root consiste à flasher une update dans le recovery contenant le binaire de su,
et il désactive également la réinstallation de la recovery (pour mettre un custom recovery).

Vous aurez juste besoin d'un pc avec [ADB](http://forum.frandroid.com/topic/143999-tuto-installation-adb/).

## Credit

Je remercis le créateur de [ioroot](http://forum.xda-developers.com/showpost.php?p=48709232&postcount=869), qui a créé **datroot**, 
que j'ai très légèrement modifié pour fonctionner sur cet appareil.

## Etape 0 : Avertissement

Ce script a été testé sur mon propre décodeur, et marche très bien.
Mais il se peut que sur votre décodeur, la configuration du stockage soit différente et mène ainsi à un brick lors du flash.

Ainsi, avant de flasher le zip, vérifiez que :
* Vous avez bien une **Google TV SFR-G8800**, modèle SZ930T,
* Vous êtes bien sur la dernière mise à jour (4.2.2 build **JDQ39**, logiciel SFR.02412.07729),
* Vous avez une connexion stable wifi / ethernet et que votre PC et sur le même réseau (pour adb),

## Etape 1 : shell adb
Pour utiliser adb, il faut activer le mode développeur, puis activer le débogage USB dans les paramètres.

Vous avec besoin d'un terminal sur le décodeur pour configurer le serveur adb.
Vous pouvez installer celui-ci : [Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=fr).

Pour activer adb par le réseau, ouvrez un terminal sur Android et tapez : 
* setprop service.adb.tcp.port 5555
* stop adbd
* start adbd

Ensuite, connectez-vous avec un ordinateur dessus avec adb :
* adb connect <ip réseau>

Ensuite vérifier que "**adb shell mount**" contient bien :
```
/dev/block/mmcblk0p6 /system ext4 ro,relatime,data=ordered 0 0
```

Si le nombre après mmcblk0p change, alors **NE FLASHER SURTOUT PAS**,
car le script s'installerait alors autre pas que sur le système Android.

*En cas de brick, je ne suis pas responsable. Bla, bla... Mais sachez que si vous ne démarrez plus sur Android,
je ne connais aucune méthode pour retourner dans la recovery et flasher le firmware de base.*

## Etape 1 : préparation d'une clé USB et boot en recovery

Téléchargez [datroot-gtv-signed.zip](datroot-gtv-signed.zip) et placez-le à la racine d'une clé USB.
Branchez cette clé USB sur le côté de la Google TV et exécutez : "**adb reboot recovery**"

## Etape 2 : Flash

Naviguez dans les menus avec la télécommande :
* Sélectionnez "*apply update from external storage*"
* Sélectionnez le fichier zip "datroot-gtv-signed.zip"
* La Google TV devrait redémarrer toute seule.

## Etape 3 : SuperSU

Il ne vous reste plus qu'installer [SuperSu](https://play.google.com/store/apps/details?id=eu.chainfire.supersu&hl=fr) dans le Play Store.
Normalement vous devriez avoir une mise à jour du binaire su disponible,
faites-là pour vérifier que le root est opérationnel.
