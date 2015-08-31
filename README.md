Root pour le stb_dvb_sfr
======

Le stb_dvb_sfr, plus connu sous le nom de **d�codeur Google Play de SFR** est une Google Tv qui est maintenant plus support�e.

# Informations

Ces informations peuvent �tre utiles pour un futur d�veloppement d'une rom (CyanogenMod...) sur le d�codeur.

* [Table des partitions et leur contenu extrait des logs de la recovery](RECOVERY_FILESYSTEM_TABLE.md),
* [Acc�s � une partie du code source](http://opensource.lge.com/fileMgr/download/op/SZ930T-HF/5360) sous license opensource (ne sert � rien pour une custom rom).

# Root du d�codeur

Si vous voulez rooter votre d�codeur, vous pouvez d�s maintenant suivre ces instructions.
Ce root consiste � flasher une update dans le recovery contenant le binaire de su,
et il d�sactive �galement la r�installation de la recovery (pour mettre un custom recovery).

Vous aurez juste besoin d'un pc avec [ADB](http://forum.frandroid.com/topic/143999-tuto-installation-adb/).

## Credit

Je remercis le cr�ateur de [ioroot](http://forum.xda-developers.com/showpost.php?p=48709232&postcount=869), qui a cr�� **datroot**, 
que j'ai tr�s l�g�rement modifi� pour fonctionner sur cet appareil.

## Etape 0 : Avertissement

```
/*
 * Your warranty is now void.
 *
 * We are not responsible for bricked devices, dead SD cards,
 * thermonuclear war, or you getting fired because the alarm app failed. Please
 * do some research if you have any concerns about features included in this ROM
 * before flashing it! YOU are choosing to make these modifications, and if
 * you point the finger at us for messing up your device, we will laugh at you.
 *
 */
```

Ce script a �t� test� sur mon propre d�codeur, et marche tr�s bien.
Mais il se peut que sur votre d�codeur, la configuration du stockage soit diff�rente et m�ne ainsi � un brick lors du flash.

Ainsi, avant de flasher le zip, v�rifiez que :
* Vous avez bien une **Google TV SFR-G8800**, mod�le SZ930T,
* Vous �tes bien sur la derni�re mise � jour (4.2.2 build **JDQ39**, logiciel SFR.02412.07729),
* Vous avez une connexion stable wifi / ethernet et que votre PC et sur le m�me r�seau (pour adb),

## Etape 1 : shell adb
Pour utiliser adb, il faut activer le mode d�veloppeur, puis activer le d�bogage USB dans les param�tres.

Vous avec besoin d'un terminal sur le d�codeur pour configurer le serveur adb.
Vous pouvez installer celui-ci : [Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=fr).

Pour activer adb par le r�seau, ouvrez un terminal sur Android et tapez : 
* setprop service.adb.tcp.port 5555
* stop adbd
* start adbd

Ensuite, connectez-vous avec un ordinateur dessus avec adb :
* adb connect <ip r�seau>

Ensuite v�rifier que "**adb shell mount**" contient bien :
```
/dev/block/mmcblk0p6 /system ext4 ro,relatime,data=ordered 0 0
```

Si le nombre apr�s mmcblk0p change, alors **NE FLASHER SURTOUT PAS**,
car le script s'installerait alors autre pas que sur le syst�me Android.

## Etape 1 : pr�paration d'une cl� USB et boot en recovery

T�l�chargez [datroot-gtv-signed.zip](datroot-gtv-signed.zip) et placez-le � la racine d'une cl� USB.
Branchez cette cl� USB sur le c�t� de la Google TV et ex�cutez : "**adb reboot recovery**"

## Etape 2 : Flash

Naviguez dans les menus avec la t�l�commande :
* S�lectionnez "*apply update from external storage*"
* S�lectionnez le fichier zip "datroot-gtv-signed.zip"
* La Google TV devrait red�marrer toute seule.

## Etape 3 : SuperSU

Il ne vous reste plus qu'installer [SuperSu](https://play.google.com/store/apps/details?id=eu.chainfire.supersu&hl=fr) dans le Play Store.
Normalement vous devriez avoir une mise � jour du binaire su disponible,
faites-l� pour v�rifier que le root est op�rationnel.
