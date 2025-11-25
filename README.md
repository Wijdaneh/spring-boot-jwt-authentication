Ok je vois exactement le problème 👌
Ton README est très bien mais **il est cassé juste à cause du Markdown mal structuré** (manque des ``` et mélange texte/code).

👉 Je te renvoie ci-dessous la version **100% corrigée et propre**, compatible GitHub (copier/coller direct) :

---

```markdown
# 🔐 Spring Boot JWT Authentication

Une implémentation complète d'un système d'authentification JWT avec Spring Boot 3 et Spring Security.

![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.0-brightgreen)
![Spring Security](https://img.shields.io/badge/Spring%20Security-6.0-blue)
![License](https://img.shields.io/badge/License-MIT-blue)

## 🚀 Fonctionnalités

- Authentification JWT stateless
- Sécurisation des endpoints API
- Configuration Spring Security
- Gestion des utilisateurs en mémoire
- Architecture modulaire et extensible
- Filtre de validation JWT
- Génération et signature de tokens
- Protection CSRF désactivée pour APIs REST
- Validation cryptographique HS256

## 🛠️ Technologies

- Spring Boot 3.2.0
- Spring Security 6
- JJWT 0.11.5
- Java 17
- Maven
- Spring Web

## 📁 Structure du Projet

```

src/main/java/com/example/demo/
├── config/
│   └── SecurityConfig.java             # Configuration sécurité
├── controller/
│   └── AuthController.java             # Endpoints d'authentification
├── filter/
│   └── JwtAuthFilter.java              # Filtre validation JWT
├── model/
│   ├── AuthRequest.java                # DTO requête auth
│   └── AuthResponse.java               # DTO réponse auth
├── service/
│   ├── JwtService.java                 # Service gestion JWT
│   └── MyUserDetailsService.java       # Service utilisateurs
└── Demo3Application.java               # Classe principale

````

## 🏃‍♂️ Installation et Exécution

### Prérequis
- Java 17+
- Maven 3.6+

### 1. Cloner le projet
```bash
git clone https://github.com/Wijdaneh/spring-boot-jwt-authentication.git
cd spring-boot-jwt-authentication
````

### 2. Configurer l'application

Modifier le fichier :

`src/main/resources/application.properties`

```properties
app.jwt.secret=VotreSecretKeySuperSecure32CaracteresMinimum
app.jwt.expiration-ms=3600000
```

### 3. Lancer l'application

```bash
mvn clean spring-boot:run
```

Application disponible sur :
[http://localhost:8080](http://localhost:8080)

---

## 🔑 Utilisation

### 1. Authentification

```bash
curl -X POST http://localhost:8080/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username": "user", "password": "password"}'
```

Réponse :

```json
{
  "token": "eyJhbGciOiJIUzI1NiJ9..."
}
```

### 2. Accès aux endpoints protégés

```bash
curl -X GET http://localhost:8080/api/hello \
  -H "Authorization: Bearer VOTRE_TOKEN_JWT"
```

Réponse :

```json
{
  "message": "Bonjour, endpoint protégé OK 💺"
}
```

---

## 👤 Utilisateurs de Test

| Username | Password | Rôle  |
| -------- | -------- | ----- |
| user     | password | USER  |
| admin    | admin123 | ADMIN |

---

## 🔒 Endpoints

| Méthode | Endpoint        | Accès  | Description                       |
| ------- | --------------- | ------ | --------------------------------- |
| POST    | /api/auth/login | Public | Authentification & génération JWT |
| GET     | /api/hello      | Privé  | Test token JWT                    |

---

## 🛡️ Sécurité Implémentée

* Validation cryptographique HS256
* Expiration configurable des tokens (1h)
* Protection CSRF désactivée (API REST)
* Filtrage des requêtes JWT
* Vérification signature + expiration
* Injection dans le SecurityContext Spring

---

## 🔄 Flux d'Authentification

```
1. Client → POST /auth/login (credentials)
2. Serveur → Validation credentials
3. Serveur → Génération JWT avec roles
4. Client → Reçoit token JWT
5. Client → GET /hello (Header: Bearer {token})
6. Serveur → Validation token → Réponse OK
```

---

## 🧪 Testing (PowerShell)

```powershell
# Login
$response = Invoke-RestMethod -Uri "http://localhost:8080/api/auth/login" -Method POST -Headers @{"Content-Type"="application/json"} -Body '{"username": "user", "password": "password"}'

# Accès protégé
$protectedResponse = Invoke-RestMethod -Uri "http://localhost:8080/api/hello" -Method GET -Headers @{"Authorization"="Bearer $($response.token)"}
```

---

## 🤝 Contribution

1. Fork le projet
2. Créer une branche feature
3. Commit
4. Push
5. PR

---

## 📝 Licence

Ce projet est sous licence MIT.

---

## 👨‍💻 Auteur

Wijdane
GitHub: @Wijdaneh

---

## 🔮 Améliorations futures

* Refresh tokens
* Connexion avec base de données
* Gestion avancée des rôles
* Logs d’audit avancés
* Rate limiting
* Support OAuth2
* Documentation Swagger

---

⭐ N'oubliez pas de donner une étoile si ce projet vous a été utile !

```