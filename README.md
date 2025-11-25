# 🔐 Spring Boot JWT Authentication

Une implémentation complète d'un système d'authentification JWT avec Spring Boot 3 et Spring Security.

![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.0-brightgreen)
![Spring Security](https://img.shields.io/badge/Spring%20Security-6.0-blue)
![License](https://img.shields.io/badge/License-MIT-blue)

## 🚀 Fonctionnalités

- ✅ Authentification JWT stateless
- ✅ Sécurisation des endpoints API
- ✅ Configuration Spring Security
- ✅ Gestion des utilisateurs en mémoire
- ✅ Architecture modulaire et extensible
- ✅ Filtre de validation JWT
- ✅ Génération et signature de tokens
- ✅ Protection CSRF désactivée pour APIs REST
- ✅ Validation cryptographique HS256

## 🛠️ Technologies

- **Spring Boot** 3.2.0
- **Spring Security** 6
- **JJWT** 0.11.5
- **Java** 17
- **Maven**
- **Spring Web**

## 📁 Structure du Projet
src/main/java/com/example/demo/
├── config/
│ └── SecurityConfig.java # Configuration sécurité
├── controller/
│ └── AuthController.java # Endpoints d'authentification
├── filter/
│ └── JwtAuthFilter.java # Filtre validation JWT
├── model/
│ ├── AuthRequest.java # DTO requête auth
│ └── AuthResponse.java # DTO réponse auth
├── service/
│ ├── JwtService.java # Service gestion JWT
│ └── MyUserDetailsService.java # Service utilisateurs
└── Demo3Application.java # Classe principale

text

## 🏃‍♂️ Installation et Exécution

### Prérequis
- Java 17+
- Maven 3.6+

### 1. Cloner le projet
```bash
git clone https://github.com/Wijdaneh/spring-boot-jwt-authentication.git
cd spring-boot-jwt-authentication
2. Configurer l'application
Éditez src/main/resources/application.properties :

properties
app.jwt.secret=VotreSecretKeySuperSecure32CaracteresMinimum
app.jwt.expiration-ms=3600000
3. Lancer l'application
bash
mvn clean spring-boot:run
L'application sera accessible sur : http://localhost:8080

🔑 Utilisation
1. Authentification
bash
curl -X POST http://localhost:8080/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username": "user", "password": "password"}'
Réponse :

json
{
  "token": "eyJhbGciOiJIUzI1NiJ9..."
}
2. Accès aux endpoints protégés
bash
curl -X GET http://localhost:8080/api/hello \
  -H "Authorization: Bearer VOTRE_TOKEN_JWT"
Réponse :

json
{
  "message": "Bonjour, endpoint protégé OK 💺"
}
👤 Utilisateurs de Test
Username	Password	Rôle
user	password	USER
admin	admin123	ADMIN
🔒 Endpoints
Méthode	Endpoint	Accès	Description
POST	/api/auth/login	Public	Authentification et génération JWT
GET	/api/hello	Privé	Endpoint protégé de test
🛡️ Sécurité Implémentée
✅ Validation cryptographique des tokens JWT (HS256)

✅ Expiration configurable des tokens (1 heure par défaut)

✅ Protection contre les attaques CSRF (désactivée pour API)

✅ Filtrage des requêtes avec Spring Security

✅ Injection dans le contexte de sécurité Spring

✅ Vérification signature et expiration

🔄 Flux d'Authentification
text
1. Client → POST /auth/login (credentials)
2. Serveur → Validation credentials
3. Serveur → Génération JWT avec roles
4. Client → Reçoit token JWT
5. Client → GET /hello (Header: Bearer {token})
6. Serveur → Validation token → Réponse sécurisée
🧪 Testing
Test avec PowerShell
powershell
# Login
$response = Invoke-RestMethod -Uri "http://localhost:8080/api/auth/login" -Method POST -Headers @{"Content-Type"="application/json"} -Body '{"username": "user", "password": "password"}'

# Accès protégé
$protectedResponse = Invoke-RestMethod -Uri "http://localhost:8080/api/hello" -Method GET -Headers @{"Authorization"="Bearer $($response.token)"}
🤝 Contribution
Les contributions sont les bienvenues ! N'hésitez pas à :

Fork le projet

Créer une branche feature (git checkout -b feature/AmazingFeature)

Commit vos changes (git commit -m 'Add some AmazingFeature')

Push sur la branche (git push origin feature/AmazingFeature)

Ouvrir une Pull Request

📝 Licence
Ce projet est sous licence MIT. Voir le fichier LICENSE pour plus de détails.

👨‍💻 Auteur
Wijdane

GitHub: @Wijdaneh

🔮 Améliorations Futures
Implémentation de refresh tokens

Intégration avec base de données réelle

Gestion des rôles plus avancée

Logs d'audit détaillés

Rate limiting pour prévenir les attaques

Support OAuth2

Documentation API avec Swagger

⭐ N'oubliez pas de donner une étoile si ce projet vous a été utile !