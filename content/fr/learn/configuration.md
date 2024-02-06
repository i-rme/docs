# Configuration

Vous pouvez personnaliser certains comportements de Flight en définissant des valeurs de configuration via la méthode `set`.

```php
Flight::set('flight.log_errors', true);
```

Ce qui suit est une liste de tous les paramètres de configuration disponibles :

- **flight.base_url** - Remplace l'URL de base de la requête. (par défaut : null)
- **flight.case_sensitive** - Correspondance sensible à la casse pour les URL. (par défaut : false)
- **flight.handle_errors** - Permet à Flight de gérer toutes les erreurs en interne. (par défaut : true)
- **flight.log_errors** - Journalise les erreurs dans le fichier journal d'erreurs du serveur web. (par défaut : false)
- **flight.views.path** - Répertoire contenant les fichiers de modèle de vue. (par défaut : ./views)
- **flight.views.extension** - Extension de fichier de modèle de vue. (par défaut : .php)