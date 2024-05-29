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
     ```bash
     sudo apt update && sudo apt upgrade -y
     ```
   - Installer Wireshark et Ettercap :
     ```bash
     sudo apt install wireshark ettercap-graphical
     ```

2. **Configurer Ubuntu (Cible)** :
   - Installer un serveur web (Apache) :
     ```bash
     sudo apt update
     sudo apt install apache2
     ```
   - Vérifier que le serveur web fonctionne en accédant à l'adresse IP de la VM cible dans un navigateur.

#### 3. Réaliser l'Attaque de Sniffing

1. **Utiliser Wireshark sur Kali Linux** :
   - Démarrer Wireshark.
   - Sélectionner l'interface réseau (dans mon cas j'ai utlisée eth0).
   - Appliquer un filtre pour capturer le trafic HTTP (écrire dans recherche de wireshark HTTP) : 
   - Analyser le trafic pour trouver des informations sensibles.

2. **Utiliser Ettercap sur Kali Linux** :
   - Démarrer Ettercap en mode graphique en utilisant:
     ```bash
     sudo ettercap -G
     ```
   - Sélectionner l'interface réseau(la méme que la précédente).
   - Démarrer le sniffing unifié.
   - Scanner les hôtes pour identifier la VM cible.
   - Lancer une attaque Man-in-the-Middle via ARP spoofing.

#### 4. Anti-Sniffing

1. **Détection des Tentatives de Sniffing** :
   - Installer `arpwatch` sur la VM cible :
     ```bash
     sudo apt install arpwatch
     ```
   - Lancer `arpwatch` pour surveiller les activités ARP :
     ```bash
     sudo arpwatch -i eth0
     ```
   - Analyser les logs pour détecter des activités suspectes.

2. **Implémentation de Mesures de Sécurité Réseau** :
   - **Chiffrement** :
     - Configurer HTTPS sur le serveur web :
       ```bash
       sudo apt install certbot python3-certbot-apache
       sudo certbot --apache
       ```
   - **Sécurisation ARP** (en utilisant des techniques anti-ARP spoofing).
   - **Segmentation du Réseau** (en divisant le réseau en segments pour limiter l'exposition des données sensibles).


---

