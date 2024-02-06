# Pedidos

Flight encapsula a solicitação HTTP em um único objeto, que pode ser
acessado fazendo:

```php
$request = Flight::request();
```

O objeto de solicitação fornece as seguintes propriedades:

- **url** - O URL sendo solicitado
- **base** - O subdiretório pai do URL
- **method** - O método da solicitação (GET, POST, PUT, DELETE)
- **referrer** - O URL do referenciador
- **ip** - Endereço IP do cliente
- **ajax** - Se a solicitação é uma solicitação AJAX
- **scheme** - O protocolo do servidor (http, https)
- **user_agent** - Informações do navegador
- **type** - O tipo de conteúdo
- **length** - O comprimento do conteúdo
- **query** - Parâmetros da string de consulta
- **data** - Dados de postagem ou dados JSON
- **cookies** - Dados do cookie
- **files** - Arquivos enviados
- **secure** - Se a conexão é segura
- **accept** - Parâmetros de aceitação HTTP
- **proxy_ip** - Endereço IP do proxy do cliente
- **host** - O nome do host da solicitação

Você pode acessar as propriedades `query`, `data`, `cookies` e `files`
como arrays ou objetos.

Portanto, para obter um parâmetro da string de consulta, você pode fazer:

```php
$id = Flight::request()->query['id'];
```

Ou você pode fazer:

```php
$id = Flight::request()->query->id;
```

## Corpo da Solicitação RAW

Para obter o corpo bruto da solicitação HTTP, por exemplo, ao lidar com solicitações PUT,
você pode fazer:

```php
$body = Flight::request()->getBody();
```

## Entrada JSON

Se você enviar uma solicitação com o tipo `application/json` e os dados `{"id": 123}`
eles estarão disponíveis na propriedade `data`:

```php
$id = Flight::request()->data->id;
```