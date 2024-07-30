<a name="readme-top"></a>
<!-- PROJECT LOGO --> 
<br />
<div align="center">
  <h1 style="font-size:50px">Boomi Atmosphere
    </h1>
  <p align="center">
    A data integration platform
    <br />
    <br />
    <a href="https://github.com/faraheloumi/Boomi-Atmosphere/issues/new?labels=bug&template=bug-report---.md">Report Bug</a>
    ·
    <a href="https://github.com/faraheloumi/Boomi-Atmosphere/issues/new?labels=enhancement&template=feature-request---.md">Request Feature</a>
  </p>
</div>


# Boomi Atmosphere
<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project">Introduction</a></li>
    <li><a href="#features">Outils et technologies</a></li>
    <li><a href="#installation">API des applications Microsoft</a></li>
    <li><a href="#contributing">Inscription de boomi atmosphere sur Microsoft Azure </a></li>
    <li><a href="#contributing">Configuration de Postman </a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

<!-- Introduction -->

## Introduction

Boomi offers an Integration Platform as a Service (iPaaS) that enables the connection of applications and data sources. It is a low-code development platform. The platform provides features for API lifecycle management and event-driven architecture for cloud integration. This includes an API proxy, an API gateway, and an API developer portal.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Outils et technologies -->

## Outils et technologies

1. **Boomi Atomsphere**
2. **API des applications Microsoft:** https://graph.microsoft.com/v1.0
3. **API Atlassian:** Jira: https://votredomaine.atlassian.net/rest/api/2/ and Confluence: https://votredomaine.atlassian.net/wiki/
4. **API BoondManager:** https://api.boondmanager.com
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- API des applications Microsoft -->

## API des applications Microsoft
`<https://graph.microsoft.com/v1.0>` est directement lié à Microsoft Azure. Microsoft Graph est un service de Microsoft qui permet d'accéder aux données et services de divers produits Microsoft, y compris ceux de la suite Microsoft 365 et Azure Active Directory. Voici comment ils sont connectés :
1. **Azure Active Directory (Azure AD):** Microsoft Graph permet de gérer les utilisateurs, les groupes, et les applications dans Azure AD. Cela inclut la gestion des identités, des accès, des rôles et des autorisations.
2. **Microsoft 365:** Les données et services de Microsoft 365, comme les emails d'Outlook, les fichiers de OneDrive, les calendriers, les contacts, et plus encore, sont accessibles via Microsoft Graph.
3. **Azure Services :** Microsoft Graph peut également interagir avec d'autres services Azure pour gérer les ressources et les périphériques, obtenir des informations de sécurité, et automatiser des processus en utilisant les données d'Azure.
En résumé, Microsoft Graph est une interface centrale qui permet d'interagir avec les données et les services de Microsoft, y compris ceux de Microsoft Azure et Microsoft 365. Les API et endpoints fournis par Microsoft Graph nécessitent des autorisations et des tokens d'accès gérés par Azure AD pour s'assurer que les requêtes sont sécurisées et que l'accès aux données est contrôlé.
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Inscription de boomi atmosphere sur Microsoft Azure -->

## Inscription de boomi atmosphere sur Microsoft Azure
1. Accédez à **Azure Active directory**.
2. Naviguez vers **Gérer**.
3. Sélectionnez **Inscriptions d'application**.
4. Configurez **Boomi Atmosphere**.
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Configuration de Postman -->

## Configuration de Postman

   **URL :** `https://login.microsoftonline.com/{tenant-id}/oauth2/v2.0/token`
   Remplacez `{tenant-id}` par votre ID de locataire.
   **Méthode :** `POST`
   **Headers :**
      - `Content-Type` : application/x-www-form-urlencoded
    **Body (x-www-form-urlencoded) :**
      - `client_id` : Utilisez l'ID d'application (client ID).
      - `scope` : `https://graph.microsoft.com/.default`
      - `client_secret` : Utilisez la valeur du secret client que vous avez copié.
      - `grant_type` : `client_credentials`

<!-- Configuration de Boomi -->

## Configuration de Boomi
1. **Configurer les Détails de la Connexion :**
   - **Name:** Donnez un nom à votre connexion (par exemple, "Microsoft Graph API").
   - **Connection Type :** Sélectionnez `HTTP Client`.
   - **URL :** Utilisez l'URL de base de Microsoft Graph : `https://graph.microsoft.com/v1.0`.
   - **Authentication Type :** Sélectionnez `OAuth 2.0`

