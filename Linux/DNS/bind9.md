---
title: Bind9 - DNS Server y tus propios ns servers
author: Julian Marcos
lang: es

toc: False
---
# Añadir un **dominio**
Añade al archivo named.conf.local
```
zone "dominio.es" IN {
	type master;
	file "/etc/bind/zones/dominio.es.zone";
};
```
Luego copia /etc/bind/db.empty a la nueva carpeta /etc/bind/zones/dominio.es.zone
en el archivo /etc/bind/zones/dominio.es.zone remplaza localhost con el nombre del dominio

# Poner entradas DNS
Usos:


- Queremos añadir a el dominio.es el registro txt "DNS for dominio.es"
```
@	IN	TXT	"DNS for dominio.es"

```

- Queremos añadir a el dominio.es el registro a del servidor de git como git.dominio.es
```
git	IN	A	10.0.4.253
```

- Queremos añadir un registro CNAME para www.dominio.es que apunte a lo mismo que dominio.es
```
www.dominio.es.	IN	CNAME	dominio.es.
```

- Queremos añadir un registro MX para el correo de dominio.es.
```
@	IN	MX	10	dominio.es.
```

# Peculiaridades

- **El archivo necesita tabs**

- Tienes que restartear bind9 para que coja la nueva config.

- El @ es como el fqdn del dominio.

- Puedes crear varios subdominios sin limite como algunos provedores y no tiene por que ser externo
puede ser una maquina de dns para la red 10.0.0.0/8 o de 192.168.0.0/24.
