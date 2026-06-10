# LAB-13-Bypass-de-la-D-tection-de-Root-Android-avec-Objections
# 🗺️ LAB 13 : Contournement de la Détection de Root Android avec Objection Framework

## 📝 Description du Projet
Ce laboratoire clôture la série d'audits de sécurité mobile en se focalisant sur le **contournement de la détection de root** via l'outil **Objection (Runtime Mobile Exploration)**[cite: 5]. Objection est un framework de sécurité alimenté par Frida, qui permet d'explorer l'état d'exécution des applications mobiles à la volée, sans avoir à rédiger manuellement des scripts d'instrumentation.

---

## 🛠️ Outils & Spécifications
* **Outil Principal :** Objection Framework (Frida-powered runtime exploration)[cite: 5]
* **Environnement Hôte :** Terminal CLI (Windows/Linux)[cite: 5]
* **Appareil Cible :** Émulateur Android rooté connecté via ADB[cite: 5]
* **Objectif :** Automatiser le Hooking de l'API de détection de Root au niveau du Runtime[cite: 5]

---

## 🚀 Chronologie du Lab & Preuves en Images

### Étape 1 : Initialisation d'Objection et Exploration du Runtime
Connexion à l'application cible en utilisant la commande d'injection d'Objection. Le framework s'attache au processus au démarrage pour prendre le contrôle du runtime de l'APK.
<img width="987" height="230" alt="Connexion et initialisation d'Objection" src="https://github.com/user-attachments/assets/1c4d5a1b-2792-4823-8b60-1cff088777e0" />

### Étape 2 : Vérification du statut de l'environnement de sécurité
Lancement de l'environnement interactif d'Objection. Le shell est prêt à recevoir les commandes de haut niveau pour manipuler l'application.
<img width="841" height="124" alt="Shell interactif Objection actif" src="https://github.com/user-attachments/assets/4e63aba9-8859-4e12-b041-47382f36ddbf" />

### Étape 3 : Injection de la commande automatique de Root Bypass
Exécution de la commande magique d'Objection : `android root disable`. Ce module intégré va automatiquement chercher toutes les classes Java standard de détection de root et simuler un environnement sain.
<img width="1095" height="548" alt="Exécution de la commande android root disable" src="https://github.com/user-attachments/assets/44bdb1b4-a3b2-47fd-b25f-66585ab5868d" />

### Étape 4 : Validation finale du contournement f l'application
Vérification des logs en temps réel. Les hooks d'Objection interceptent avec succès les fonctions de sécurité, permettant de bypasser la restriction et de faire fonctionner l'application sur l'appareil rooté.
<img width="702" height="523" alt="Logs de succès et validation du Root Bypass" src="https://github.com/user-attachments/assets/97ccc0fe-e732-40d2-88f9-78c5b6fa217c" />

---

## 📊 Rapport d'Audit de Sécurité

* **Auditeur :** Anas El Mahfoudy
* **Établissement :** École Marocaine des Sciences de l'Ingénieur (EMSI)
* **Catégorie :** Instrumentation Dynamique / Pentesting Mobile[cite: 5]

---

## 🔍 Méthodologie et Avantages d'Objection

L'un des plus grands défis de la sécurité mobile est la rapidité d'exécution lors d'un audit. Là où **Frida pur** demande l'écriture de scripts JS spécifiques, **Objection** fournit une abstraction totale[cite: 5]. 

En tapant simplement la commande `android root disable`, le framework effectue un scan des signatures de méthodes et des packages connus pour le Root Check (comme *RootBeer*) et applique des règles de retour systématiques à `false` sur les indicateurs de compromission[cite: 5].

---

## 📌 Points clés à retenir de la série des Labs
1. **L'écosystème Frida :** À travers les Labs 11, 12, et 13, l'utilisation successive de Frida, Medusa, puis Objection montre la puissance de l'instrumentation dynamique déclinée sous différentes formes (scripts purs, automatisation par recettes, ou exploration interactive en ligne de commande).
2. **Défense en profondeur :** Pour protéger efficacement une application, s'appuyer sur de simples vérifications locales (Java/Natif) est insuffisant. Il est crucial d'implémenter des mécanismes de détection de Frida (Anti-Frida) combinés à des vérifications de l'intégrité du code côté serveur.