1. **Configurer l'Authentification OAuth 2.0 :**
   - **Grant Type :** Sélectionnez `Client Credentials`.
   - **Client ID :** Utilisez l'ID d'application (client ID) que vous avez obtenu dans Azure AD.
   - **Client Secret :** Utilisez le secret client que vous avez généré dans Azure AD.
   - **Scope :** `https://graph.microsoft.com/.default`
   - **Access Token URL :** Utilisez l'URL suivante, en remplaçant {`tenant-id`} par votre ID de locataire : `https://login.microsoftonline.com/{tenant-id}/oauth2/v2.0/token`
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- L’utilité des paramètres -->

## L’utilité des paramètres

Ces paramètres sont essentiels pour l'authentification et l'autorisation OAuth 2.0 avec Azure Active Directory (Azure AD) pour accéder aux API de Microsoft Graph. Voici une explication de chacun :
1. **Client ID :** 
  -**Utilité :** Il s'agit de l'identifiant unique de l'application dans Azure AD. Il permet à     Azure AD de reconnaître l'application qui demande l'accès aux ressources protégées.
  -**Obtention :** Vous l'obtenez lors de l'enregistrement de votre application dans Azure AD.
2. **Client Secret :**
  - **Utilité :** C'est une clé secrète partagée entre votre application et Azure AD. Elle est   utilisée pour prouver l'authenticité de l'application lors des demandes de jetons d'accès.
  - **Obtention :** Vous le générez lors de l'enregistrement de l'application et devez le        conserver en sécurité.
3. **Scope :** 
  - **Utilité :** Il définit les permissions dont l'application a besoin.       
   `<https://graph.microsoft.com/.default>` indique que l'application demande toutes les     
   permissions qui lui ont été accordées lors de son enregistrement dans Azure AD.
  - **Spécification :** Cela permet de limiter l'accès aux données et fonctionnalités   
    spécifiques nécessaires pour l'application.
4. **Access Token URL :** 
  - **Utilité :** C'est l'URL à laquelle l'application envoie une demande pour obtenir un jeton d'accès OAuth 2.0. Ce jeton est ensuite utilisé pour accéder aux API protégées de Microsoft Graph.
  - **Personnalisation :** Vous devez remplacer {tenant-id} par l'ID de votre locataire Azure AD, ce qui permet de diriger la requête vers l'annuaire spécifique de votre organisation.
5. **tenant-id :**
  - **Utilité :** C'est l'identifiant unique de votre locataire Azure AD (votre organisation dans Azure). Il est nécessaire pour configurer correctement les URL d'autorisation et de jeton afin de pointer vers les ressources de votre locataire spécifique.
  - **Obtention :** Vous pouvez le trouver dans le portail Azure AD sous les propriétés de votre annuaire.

<!-- Utilisation globale de ces paramètres -->

## Utilisation globale de ces paramètres
Ces paramètres sont utilisés ensemble pour permettre à votre application d'obtenir un jeton d'accès via le flux d'authentification OAuth 2.0. Voici un résumé du processus :
1. **Enregistrement de l'application :** Vous enregistrez votre application dans Azure AD pour obtenir le Client ID et générer un Client Secret.
2. **Demande de jeton :** Votre application envoie une requête POST à l'URL du jeton (Access Token URL) avec le Client ID, Client Secret, Scope, et d'autres informations nécessaires.
3. **Obtention du jeton :** Si les informations fournies sont valides, Azure AD renvoie un jeton d'accès.
4. **Accès aux API :** Votre application utilise ce jeton d'accès pour faire des requêtes authentifiées aux API de Microsoft Graph et accéder aux ressources demandées.

<!-- Utilité de l'Access Token dans Boomi -->

## Utilité de l'Access Token dans Boomi

L'Access Token que vous avez généré est utilisé pour authentifier les demandes que votre application envoie à l'API Microsoft Graph. Lorsque vous utilisez Boomi pour interagir avec Microsoft Graph, Boomi nécessite cet Access Token pour pouvoir faire des appels authentifiés à l'API.

<!-- CONTACT -->

## Contact

Farah Elloumi- [@Farah Elloumi][linkedin-url] - farah.elloumi@supcom.tn <br/>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/farah-elloumi-735ab1269/

