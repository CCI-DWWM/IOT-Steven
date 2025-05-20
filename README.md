# IoT
## Liste des objets connectés autours de vous
- Porte de la fab<br>
- montre<br>
- portable<br>
- aspirateur robot<br>
- lave linge<br>
- sèche linge<br>
- ordinateur / tablette<br>
- chauffage / thermostat<br>
- store<br>
- cigarette électronique<br>
- voiture<br>
- moto<br>
- gourde<br>
- vélo<br>
- console jeux<br>
- bague<br>
- balance<br>
- chaussure / semelle<br>
- lunette<br>
- vêtements<br>
- fourchette<br>

## Mermaid WelcomerDoor
```mermaid
sequenceDiagram
participant Utilisateur
participant Smartphone
participant WelcomrCloud
participant Porte
participant Bluetooth
participant WiFi
participant GPS

Utilisateur->>Smartphone: Ouvre l'application Welcomr
Smartphone->>WelcomrCloud: Demande d'accès via /api/access/request
alt Accès confirmé
WelcomrCloud-->>Smartphone: Confirme l'accès via /api/access/confirm
Smartphone->>Bluetooth: Établit la connexion via /api/bluetooth/connect
alt Connexion Bluetooth réussie
Bluetooth-->>Smartphone: Confirme la connexion
Smartphone->>WiFi: Établit la connexion via /api/wifi/connect
alt Connexion WiFi réussie
WiFi-->>Smartphone: Confirme la connexion
Smartphone->>GPS: Récupère la position via /api/gps/location
alt Position GPS récupérée
GPS-->>Smartphone: Retourne la position
Smartphone->>Porte: Envoie la commande d'ouverture via /api/door/open
Porte-->>Smartphone: Confirme l'ouverture via /api/door/confirm
Smartphone-->>Utilisateur: Notifie l'ouverture de la porte
else Position GPS non disponible
Smartphone-->>Utilisateur: Erreur : Position GPS non disponible
end
else Connexion WiFi échouée
Smartphone-->>Utilisateur: Erreur : Connexion WiFi échouée
end
else Connexion Bluetooth échouée
Smartphone-->>Utilisateur: Erreur : Connexion Bluetooth échouée
end
else Accès non confirmé
WelcomrCloud-->>Smartphone: Erreur : Accès non confirmé
Smartphone-->>Utilisateur: Erreur : Accès non confirmé
end
```

## Code NodeRed

![image](https://github.com/user-attachments/assets/771a40a1-2749-42af-9f5f-94d808677b6b)
