# Sniffing_et_Anti-Sniffing_MitM
ce projet est de la part de Oukaci Sarah M1 SSI 
### Rapport de Test de Pénétration : Sniffing et Anti-Sniffing

#### 1. Préparation de l'Environnement Virtuel

1. **Créer deux Machines Virtuelles (VMs)** :
   - **Attaquant** : Kali Linux
   - **Cible** : Ubuntu

2. **Configurer les Paramètres Réseau** :
   - Configurer l'adaptateur réseau sur "Bridged Adapter" ou "Internal Network" pour assurer la communication entre elles.
   - Vérifier que les deux VMs sont sur le même réseau.

#### 2. Configuration des VMs

1. **Configurer Kali Linux (Attaquant)** :
   - Mettre à jour le système en utilisant :
     
     **_sudo apt update && sudo apt upgrade -y_**
   - Installer Wireshark et Ettercap :
     
     **_sudo apt install wireshark ettercap-graphical_**

2. **Configurer Ubuntu (Cible)** :
   - Installer un serveur web (Apache) :
     
     **_sudo apt update_**
     
     **_sudo apt install apache2_**
   - Vérifier que le serveur web fonctionne en accédant à l'adresse IP de la VM cible dans un navigateur.

#### 3. Réaliser l'Attaque de Sniffing

1. **Utiliser Wireshark sur Kali Linux** :
   - Démarrer Wireshark.
   - Sélectionner l'interface réseau (dans mon cas j'ai utlisée eth0).
   - Appliquer un filtre pour capturer le trafic HTTP (écrire dans recherche de wireshark HTTP) : 
   - Analyser le trafic pour trouver des informations sensibles.

2. **Utiliser Ettercap sur Kali Linux** :
   - Démarrer Ettercap en mode graphique en utilisant:
     
     **_sudo ettercap -G_**
   - Sélectionner l'interface réseau(la méme que la précédente).
   - Démarrer le sniffing unifié.
   - Scanner les hôtes pour identifier la VM cible.
   - Lancer une attaque Man-in-the-Middle via ARP spoofing.

#### 4. Anti-Sniffing

1. **Détection des Tentatives de Sniffing** :
   - Installer `arpwatch` sur la VM cible :
     
     **_sudo apt install arpwatch_**
   - Lancer `arpwatch` pour surveiller les activités ARP :

     **_sudo arpwatch -i eth0_**
   - Analyser les logs pour détecter des activités suspectes.

2. **Implémentation de Mesures de Sécurité Réseau** :
   - **Chiffrement** :
     - Configurer HTTPS sur le serveur web :
       
       **_sudo apt install certbot python3-certbot-apache_**
       
       **_sudo certbot --apache_**
   - **Sécurisation ARP** (en utilisant des techniques anti-ARP spoofing).
   - **Segmentation du Réseau** (en divisant le réseau en segments pour limiter l'exposition des données sensibles).




