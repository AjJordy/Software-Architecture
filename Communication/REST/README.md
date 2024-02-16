# REST

## Verbs

- GET
- POST
- PUT
- DELETE
- OPTIONS

## HTTP Method Negotiation

```sh
OPTIONS /api/product HTTP/1.1
host: fullcycle.com.br
-------------------
HTTP/1.1 200 OK
Allow: GET, POST
```

## HTTP Content Negotiation 

```sh
GET /product
Accept: application/json
-------------------
HTTP/1.1 406 Not Acceptable
{
	"type": "http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html",
	"title": "Not Acceptable",
	"status": "406",
	"detail": "Cannot honor Accept type specified"
}
```

```sh
POST /product HTTP/1.1
Accept: application/json
Content-Type: application/json

{
	"name": "product",
}

------------

HTTP/1.1 415 Unsupported Media Type

{
	"type": "http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html",
	"title": "Unsupported Media Type",
	"status": "415",
	"detail": "Invalid content-type specified"
}
```

### Padrão HAL

```json
// Media type = application/hal+json
{
	"_links": {
		"self": {
			"href": "https://github.com/AjJordy", // Pagina atual
		}
	},
	"id": "AjJordy",
	"name":"Jordy",
	"_embedded": { // Ligação de relacionamento
		"familly": [
			{
				"_links": {
					"self": {
						"href": "https://github.com/test"						
					}
				},
				"id": "test",
				"name": "Teste"
			}
		]
	},
	"page_count": 0,
	"page_size": 25,
	"total_items": 0,
	"page": 0,
}
```

