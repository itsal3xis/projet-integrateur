# Livrable 6 – Plan d'adressage IP

## Sous-réseaux et VLANs

| Nom VLAN        | ID  | CIDR              | Passerelle       |
|-----------------|-----|-------------------|------------------|
| Corpo HQ        | 10  | 192.168.10.0/24   | 192.168.10.1     |
| Succursale MTL  | 20  | 192.168.20.0/24   | 192.168.20.1     |
| Succursale LVL  | 30  | 192.168.30.0/24   | 192.168.30.1     |
| DMZ             | 40  | 192.168.40.0/24   | 192.168.40.1     |
| IoT             | 50  | 192.168.50.0/24   | 192.168.50.1     |
| Management      | 60  | 192.168.60.0/24   | 192.168.60.1     |
| Wi-Fi publique  | 100 | 192.168.100.0/24  | 192.168.100.1    |
| Wi-Fi corpo     | 110 | 192.168.110.0/24  | 192.168.110.1    |
| VPN             |  x  | 192.168.120.0/24  | 192.168.120.1    |
| FAI             | 460 | 206.167.46.0/24   | 206.167.46.1    |

## VLAN Corpo HQ (ID 10)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| PFsense          | 192.168.10.1       | Statique |
| VM-AD/DNS        | 192.168.10.10      | Statique |
| VM-VEEAM         | 192.168.10.103     | Statique |
| PCs Admin        | DHCP (.100-.200)   | DHCP     |

## VLAN Succursale MTL (ID 20)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| pfSense          | 192.168.20.1       | Statique |
| PCs employés     | DHCP (.5-.200)     | DHCP     |

## VLAN Succursale LVL (ID 30)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| pfSense          | 192.168.30.1       | Statique |
| PCs employés     | DHCP (.5-.200)     | DHCP     |

## VLAN DMZ (ID 40)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| PFsense          | 192.168.40.1       | Statique |
| Web              | 192.168.40.10      | Statique |

## VLAN IoT (ID 50)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| PFsense          | 192.168.50.1       | Statique |
| Caméras IP       | DHCP (.5-.200)     | DHCP     |

## VLAN Management (ID 60)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| PFsense          | 192.168.60.1       | Statique |
| Switch HQ        | 192.168.60.2       | Statique |
| AP 1             | 192.168.60.10      | Statique |
| AP 2             | 192.168.60.20      | Statique |
| Unifi            | 192.168.60.5       | Statique |


## VLAN Wi-Fi publique (ID 100)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| PFsense          | 192.168.100.1      | Statique |
| Connexions       | DHCP (.5-.200)     | DHCP     |

## VLAN Wi-Fi corpo (ID 110)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| PFsense          | 192.168.110.1      | Statique |
| Connexions       | DHCP (.5-.200)    | DHCP     |

## VLAN VPN (ID 120)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| PFsense          | 192.168.120.1      | Statique |
| Connexions VPN   | DHCP (.2-.200)     | DHCP     |

## VLAN FAI (ID 460)

| Appareil/Service | Adresse IP         | Mode     |
|------------------|--------------------|----------|
| pfSense WAN      | 206.167.46.254     | Statique |
| Routeur FAI      | 206.167.46.1       | Statique |
