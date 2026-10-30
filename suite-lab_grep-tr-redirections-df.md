# Suite lab – grep, tr, redirections, df


---

## Question 1

> **Créer une copie de fichier /etc/shadow dans votre répertoire personnel. Le nouveau fichier est nommé passwords**

**Commandes :**

```bash
sudo cp /etc/shadow passwords
sudo cat passwords
```

**Résultat :**

```text
root:$y$j9T$[masqué]::0:99999:7:::
bin:*:20186:0:99999:7:::
daemon:*:20186:0:99999:7:::
adm:*:20186:0:99999:7:::
lp:*:20186:0:99999:7:::
sync:*:20186:0:99999:7:::
shutdown:*:20186:0:99999:7:::
halt:*:20186:0:99999:7:::
mail:*:20186:0:99999:7:::
operator:*:20186:0:99999:7:::
games:*:20186:0:99999:7:::
ftp:*:20186:0:99999:7:::
nobody:*:20186:0:99999:7:::
dbus:!:20734::::::
yggdrasil:!:20734::::::
yggdrasil-worker:!:20734::::::
tss:!:20734::::::
avahi:!:20734::::::
systemd-oom:!:20734::::::
polkitd:!:20734::::::
rtkit:!:20734::::::
geoclue:!:20734::::::
clevis:!:20734::::::
sssd:!:20734::::::
gnome-remote-desktop:!*:20734::::::
libstoragemgmt:!*:20734::::::
pipewire:!*:20734::::::
systemd-coredump:!*:20734:::::1:
wsdd:!:20734::::::
colord:!:20734::::::
setroubleshoot:!:20734::::::
flatpak:!:20734::::::
gdm:!:20734::::::
gnome-initial-setup:!:20734::::::
sshd:!:20734::::::
chrony:!:20734::::::
dnsmasq:!:20734::::::
tcpdump:!:20734::::::
cyrine:$y$j9T$[masqué]::0:99999:7:::
```


---

## Question 2

> **En utilisant le fichier passwords, rechercher les lignes qui contiennent !!**

**Commandes et résultats :**

```bash
cyrine@localhost:~$ sudo chown cyrine passwords
cyrine@localhost:~$ grep '!!' passwords
grep: passwords: Permission denied
cyrine@localhost:~$ chmod 600 passwords
cyrine@localhost:~$ grep '!!' passwords
-----------------------------
```

```bash
cyrine@localhost:~$ grep '!' passwords
```


```text
dbus:!:20734::::::
yggdrasil:!:20734::::::
yggdrasil-worker:!:20734::::::
tss:!:20734::::::
avahi:!:20734::::::
systemd-oom:!:20734::::::
polkitd:!:20734::::::
rtkit:!:20734::::::
geoclue:!:20734::::::
clevis:!:20734::::::
sssd:!:20734::::::
gnome-remote-desktop:!*:20734::::::
libstoragemgmt:!*:20734::::::
pipewire:!*:20734::::::
systemd-coredump:!*:20734:::::1:
wsdd:!:20734::::::
colord:!:20734::::::
setroubleshoot:!:20734::::::
flatpak:!:20734::::::
gdm:!:20734::::::
gnome-initial-setup:!:20734::::::
sshd:!:20734::::::
chrony:!:20734::::::
dnsmasq:!:20734::::::
tcpdump:!:20734::::::
```


---

## Question 3

> **A l’aide de la commande tr, remplacer les : par #. Sauvegarder le résultat dans un fichier pass2**

**Commande :**

```bash
cyrine@localhost:~$ tr ':' '#' < passwords > pass2
```

> [!TIP]
> **`tr`** (translate) remplace des caractères par d’autres. Il prend chaque caractère de la première liste et le remplace par le caractère correspondant de la deuxième.
>
> Le **`<`** sert à donner le contenu d’un fichier à une commande, comme si tu le tapais toi-même au clavier.

---

## Question 4

> **A partir de fichier passwords, et en utilisant tr, remplacer / par %. Sauvegarder le résultat dans le même fichier passwords1.**

**Commandes :**

```bash
cyrine@localhost:~$ tr '/' '%' < passwords > passwords1
cyrine@localhost:~$ diff passwords passwords1
```

**Résultat :**

```text
1c1
< root:$y$j9T$[masqué]...dFu/p77A::0:99999:7:::
---
> root:$y$j9T$[masqué]...dFu%p77A::0:99999:7:::
```

---

## Question 5

> **Lire à partir de clavier le texte suivant et l’ajouter au fichier exemple :**

**Commande et texte saisi :**

