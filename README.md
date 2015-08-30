Root pour la Google TV de SFR
======

Si vous voulez rooter votre Google TV, vous pouvez d�s maintenant suivre ces instructions.
Ce root consiste � flasher une update contenant le binaire de su,
ainsi qu'un script d�sactivant la r�installation de la recovery (pour mettre un custom recovery).

## Etape 0 : Avertissement

Ce script a �t� test� sur ma propre Google TV par SFR, et marche tr�s bien. Mais il se peut que sur votre Google TV par SFR, la configuration du stockage soit diff�rent et m�ne ainsi � un brick lors du flash.

Ainsi, avant de flasher le zip, v�rifiez que :
- Vous avez bien une Google TV SFR-G8800,
- Vous �tes bien sur la derni�re mise � jour (4.2.2 build JDQ39, logiciel SFR.02412.07729),
- Vous avez une connexion stable wifi / ethernet et que votre PC et sur le m�me r�seau (pour adb),

## Etape 1 : shell adb
Pour utiliser adb, il faut activer le mode d�veloppeur sur votre Google TV, puis activer le d�bogage USB.

R�cup�rez l'IP de la Google TV et connectez-vous dessus avec adb :
* adb connect <IP>

Ensuite v�rifier que "adb shell mount" contient bien "/dev/block/mmcblk0p6 /system ext4 ro,relatime,data=ordered 0 0".
Si le nombre apr�s mmcblk0p change, alors NE FLASHER SURTOUT P�S, car le script s'installarait alors autre pas que sur le syst�me Android.

## Etape 1 : pr�paration d'une cl� USB et boot en recovery

T�l�chargez [datroot-gtv-signed.zip](datroot-gtv-signed.zip) et placez-le � la racine d'une cl� USB.
Branchez cette cl� USB sur le c�t� de la Google TV et ex�cuter : "adb reboot recovery"

## Etape 2 : Flash

Naviguez dans les menus avec la t�l�commande :
* S�lectionnez "apply update from external storage"
* S�lectionnez le fichier zip "datroot-gtv-signed.zip"
* La Google TV devrait red�marrer toute seule.

## Etape 3 : SuperSU

Il ne vous reste plus qu'installer SuperSu dans le Play Store.
Normalement vous devriez avoir une mise � jour du binaire su disponible,
faites-l� pour v�rifier que le root est op�rationnel.
