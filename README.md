# Découpage symétrique

- **Réseau de départ :** 172.16.1.0/24
- **4 pôles :**
  - Sous-réseau 1: Informatique (50 équipements)
  - Sous-réseau 2: Développement (12 équipements)
  - Sous-réseau 3: Administratif (20 équipements)
  - Sous-réseau 4: Technicien (15 équipements)

On cherche dans le tableau des puissances de 2 ci-dessous le nombre supérieur à 50. 2^6 = 64, donc 64 - 2 = 62 adresses IP disponibles pour chaque sous-réseau.

### Calcul du CIDR :
- Le CIDR sera /26. Pour le réseau 172.16.1.0/26, on peut faire les 4 sous-réseaux suivants :

1. **Sous-réseau 1: Informatique**
   - Adresse du réseau : 172.16.1.0/26
   - Début de la plage IP disponible : 172.16.1.1
   - Fin de la plage IP disponible : 172.16.1.62
   - Adresse de broadcast : 172.16.1.63

2. **Sous-réseau 2: Développement**
   - Adresse du réseau : 172.16.1.64/26
   - Début de la plage IP disponible : 172.16.1.64
   - Fin de la plage IP disponible : 172.16.1.126
   - Adresse de broadcast : 172.16.1.127

3. **Sous-réseau 3: Administratif**
   - Adresse du réseau : 172.16.1.128/26
   - Début de la plage IP disponible : 172.16.1.129
   - Fin de la plage IP disponible : 172.16.1.190
   - Adresse de broadcast : 172.16.1.191

4. **Sous-réseau 4: Technicien**
   - Adresse du réseau : 172.16.1.192/26
   - Début de la plage IP disponible : 172.16.1.193
   - Fin de la plage IP disponible : 172.16.1.254
   - Adresse de broadcast : 172.16.1.255

# Découpage asymétrique

### Déterminer la taille des sous-réseaux :

- **Sous-réseau 1 Informatique :** 50 équipements → Besoin de 2 bits supplémentaires pour adresses réseau et broadcast, donc 2^6 = 64 adresses.
- **Sous-réseau 2 Développement :** 12 équipements → Besoin de 2 bits supplémentaires pour adresses réseau et broadcast, donc 2^4 = 16 adresses.
- **Sous-réseau 3 Administratif :** 20 équipements → Besoin de 2 bits supplémentaires pour adresses réseau et broadcast, donc 2^5 = 32 adresses.
- **Sous-réseau 4 Technicien :** 15 équipements → Besoin de 2 bits supplémentaires pour adresses réseau et broadcast, donc 2^5 = 32 adresses.

### Calcul du CIDR :
- Pour 64 adresses : 2^6 = 64 → CIDR = /26 (32 - 6 = 26)
- Pour 32 adresses : 2^5 = 32 → CIDR = /27 (32 - 5 = 27)
- Pour 16 adresses : 2^4 = 16 → CIDR = /28 (32 - 4 = 28)

### Allocation des sous-réseaux :

1. **Sous-réseau 1 : Informatique**
   - Adresse du réseau : 172.16.1.0/26
   - Début de la plage IP disponible : 172.16.1.1
   - Fin de la plage IP disponible : 172.16.1.62
   - Adresse de broadcast : 172.16.1.63

2. **Sous-réseau 2 : Développement**
   - Adresse du réseau : 172.16.1.64/28
   - Début de la plage IP disponible : 172.16.1.65
   - Fin de la plage IP disponible : 172.16.1.78
   - Adresse de broadcast : 172.16.1.79

3. **Sous-réseau 3 : Administratif**
   - Adresse du réseau : 172.16.1.80/27
   - Début de la plage IP disponible : 172.16.1.81
   - Fin de la plage IP disponible : 172.16.1.110
   - Adresse de broadcast : 172.16.1.111

4. **Sous-réseau 4 : Technicien**
   - Adresse du réseau : 172.16.1.112/27
   - Début de la plage IP disponible : 172.16.1.113
   - Fin de la plage IP disponible : 172.16.1.126
   - Adresse de broadcast : 172.16.1.144
