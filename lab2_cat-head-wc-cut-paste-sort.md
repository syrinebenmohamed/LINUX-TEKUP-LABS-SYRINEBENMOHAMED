# Compte rendu – LAB2 : chaînes de caractères, filtres et redirections

---

## Question 1

> [!NOTE]
> **Copier le fichier /etc/passwd dans votre répertoire personnel, sous le nom mypasswd.**

**Commande :**

```bash
cp /etc/passwd ~/mypasswd
```

> [!TIP]
> **Réponse :** le fichier **`mypasswd`** est créé dans le répertoire personnel.

---

## Question 2

> [!NOTE]
> **Visualiser le contenu du nouveau fichier créé mypasswd à l'aide des commandes cat, less, et more, et vérifier que chaque ligne de ce fichier décrit la configuration d'un compte utilisateur sur le système.**

**Commande :**

```bash
cat mypasswd
```

**Résultat :**

```text
root:x:0:0:Super User:/root:/bin/bash
bin:x:1:1:bin:/bin:/usr/sbin/nologin
daemon:x:2:2:daemon:/sbin:/usr/sbin/nologin
adm:x:3:4:adm:/var/adm:/usr/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/usr/sbin/nologin
[…]
tcpdump:x:72:72:tcpdump:/:/usr/sbin/nologin
cyrine:x:1000:1000:cyrine:/home/cyrine:/bin/bash
```

**Commandes :**

```bash
less mypasswd
more mypasswd
```

> [!TIP]
> **Explication :**
> - **`cat`** affiche tout le contenu du fichier d'un seul coup.
> - **`less`** affiche le fichier page par page ; on avance et on recule avec les flèches, **`q`** pour quitter.
> - **`more`** affiche aussi page par page mais seulement vers l'avant (Espace = page suivante, **`q`** = quitter).

**Réponse :** oui, chaque ligne décrit un compte utilisateur. Elle contient 7 champs séparés par **`:`**. Exemple avec `cyrine:x:1000:1000:cyrine:/home/cyrine:/bin/bash` :

