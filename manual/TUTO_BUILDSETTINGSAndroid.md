Comment créer un build pour android 7.0 et PLUS ?

Version Unity : 2020.2.4f1
Version du projet : 0.5.0
Date : 28/10/2021

La toute première chose qu'il faut vérifier avant de faire votre build est de voir si vous avez votre "build affiliation" avec *Android* ou *iOS*.
![](../resources/BUILDSETTINGSAndroid/Aspose.Words.83a8d5d0-0eaf-4178-8e0e-2b5d1dd65668.001.png)
Ensuite vous devrez aller vérifier dans Preferences --) External tools que votre JDK, SDK, NDK et Gladle se sont bien setup quand vous avez installé les modules du Unity Hub.

![](../resources/BUILDSETTINGSAndroid/Aspose.Words.83a8d5d0-0eaf-4178-8e0e-2b5d1dd65668.002.png)


Si les modules sont bien installés, vous pouvez tenter de faire un build pour vérifier leur installation. Si tout marche GG aller vers la partie IL2CPP du tutoriel.

Si les modules ne se sont pas correctement installés (modules manquants, mauvaise version, ect.)

Vous devrez voir quel module manque (SDK, JDK, Ndk, etc.) En fonction de cela vous devrez télécharger les versions ci-dessous et les intégrer à vos projets.

JDK, SDK, NDK et gradle : 

<https://drive.google.com/drive/folders/11FE9c_rRtwuOpD4OMBJEMXLjYFsopW4r?usp=sharing>

![](../resources/BUILDSETTINGSAndroid/Aspose.Words.83a8d5d0-0eaf-4178-8e0e-2b5d1dd65668.003.png)

Quand vous avez récupérer les liens du drive il suffit de les ajouter dans votre version unity depuis votre bibliothèque (sauf pour le gradle qu'après avoir unzip vous pouvez laisser dans votre téléchargement) voici le path : 

C:\Program Files\Unity\Hub\Editor\2020.2.4f1\Editor\Data\PlaybackEngines\AndroidPlayer 

Suprimez les dossiers SDK, JDK, NDK s'ils sont présent dans votre bibliothèque au path indiqué, ATTENTION quand vous Unzippez à bien respecter le path et ne pas avoir de double exemple ...Data\PlaybackEngines\AndroidPlayer\SDK\SDK ! Bien faire gaffe au doublon !

Dans unity après l'avoir lancé vous devriez obtenir le résultat ci-dessous :

![](../resources/BUILDSETTINGSAndroid/Aspose.Words.83a8d5d0-0eaf-4178-8e0e-2b5d1dd65668.004.png)


(Nécessaire pour lire avec bluestack mais normalement automatique au prochain push)


Une fois que tout est bien setup aller dans les project settings changer dans Player le scripting backend pour le mettre en IL2CPP.


![](../resources/BUILDSETTINGSAndroid/Aspose.Words.83a8d5d0-0eaf-4178-8e0e-2b5d1dd65668.005.png)

Voilà vous avez maintenant tout prêt pour un build, il vous suffit juste de BUILD et faire votre APK.

Avec l'APK vous pouvez l'exporter sur BlueStacks ou LD player pour tester l'application ! 

PS : Merci de reporter tous les bugs rencontrés et comment vous les avez réglés ou remplir une FAQ ! :D


