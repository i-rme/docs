# Configuração

Você pode personalizar certos comportamentos do Flight definindo valores de configuração
através do método `set`.

```php
Flight::set('flight.log_errors', true);
```

A seguir está uma lista de todas as configurações disponíveis:

- **flight.base_url** - Substitui a URL base da requisição. (padrão: null)
- **flight.case_sensitive** - Corresponder a maiúsculas e minúsculas para URLs. (padrão: false)
- **flight.handle_errors** - Permitir que o Flight manipule todos os erros internamente. (padrão: true)
- **flight.log_errors** - Registrar erros no arquivo de log de erros do servidor web. (padrão: false)
- **flight.views.path** - Diretório contendo arquivos de modelo de visualização. (padrão: ./views)
- **flight.views.extension** - Extensão do arquivo de modelo de visualização. (padrão: .php)