| Champ | Signification | Valeur |
| --- | --- | --- |
| 1 | Nom de l'utilisateur (login) | cyrine |
| 2 | Mot de passe (x = stocké dans /etc/shadow) | x |
| 3 | UID (numéro de l'utilisateur) | 1000 |
| 4 | GID (numéro du groupe principal) | 1000 |
| 5 | Commentaire (nom complet) | cyrine |
| 6 | Répertoire personnel | /home/cyrine |
| 7 | Shell de connexion | /bin/bash |

---

## Question 3

> [!NOTE]
> **Visualiser le contenu du fichier mypasswd dans l'ordre inverse des lignes, à l'aide de la commande tac.**

**Commande :**

```bash
tac mypasswd
```

**Résultat :**

```text
cyrine:x:1000:1000:cyrine:/home/cyrine:/bin/bash
tcpdump:x:72:72:tcpdump:/:/usr/sbin/nologin
dnsmasq:x:981:980:Dnsmasq DHCP and DNS server:/var/lib/dnsmasq:/usr/sbin/nologin
[…]
daemon:x:2:2:daemon:/sbin:/usr/sbin/nologin
bin:x:1:1:bin:/bin:/usr/sbin/nologin
root:x:0:0:Super User:/root:/bin/bash
```

> [!TIP]
> **Explication :** **`tac`** (« cat » à l'envers) affiche les lignes du fichier en commençant par la dernière.

**Réponse :** le fichier s'affiche dans l'ordre inverse : `cyrine` (dernière ligne) apparaît en premier et `root` (première ligne) en dernier.

---

## Question 4

> [!NOTE]
> **À l'aide des commandes head et tail, afficher respectivement les 5 premières lignes et les 5 dernières lignes du fichier mypasswd.**

**Commande :**

```bash
head -5 mypasswd
```

**Résultat :**

```text
root:x:0:0:Super User:/root:/bin/bash
bin:x:1:1:bin:/bin:/usr/sbin/nologin
daemon:x:2:2:daemon:/sbin:/usr/sbin/nologin
adm:x:3:4:adm:/var/adm:/usr/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/usr/sbin/nologin
```

**Commande :**

```bash
tail -5 mypasswd
```

**Résultat :**

```text
sshd:x:74:74:Privilege-separated SSH:/usr/share/empty.sshd:/usr/sbin/nologin
chrony:x:982:981:chrony system user:/var/lib/chrony:/sbin/nologin
dnsmasq:x:981:980:Dnsmasq DHCP and DNS server:/var/lib/dnsmasq:/usr/sbin/nologin
tcpdump:x:72:72:tcpdump:/:/usr/sbin/nologin
cyrine:x:1000:1000:cyrine:/home/cyrine:/bin/bash
```

> [!TIP]
> **Explication :** **`head -5`** affiche les 5 premières lignes du fichier et **`tail -5`** les 5 dernières. Sans le nombre, les deux commandes affichent 10 lignes par défaut.

**Réponse :** les 5 premiers comptes sont root, bin, daemon, adm et lp ; les 5 derniers sont sshd, chrony, dnsmasq, tcpdump et cyrine.

---

## Question 5

> [!NOTE]
> **En utilisant la commande wc, compter le nombre de comptes utilisateurs existants sur la machine.**

**Commande :**

```bash
wc -l mypasswd
```

**Résultat :**

```text
39 mypasswd
```

> [!TIP]
> **Explication :** **`wc`** (word count) compte le contenu d'un fichier ; l'option **`-l`** compte seulement les lignes. Sans option, `wc mypasswd` affiche `39 97 2355` : 39 lignes, 97 mots et 2355 octets.

**Réponse :** chaque ligne correspond à un compte, donc il y a **39 comptes utilisateurs** sur la machine.

---

## Question 6

> [!NOTE]
> **À l'aide de la commande nl afficher le contenu du fichier mypasswd en numérotant chaque ligne.**

**Commande :**

```bash
nl mypasswd
```

**Résultat :**

```text
     1  root:x:0:0:Super User:/root:/bin/bash
     2  bin:x:1:1:bin:/bin:/usr/sbin/nologin
     3  daemon:x:2:2:daemon:/sbin:/usr/sbin/nologin
[…]
    38  tcpdump:x:72:72:tcpdump:/:/usr/sbin/nologin
    39  cyrine:x:1000:1000:cyrine:/home/cyrine:/bin/bash
```

> [!TIP]
> **Explication :** **`nl`** (number lines) affiche le fichier en ajoutant le numéro de chaque ligne au début.

**Réponse :** les lignes sont numérotées de 1 à 39, ce qui confirme les 39 comptes trouvés avec `wc -l`.

---

## Question 7

> [!NOTE]
> **Générer une liste des différents shells en cours d'utilisation sur l'ordinateur et l'enregistrer dans un fichier sous le nom shells. Visualiser par la suite le contenu du nouveau fichier créé shells. Expliquer le rôle des options -d et -f.**

**Commandes :**

```bash
cut -d: -f7 mypasswd > shells
cat shells
```

**Résultat :**

```text
/bin/bash
/usr/sbin/nologin
/usr/sbin/nologin
/usr/sbin/nologin
/usr/sbin/nologin
/bin/sync
/sbin/shutdown
/sbin/halt
[…]
/usr/sbin/nologin
/bin/bash
```

> [!TIP]
> **Explication :** **`cut`** découpe chaque ligne et n'en garde qu'une partie. Ici il garde le 7e champ de chaque ligne, c'est-à-dire le shell.
>
> **`>`** enregistre le résultat dans le fichier `shells` au lieu de l'afficher, puis `cat shells` affiche ce fichier.

**Réponse :** le fichier `shells` contient la liste des shells des 39 comptes (`/bin/bash`, `/usr/sbin/nologin`, `/sbin/nologin`, `/bin/sync`, `/sbin/shutdown`, `/sbin/halt`). Rôle des options :

- **`-d`** : indique le caractère qui sépare les champs, ici `:`.
- **`-f`** : indique le numéro du champ à garder, ici le 7e (le shell).

---

## Question 8

> [!NOTE]
> **Que permettent ces deux commandes de réaliser ?**
> `cut -c 1-10 mypasswd > mypasswd1`
> `cut -c 11- mypasswd > mypasswd2`

**Commandes :**

```bash
cut -c 1-10 mypasswd > mypasswd1
cat mypasswd1
```

**Résultat :**

```text
root:x:0:0
bin:x:1:1:
daemon:x:2
adm:x:3:4:
lp:x:4:7:l
[…]
cyrine:x:1
```

**Commandes :**

```bash
cut -c 11- mypasswd > mypasswd2
cat mypasswd2
```

**Résultat :**

```text
:Super User:/root:/bin/bash
bin:/bin:/usr/sbin/nologin
:2:daemon:/sbin:/usr/sbin/nologin
adm:/var/adm:/usr/sbin/nologin
p:/var/spool/lpd:/usr/sbin/nologin
[…]
000:1000:cyrine:/home/cyrine:/bin/bash
```

> [!TIP]
> **Explication :** l'option **`-c`** découpe par position de caractères (et non par champs). `1-10` = du 1er au 10e caractère ; `11-` = du 11e caractère jusqu'à la fin de la ligne.

**Réponse :** ces deux commandes coupent chaque ligne de `mypasswd` en deux morceaux : les 10 premiers caractères sont enregistrés dans `mypasswd1` et le reste de la ligne dans `mypasswd2`.

---

## Question 9

> [!NOTE]
> **Fusionner le contenu des deux fichiers mypasswd1 et mypasswd2 à l'aide de la commande paste.**

**Commande :**

```bash
paste mypasswd1 mypasswd2
```

**Résultat :**

```text
root:x:0:0      :Super User:/root:/bin/bash
bin:x:1:1:      bin:/bin:/usr/sbin/nologin
daemon:x:2      :2:daemon:/sbin:/usr/sbin/nologin
adm:x:3:4:      adm:/var/adm:/usr/sbin/nologin
lp:x:4:7:l      p:/var/spool/lpd:/usr/sbin/nologin
[…]
cyrine:x:1      000:1000:cyrine:/home/cyrine:/bin/bash
```

> [!TIP]
> **Explication :** **`paste`** colle les fichiers côte à côte, ligne par ligne : la ligne 1 de `mypasswd1` avec la ligne 1 de `mypasswd2`, et ainsi de suite. Par défaut, il met une tabulation entre les deux.

**Réponse :** on retrouve les lignes complètes de `mypasswd`, avec une tabulation à l'endroit de la coupure. Avec `paste -d '' mypasswd1 mypasswd2` (aucun séparateur), on obtiendrait exactement le fichier d'origine.

---

## Question 10

> [!NOTE]
> **Le fichier shells contient toutes les informations recherchées, mais sans un ordre particulier. Trier les lignes de la sortie et placer les nouvelles données dans un nouveau fichier intitulé sorted.shells.**

**Commandes :**

```bash
sort shells > sorted.shells
cat sorted.shells
```

**Résultat :**

```text
/bin/bash
/bin/bash
/bin/sync
/sbin/halt
/sbin/nologin
/sbin/nologin
[…]
/sbin/shutdown
/usr/sbin/nologin
/usr/sbin/nologin
[…]
/usr/sbin/nologin
```

> [!TIP]
> **Explication :** **`sort`** trie les lignes du fichier `shells` par ordre alphabétique, et **`>`** enregistre le résultat dans le nouveau fichier `sorted.shells`. Le fichier `shells` n'est pas modifié.

**Réponse :** les shells identiques sont maintenant regroupés : 2 × `/bin/bash`, 1 × `/bin/sync`, 1 × `/sbin/halt`, 10 × `/sbin/nologin`, 1 × `/sbin/shutdown` et 24 × `/usr/sbin/nologin` (total 39).