```bash
cyrine@localhost:~$ cat >>exemple
Tekup

Tic
Tekup%Tic
C'est la 5ème ligne
```

---

## Question 6

> **Ajouter le contenu de fichier exemple à la fin de fichier passwords**

**Commandes :**

```bash
cyrine@localhost:~$ cat exemple >> passwords
cyrine@localhost:~$ cat passwords
```

**Résultat :**

```text
root:$y$j9T$[masqué]::0:99999:7:::
bin:*:20186:0:99999:7:::
daemon:*:20186:0:99999:7:::
adm:*:20186:0:99999:7:::
lp:*:20186:0:99999:7:::
sync:*:20186:0:99999:7:::
shutdown:*:20186:0:99999:7:::
halt:*:20186:0:99999:7:::
mail:*:20186:0:99999:7:::
operator:*:20186:0:99999:7:::
games:*:20186:0:99999:7:::
ftp:*:20186:0:99999:7:::
nobody:*:20186:0:99999:7:::
dbus:!:20734::::::
yggdrasil:!:20734::::::
yggdrasil-worker:!:20734::::::
tss:!:20734::::::
avahi:!:20734::::::
systemd-oom:!:20734::::::
polkitd:!:20734::::::
rtkit:!:20734::::::
geoclue:!:20734::::::
clevis:!:20734::::::
sssd:!:20734::::::
gnome-remote-desktop:!*:20734::::::
libstoragemgmt:!*:20734::::::
pipewire:!*:20734::::::
systemd-coredump:!*:20734:::::1:
wsdd:!:20734::::::
colord:!:20734::::::
setroubleshoot:!:20734::::::
flatpak:!:20734::::::
gdm:!:20734::::::
gnome-initial-setup:!:20734::::::
sshd:!:20734::::::
chrony:!:20734::::::
dnsmasq:!:20734::::::
tcpdump:!:20734::::::
cyrine:$y$j9T$[masqué]::0:99999:7:::
Tekup

Tic
Tekup%Tic
C'est la 5ème ligne
```

</details>

> [!TIP]
> **`cat exemple`** lit le contenu du fichier exemple, et **`>>`** l'ajoute à la fin de passwords sans effacer ce qu'il contient déjà.

> [!WARNING]
> Attention : avec un seul **`>`**, tout le contenu de passwords serait perdu.

---

## Question 7

> **Rechercher dans la fichier passwords les lignes contenant uniquement le mot Tic**

**Commande et résultat :**

```bash
cyrine@localhost:~$ grep '^Tic$' passwords
Tic
```

> [!TIP]
> - **`^`** veut dire « début de la ligne » ;
> - **`$`** veut dire « fin de la ligne » ;

---

## Question 8

> **La commande df permet d’afficher la valeur d'espace disque disponible des systèmes de fichiers. Utilisez cette commande avec les options hT. Puis extraire le type de système de fichiers. Enlever les redondances pour les noms des systèmes de fichiers et sauvegarder le résultat dans un fichier type.**

**Commande :**

```bash
cyrine@localhost:~$ df -hT
```

**Résultat :**

```text
Filesystem            Type      Size  Used Avail Use% Mounted on
/dev/mapper/rhel-root xfs        17G  4.3G   13G  25% /
devtmpfs              devtmpfs  1.8G     0  1.8G   0% /dev
tmpfs                 tmpfs     1.8G   84K  1.8G   1% /dev/shm
tmpfs                 tmpfs     731M  9.5M  722M   2% /run
tmpfs                 tmpfs     1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
/dev/sda2             xfs       960M  353M  608M  37% /boot
tmpfs                 tmpfs     366M  136K  366M   1% /run/user/1000
/dev/sr0              iso9660   9.5G  9.5G     0 100% /run/media/cyrine/RHEL-10-1-BaseOS-x86_64
```

> [!TIP]
> here the fields aren't seperated by **`:`** so to seperate fields we need to set the multiple espaces to one espace with **`tr -s ' '`** this squeezes the **`' '`** to one espace, this can be used anywhere like in this example:
>
> ```bash
> echo "aaabbbccc" | tr -s 'a'
> abbbccc
> ```

> [!TIP]
> we used **pipe** pour que le résultat d'une commande soit l'input de la next commande.

**Commandes :**

```bash
cyrine@localhost:~$ df -hT | tr -s ' ' | cut -d' ' -f2 | sort | uniq > type
cyrine@localhost:~$ cat type
```

**Résultat :**

```text
devtmpfs
iso9660
tmpfs
Type
xfs
```
