# Añade al docker-compose del DNS otro servicio (contenedor) que haga la función de cliente.
- cliente:
    - container_name: cliente
    - image: alpine
    - platform: linux/amd64
    - tty: true
    - stdin_open: true
- dns:
    - 172.28.5.1
- networks:
    - alpine_subnet:
        - ipv4_address: 172.28.5.2

## Utiliza una imágen alpine
### Ayuda: repositorio con el docker-compose.yml
- docker compose up -d
- docker network create \
  --driver=bridge \
  --subnet=172.28.0.0/16 \
  --ip-range=172.28.5.0/24 \
  --gateway=172.28.5.254 \
  bind9_subnet

- docker exec -it servidor_asir2 bash

- apt update

- docker compose restart

- docker exec cliente_asir2 bash

- docker compose down

- $TTL 38400	; 10 hours 40 minutes
@		IN SOA	ns.asircastelao.int. some.email.address. (
				10000002   ; serial
				10800      ; refresh (3 hours)
				3600       ; retry (1 hour)
				604800     ; expire (1 week)
				38400      ; minimum (10 hours 40 minutes)
				)
@		IN NS	ns.asircastelao.int.
ns		IN A		172.22.5.1
test	IN A		172.22.5.4
www		IN A		172.22.5.7
roberto   IN A          172.22.5.9
alias	IN CNAME	test
texto	IN TXT		mensaje

# Instala, si es necesario, los paquetes necesarios para poder usar en el cliente los comandos de red del siguiente enlace.
- dig @172.22.5.1 test.asircastelao.int

- dig @172.22.5.1 roberto.asircastelao.int
### Comprueba su uso.
# Instala, si es necesario, para poder usar el comando 'dig'.

- apt isntall dnsuntils

# Configura el cliente para que su DNS sea el otro contenedor, modificando el resolv.conf o utilizando el fichero docker-compose.yml

- docker exec -it cliente_asir2 sh

- apk add --no-cache bind-tools

- docker exec -it servidor_asir2 bash

- ping 172.22.5.2

- apt update

- apt install -y iputils-ping

- ping 172.22.5.2

### Compruébalo con 'dig'.

- dig @172.22.5.1 roberto.asircastelao.int
