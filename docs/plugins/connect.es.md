# Conectar un plugin a un servidor

Conectar un plugin es simplemente instalarlo en el entorno del
servidor. Al arrancar, el servidor escanea todos los paquetes
instalados y registra sus herramientas:

```bash
uv pip install "git+https://github.com/okfn/mcp-server"
uv pip install "git+https://github.com/okfn/mcp-exampleplugin"
uv run mcp-server
```

Los plugins en Python se descubren a través de su entry point
`mcp_server`. Los paquetes llamados `mcp_server_*` que traen [datasets
en YAML](yaml-datasets.md) se descubren por convención de nombre.

Para un repo de plugin privado, instala desde una URL git que tu
entorno pueda alcanzar, por ejemplo sobre SSH con una deploy key de
solo lectura.

Así funciona también el [despliegue de
producción](../operations/deployment.md): la imagen del servidor
instala los paquetes de plugins al momento de construirse.

## Después de cambiar un plugin

Haz push al repo del plugin, luego reinstala el paquete y reinicia el
servidor. Las herramientas se cargan una sola vez, al arrancar.
