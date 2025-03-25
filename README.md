# redpanda_sasl

Arrancar unicamente el contenedor del kafkaesque 
```
docker compose up -d redpanda-0
```

## Poner seguridad al kafka

Añadir los superusuarios
```
rpk cluster config set superusers ['usuario1']
```

Crear superusuario
```
rpk security user create usuario1 \
  -p 'CDaPnTjl9HDklvOTa21Gc16iUtSZSo' \
  --mechanism=SCRAM-SHA-256
```

Activar la seguridad del cluster
```
rpk cluster config set enable_sasl true
```

Comprobar la seguridad del cluster
```
rpk cluster config get sasl_mechanisms
```

Posteriormente hay que reiniciar el cluster
