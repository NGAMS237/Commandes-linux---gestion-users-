# Commandes-linux---gestion-users-
✔gestion utilisateurs ✔ groupes ✔ permissions Linux ✔ sudo / root ✔ sécurité de base


# 🐧 Linux Administration Cheat Sheet (Debian)

Un guide complet pour la gestion des **utilisateurs, groupes, permissions et privilèges (sudo/root)** sous Linux (Debian/Ubuntu).

---

# 📌 Table des matières

* [Utilisateurs](#-utilisateurs)
* [Groupes](#-groupes)
* [Sudo & privilèges](#-sudo--privilèges)
* [Root](#-root)
* [Permissions](#-permissions)
* [Permissions avancées](#-permissions-avancées)
* [Cas pratique](#-cas-pratique)
* [Commandes essentielles](#-commandes-essentielles)

---

# 👤 Utilisateurs

## 🔎 Voir les utilisateurs

```bash
cat /etc/passwd
cut -d: -f1 /etc/passwd
```

## 👀 Infos utilisateur

```bash
id user
groups user
```

## ➕ Créer un utilisateur

```bash
sudo adduser john
```

## ❌ Supprimer un utilisateur

```bash
sudo userdel -r john
```

## 🔑 Changer mot de passe

```bash
sudo passwd john
```

---

# 👥 Groupes

## 🔎 Voir tous les groupes

```bash
cat /etc/group
```

## 👀 Voir les membres d’un groupe

```bash
getent group nom_groupe
```

👉 Exemple :

```bash
getent group sudo
```

## ➕ Créer un groupe

```bash
sudo groupadd dev
```

## ❌ Supprimer un groupe

```bash
sudo groupdel dev
```

## ➕ Ajouter utilisateur à un groupe

```bash
sudo usermod -aG dev john
```

## ➖ Retirer utilisateur d’un groupe

```bash
sudo gpasswd -d john dev
```

## 🔁 Changer groupe principal

```bash
sudo usermod -g dev john
```

---

# 🛡️ Sudo & privilèges

## 🔎 Voir les utilisateurs sudo

```bash
getent group sudo
```

## ➕ Donner sudo

```bash
sudo usermod -aG sudo john
```

## ➖ Retirer sudo

```bash
sudo deluser john sudo
```

## ⚙️ Modifier sudoers (IMPORTANT)

```bash
sudo visudo
```

👉 Exemple :

```bash
john ALL=(ALL) ALL
```

👉 Sans mot de passe :

```bash
john ALL=(ALL) NOPASSWD: ALL
```

---

# 👑 Root

## 🔎 Accès root

```bash
sudo -i
```

ou

```bash
su -
```

⚠️ Utiliser root avec précaution (contrôle total du système)

---

# 🔐 Permissions

## 🔎 Voir permissions

```bash
ls -l
```

👉 Exemple :

```
-rwxr-x--- 1 john dev fichier.txt
```

## 🔢 Modifier permissions

```bash
chmod 755 fichier
```

## ✍️ Mode symbolique

```bash
chmod u+x fichier
chmod g-w fichier
chmod o-r fichier
```

## 👤 Changer propriétaire

```bash
sudo chown john fichier.txt
```

## 👥 Changer groupe

```bash
sudo chown :dev fichier.txt
```

## 👤👥 Les deux

```bash
sudo chown john:dev fichier.txt
```

---

# 🔥 Permissions avancées

## SUID

```bash
chmod u+s fichier
```

## SGID

```bash
chmod g+s dossier
```

## Sticky Bit

```bash
chmod +t dossier
```

---

# 📂 Cas pratique

## 🎯 Objectif :

Créer un dossier partagé pour une équipe

```bash
# Créer groupe
sudo groupadd dev

# Ajouter utilisateur
sudo usermod -aG dev john

# Créer dossier
sudo mkdir /projet

# Attribuer groupe
sudo chown :dev /projet

# Permissions
sudo chmod 770 /projet

# Héritage groupe
sudo chmod g+s /projet
```

---

# ⚡ Commandes essentielles

```bash
# Utilisateurs
id user
groups user

# Groupes
getent group groupe

# Sudo
sudo usermod -aG sudo user
sudo deluser user sudo

# Permissions
ls -l
chmod 755 fichier
chown user:groupe fichier
```

---

# 🧠 Astuces

```bash
who        # utilisateurs connectés
w          # activité système
history    # commandes utilisées
sudo -l    # vérifier droits sudo
```

---

# 🚀 Objectif

Ce guide permet de :

* Gérer les utilisateurs et groupes
* Contrôler les accès
* Sécuriser un système Linux
* Administrer efficacement un serveur Debian

---

# 📌 Auteur

Projet personnel pour apprentissage Linux & administration système.
