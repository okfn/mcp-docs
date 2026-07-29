# Conectar a un servidor

Hay dos maneras de llevar las herramientas de un plugin a un servidor
en ejecución.

## Opción 1: pip install (plugins en Python)

El servidor escanea todos los paquetes de Python instalados en busca
de entry points `mcp_server` al arrancar. Así que conectar un plugin
es simplemente instalarlo en el mismo entorno:

```bash
uv pip install "git+https://github.com/okfn/mcp-server"
uv pip install "git+https://github.com/okfn/mcp-exampleplugin"
uv run mcp-server
```

## Opción 2: tool sources (repos de YAML)

Para repos de datasets declarativos en YAML, lístalos en el archivo
`deploy/tool_sources.yaml` del servidor. El servidor los clona y carga
los archivos YAML desde la ruta indicada:

```yaml
- name: mcp-dados-brasil
  repo: git@github.com:okfn/mcp-dados-brasil.git
  path: datasets     # folder inside the repo where the tools live
  ref: main
```

### Repos privados

Si el repo es privado, agrega una deploy key de solo lectura:

```yaml
  key: deploy/keys/mcp-dados-brasil-key
```

Genera el par de llaves, sube la mitad pública a las deploy keys del
repo en GitHub (acceso de lectura es suficiente), y coloca el archivo
privado en el servidor con permisos `600`:

```bash
ssh-keygen -t ed25519 -f keys/mcp-dados-brasil-key -N "" -C "deploy@mcp-server"
```

## Después de cambiar un plugin

Haz push al repo del plugin, y luego vuelve a traer los cambios /
reinicia en el servidor. Las herramientas se cargan una sola vez, al
arrancar.
