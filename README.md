📘 README – Mini-Projet 2
Monitoring et alerting d’une instance EC2 avec CloudWatch et SNS
🎯 Objectif du projet

Mettre en place une solution de supervision et d’alerting sur une instance EC2 Amazon Linux (t3.micro) en utilisant les services AWS suivants :

Amazon EC2

Amazon CloudWatch

Amazon SNS

L’objectif est de détecter une anomalie (CPU) et de recevoir une notification automatique par email, sans accès SSH à l’instance.

🧰 Services AWS utilisés

Amazon EC2 : hébergement de l’instance

Amazon CloudWatch : monitoring et création d’alarmes

Amazon SNS : envoi de notifications par email

🧩 Étapes détaillées du projet
1️⃣ Lancement de l’instance EC2

📁 Dossier : 01-EC2-Running

Accès à la console AWS

Service EC2 → Launch instance

AMI sélectionnée : Amazon Linux

Type d’instance : t3.micro

Lancement sans clé SSH (choix volontaire)

Vérification de l’état : RUNNING

📸 Capture : instance en état Running

2️⃣ Monitoring de l’instance via CloudWatch

📁 Dossier : 02-Monitoring

Accès au service CloudWatch

Menu Metrics → EC2

Visualisation des métriques par défaut :

CPUUtilization

NetworkIn

NetworkOut

Vérification de la remontée des données

📸 Capture : graphiques CloudWatch actifs

3️⃣ Création du topic SNS

📁 Dossier : 03-SNS-Tropic

Accès au service SNS → Topics

Création d’un Standard Topic

Nom explicite du topic (ex : ec2-cpu-alert)

Objectif : centraliser les alertes CloudWatch

📸 Capture : topic SNS créé

4️⃣ Création de l’abonnement SNS (en attente)

📁 Dossier : 04-Subscription-Pending

Menu Subscriptions → Create subscription

Protocole : Email

Saisie de l’adresse email

Statut affiché : Pending confirmation

📸 Capture : abonnement en attente de validation

5️⃣ Validation de l’abonnement SNS

📁 Dossier : 05-Subscription-Confirmed

Réception de l’email AWS

Clic sur le lien de confirmation

Statut de l’abonnement : Confirmed

📸 Capture : abonnement confirmé

6️⃣ Création de l’alarme CloudWatch

📁 Dossier : 06-CloudWatch-Alarm

Accès à CloudWatch → Alarms → Create alarm

Sélection de la métrique CPUUtilization

Type de seuil : Statique

Condition : Supérieur au seuil

Valeur du seuil : définie manuellement

Période d’évaluation : 1 minute

Action : notification via le topic SNS créé

📸 Capture : configuration complète de l’alarme

7️⃣ Déclenchement de l’alerte

📁 Dossier : 07-Alarm-Trigered

Passage de l’alarme à l’état ALARM

Envoi automatique d’une notification par email

Validation du bon fonctionnement du flux :

EC2 → CloudWatch → SNS → Email

📸 Capture : alarme déclenchée + email reçu

✅ Résultat final

Instance EC2 surveillée en temps réel

Alarme CloudWatch fonctionnelle

Notification automatique reçue par email

Solution sans accès SSH, orientée supervision
