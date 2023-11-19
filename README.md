
# Installation via Composer:


### Public repository:

https repo url:
> https://github.com/joussin/package-template.git


ssh repo url:
> git@github.com:joussin/package-template.git


### Private repository:

PRIVATE https repo url with credentials:

> https://{username}:{password}@github.com/joussin/package-template.git





### Liaison des packages:

https://getcomposer.org/doc/04-schema.md#package-links
https://getcomposer.org/doc/05-repositories.md


type `vcs` ou `git`:

````json
{
  "repositories": [
    {
      "type": "git",
      "url": "https://github.com/joussin/package-template.git"
    }
  ],
  "require": {
    "joussin/package-template": "dev-develop"
  }
}
````

type `composer`:

http://packages.example.com = http://packages.example.com/packages.json

````json
{
  "repositories": [
    {
      "type": "composer",
      "url": "http://packages.example.com"
    }
  ],
  "require": {
    "joussin/package-template": "dev-develop"
  }
}
````

Dans notre cas:

ex: https://raw.githubusercontent.com/joussin/package-template/develop/packages.json


````json
{
  "repositories": [
    {
      "type": "composer",
      "url": "https://raw.githubusercontent.com/joussin/package-template/develop/"
    }
  ],
  "require": {
    "joussin/package-template": "dev-develop"
  }
}
````

packages.json:

````json
{
  "packages": {
    "joussin/package-template": {
      "dev-develop": {
        "name": "joussin/package-template",
        "version": "dev-develop",
        "source": {
          "url": "https://github.com/joussin/package-template.git",
          "type": "git",
          "reference" : "develop"
        }
      },
      "0.0.1": {}
    }
  }
}
````
