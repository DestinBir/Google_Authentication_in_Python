<header>



# Implémentation de google authentification dans vos projet django avec python
## Implementation of google authentication in your django project using python

## Destin BIRINGANINE, _Backend Developer, Python Programmer_

</header>

<!--
  <<< Author notes: Step 1 >>>
  Choose 3-5 steps for your course.
  The first step is always the hardest, so pick something easy!
  Link to docs.github.com for further explanations.
  Encourage users to open new tabs for steps!
-->
> “Lorsqu'on s'occupe d'informatique il faut faire comme les canards... Paraître calme en surface et pédaler comme un forcené par en dessous. ”
> Richard Lallement

## 0. Quid authentification ?

### a.  Définition

L’***authentification*** est une procédure, par laquelle un système informatique certifie l’identité d’une personne ou d’un ordinateur. 
Le but de cette procédure est d’autoriser la personne ou l’ordi à accéder à certaines ressources sécurisées. 
Ainsi, il compare les informations données par l’utilisateur à celles se trouvant dans la base de données du système.
L’accès sera accordé uniquement si les informations sont identiques.

### b. Type 

Il existe 4 ***facteurs*** d’authentifications : Ce que l’on connait (***facteur mémoriel***),  Ce que l’on possède (***facteur matériel***), Ce que l’on est (***facteur corporel***), Ce que l’on sait faire (***facteur réactionnel***) et on peut toutefois parler du ***facteur immémorial***, Ce que l’on ne sait pas.

Grâce à ces différents facteurs d’identifications cités ci-dessus, des méthodes de vérifications ont été mises en place pour qualifier le degré d’authentification. C’est-à-dire que l’on peut combiner un ou deux facteurs pour renforcer la vérification.
Il existe 3 familles d’authentification : ***simple***, ***forte*** et ***unique***.

L’authentification simple ne repose que sur un seul facteur alors que l’authentification unique permet une seule authentification permettant ainsi d’accéder à plusieurs applications informatiques. Quant à l’authentification forte, elle repose sur deux facteurs ou plus.

> _***Pourquoi l’authentification google ?*** Un mot de passe pour toutes vos connexions
celui de votre compte google_

## 1. Quid Python et Django ?

***Python*** est un langage de programmation de haut niveau ou évolué, créé en 1991 par Guido Von Rossum.

***Python*** est un langage riche et pluridisciplinaire: Web, Software, Data Science et même le Mobile.

Ainsi, nous retrouvons ***Django*** comme un de ses librairies du web au côté de Fast API, Flask etc

***Django*** est une librairie de Python permettant de créer des systèmes ***ORM*** (Object Relational Management).

## 2. Implementation de google authentification

Google authentification permet de s’identifier sur un système informatique en se connectant uniquement sur son propre compte Google. 

Ceci, permet à l’utilisateur de bien sécuriser son identité, de gagner en temps  et surtout de n’avoir à garder qu’un seul mot de passe celui de son compte Google. Pour le développeur, il reçoit uniquement les informations dont il a besoin et dans le bon format.

Pré-requis: 
* Savoir créer et manipuler un projet web en Django
* Avoir un compte Google
* Connaître la programmation Python
* Connaitre le langage HTML
* Connaître le langage de Gabarit

Un guide étape par étape pour implementer google authentication


## Etape 0: 
Créer un projet web avec django, créer votre application, vos pages web pour la connexion, la page d’accueil ainsi que la création d’un super utilisateur permettant d'accéder à la page admin de votre site web.

_Visiter ce lien: https://docs.allauth.org/en/latest/installation/quickstart.html pour avoir acces à la documentation sur le package django allauth :wave:_

## Etape 1: Installation du package
Dans le terminal et surtout de préférence dans l’environnement virtuel du projet
```bash
(env) PS D:\projets\devFest> pip install django-allauth
```

## Etape 2: Configuration dans settings.py

```python
AUTHENTICATION_BACKENDS = [
    'django.contrib.auth.backends.ModelBackend',
    'allauth.account.auth_backends.AuthenticationBackend',
]

INSTALLED_APPS = [
    'django.contrib.auth',
    'django.contrib.messages',

    'allauth',
    'allauth.account',
    'allauth.socialaccount',
	
    'allauth.socialaccount.providers.google',
]

MIDDLEWARE = (
    "allauth.account.middleware.AccountMiddleware",
)

SOCIALACCOUNT_PROVIDERS = {
    'google': {
        'APP': {
            'client_id': '123', #provisoirement
            'secret': '456', #provisoirement
            'key': ''
        }
    }
}
```

## Etape 2: Configuration dans settings.py

```python
urlpatterns = [
    path('accounts/', include('allauth.urls')),
]
```

## Etape 3: Ajout parmi les liens: urls.py

```bash
(env) PS D:\projets\devFest> python manage.py makemigrations

(env) PS D:\projets\devFest> python manage.py migrate
```

## Etape 4: Creation de l’API google auth 

Link: https://console.cloud.google.com/apis/dashboard 
Nous pourrions y jeter un coup d’oeil à la fin de la présentation.
```python
SOCIALACCOUNT_PROVIDERS = {
    'google': {
        'APP': {
            'client_id': ' ', 
            'secret': ' ', 
            'key': ''
        }
    }
}
```
<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

Bibliographie
* https://www.syloe.com/glossaire/authentification/ 
* https://support.google.com/cloud/answer/10311615?hl=fr#user-type&zippy=%2Cinternal%2Cexternal 
* https://docs.allauth.org/en/latest/introduction/index.html 
* https://docs.allauth.org/ 
* https://cga-blog.vercel.app/ 

&copy; 2023 Code, Growth Alive  &bull; [MIT License](https://gh.io/mit)

</footer>
