# Plugins manuales

Estos JAR **no** van en el repositorio. Descargarlos y colocarlos aquí antes del primer `docker compose up`:

| Archivo | Origen |
|---------|--------|
| `GravesX.jar` | [Graves / GravesX en SpigotMC](https://www.spigotmc.org/resources/graves.74208/) |
| `SkinsRestorer.jar` | [SkinsRestorer en SpigotMC](https://www.spigotmc.org/resources/skinsrestorer.2124/) |

Opcional (anti-lag, no incluido por defecto):

| Archivo | Origen |
|---------|--------|
| `FixLag.jar` | [FixLag en Modrinth](https://modrinth.com/plugin/fixlag) |

El resto de plugins se descargan solos vía `SPIGET_RESOURCES` en `docker-compose.yaml`.
