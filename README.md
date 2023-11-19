

# Installation des packages via ce faux 'registry':

Liste des packages & versions:

> https://raw.githubusercontent.com/joussin/package-registry/packages/packages.json

````json
{
  "repositories": [
    {
      "type": "composer",
      "url": "https://raw.githubusercontent.com/joussin/package-registry/packages/"
    }
  ],
  "require": {
    "joussin/package-template": "dev-develop"
  }
}
````

# Versioning & tagging:

### Créer un tag:

> git tag <tagname>


### Créer un tag annotés:

> git tag -a <tagname> -m "<msg>"
 

### Liste tag:

> git tag


### Se placer sur un tag:

> git checkout <tagname>


### Push tag:

> git push origin <tagname>

> Pour faire un push de plusieurs tags simultanément, transmettez l'option --tags à la commande git push. Lorsqu'un autre utilisateur clone un dépôt ou en fait un pull, il reçoit les nouveaux tags.

### Delete tag:

> git tag -d <tagname>


### ReTagging/Replacing old tags:

> git tag -a -f <tagname> <commit>

> Lorsque vous exécutez la commande ci-dessus, vous mappez le commit 15027957951b64cf874c3557a0f3547bd83b3ff6 à l'identifiant de tag v1.4. Tout contenu existant pour le tag v1.4 est écrasé.


### Example:

Simple tag:

````shell
git tag 0.0.1
git push origin 0.0.1
````

Tag annotés:

````shell
git tag -a v1.4 -m "my version 1.4"
git push origin v1.4
git tag -a -f v1.4 15027957951b64cf874c3557a0f3547bd83b3ff6
````

Modifier un tag annoté:

Dernier commit:
````shell
git rev-parse HEAD
````

Derniers commit: -n1 , -n2, -n3 ...
````shell
git log -n1 --format="%H"
````

````shell
git tag
git tag -a -f v1.4 15027957951b64cf874c3557a0f3547bd83b3ff6
````








---


# Documentation Composer & repositories:

https://getcomposer.org/doc/04-schema.md#package-links
https://getcomposer.org/doc/05-repositories.md
https://getcomposer.org/doc/04-schema.md



# Documentation Installation via Composer:


### Installation via repository url: 

Repositories `type` = `vcs` ou `git`:
````json
{
  "repositories": [
    {
      "type": "git",
      "url": "https://github.com/vendor/package-name.git"
    },
    {
      "type": "git",
      "url": "https://github.com/vendor-2/package-name-2.git"
    }
  ],
  "require": {
    "vendor/package-name": "dev-branch",
    "vendor-2/package-name-2": "0.0.1"
  }
}
````

Public repository `https` url:
> https://github.com/vendor/package-name.git

Public repository `ssh` url:
> git@github.com:vendor/package-name.git

Private repository `ssh` url with credentials:
> https://{username}:{password}@github.com/vendor/package-name.git


### Installation via registry ou liste des packages repository: 


Repositories `type` = `composer`:
````json
{
  "repositories": [
    {
      "type": "composer",
      "url": "http://packages.registry.com"
    }
  ],
  "require": {
    "vendor/package-name": "dev-branch",
    "vendor-2/package-name-2": "0.0.1"
  }
}
````

Public registry url:
> http://packages.registry.com


Avec à la racine, le fichier `packages.json`:
> http://packages.registry.com/packages.json:

Le fichier `packages.json` contient la liste des packages et leur versions:
````json
{
  "packages": {

    "vendor/package-name": {
      "dev-branch": {
        "name": "vendor/package-name",
        "version": "dev-branch",
        "source": {
          "url": "https://github.com/vendor/package-name.git",
          "type": "git",
          "reference" : "branch"
        }
      },
      "0.0.1": {
        "name": "vendor/package-name",
        "version": "0.0.1",
        "source": {
          "url": "https://github.com/vendor/package-name.git",
          "type": "git",
          "reference" : "0.0.1"
        }
      }
    },


    "vendor-2/package-name-2": {
      "dev-branch": {
        "name": "vendor-2/package-name-2",
        "version": "dev-branch",
        "source": {
          "url": "https://github.com/vendor-2/package-name-2.git",
          "type": "git",
          "reference" : "branch"
        }
      },
      "0.0.1": {
        "name": "vendor-2/package-name-2",
        "version": "0.0.1",
        "source": {
          "url": "https://github.com/vendor-2/package-name-2.git",
          "type": "git",
          "reference" : "0.0.1"
        }
      }
    }
    
  }
}
````
