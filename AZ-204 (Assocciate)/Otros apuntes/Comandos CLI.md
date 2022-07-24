[Documentación Microsoft](https://docs.microsoft.com/es-es/azure/virtual-machines/linux/cli-manage)

# Inicio

Los comandos del CLI de Azure relacionados con sus productos deben empezar con `az` seguido del tipo de recurso sobre el que vamos a realizar la acción requerida (`group`, `webapp`, `vm` ...)
---
---
---

# Creación de un recurso

Normalmente los recursos se crean de la siguiente forma (sustituyendo las <>):

`az <recurso> create --name <nombre> --location <zona geografica> --resource-group <nombre del grupo>`


---
---
---

# Información adicional sobre la salida

`-o`
`--output`

Indica que queremos especificar la forma en la que se imprime la información

## Formas de imprimir la salida

- `tsv` ->  formato tabular
- `table` -> formato tabla
- `list` -> formato lista

---
---
---

## Consulta de Runtime

`az webapp list-runtimes --os-type <sistema operativo>`

> NOTA: Runtime es el conjunto de lenguajes y frameworks compatibles con el sistema operativo
