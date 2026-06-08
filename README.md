# docker-minecraft

Servidor **Minecraft Java** (Paper **26.1.2**, Java **25**) con Docker Compose, basado en [itzg/docker-minecraft-server](https://github.com/itzg/docker-minecraft-server).

Survival PvP, whitelist, máximo 4 jugadores, piratas y premium (`ONLINE_MODE=false`).

## Inicio rápido

```bash
git clone https://github.com/avillalba96/docker-minecraft.git
cd docker-minecraft
cp .env.example .env          # editar MC_OPS y MC_WHITELIST
# Descargar JARs en host-plugins/ (ver host-plugins/README.md)
docker compose up -d
docker compose logs -f
```

## Conexión (MultiMC / launcher)

| Campo | Valor |
|-------|--------|
| **Host** | IP de la máquina donde corre Docker |
| **Puerto** | `9993` (mapeado a `25565` del contenedor) |
| **Protocolo** | **TCP** (Java Edition) |
| **Versión cliente** | `26.1.2` |

- **Piratas (cracked):** permitidos.
- **Premium:** también pueden entrar.
- **Whitelist:** solo nicks en `MC_WHITELIST` (archivo `.env`).
- **OP:** nick en `MC_OPS` (archivo `.env`).

## Objetivos del servidor

| Necesidad | Plugin |
|-----------|--------|
| Backups automáticos del mundo | QuickSave |
| Tumba con inventario al morir | GravesX |
| Ordenar cofres rápido | ChestSort |
| Talar árbol entero con hojas | TreeCapitator |
| Teleport entre jugadores | SimpleTpa |
| Skins sin cuenta premium | SkinsRestorer |
| Un durmiendo pasa la noche | OneSleep |
| Anti-lag granjas técnicas | FixLag *(documentado, no instalado)* |

## Stack

| Parámetro | Valor |
|-----------|--------|
| Imagen | `itzg/minecraft-server:2026.5.4-java25-alpine` |
| Minecraft | Paper `26.1.2` |
| Puerto | `9993:25565` (TCP) |
| Jugadores máx. | `4` |
| RAM JVM | `3G` |

## Plugins

**Spiget (automático):** QuickSave `75871`, ChestSort `59773`, TreeCapitator `18083`, OneSleep `96014`, SimpleTpa `64270`.

**Manuales (`host-plugins/`):** GravesX, SkinsRestorer.

**Solo documentado:** [FixLag](https://modrinth.com/plugin/fixlag) como reemplazo moderno del obsoleto NoLagg.

## Estructura

```
docker-minecraft/
├── docker-compose.yaml
├── .env.example          → copiar a .env (no se sube a git)
├── host-plugins/         → GravesX.jar, SkinsRestorer.jar
├── mc-paper/             → generado al correr (ignorado por git)
└── server-icon.png
```

## Gamerule manual: `max_entity_cramming` (granjas técnicas)

**No** se aplica desde `docker-compose`; el servidor usa el **valor por defecto de Minecraft** (24).

Si en el mundo técnico querés ajustarlo a mano (consola in-game o RCON):

```bash
/gamerule max_entity_cramming 24
```

Consultar valor actual:

```bash
/gamerule max_entity_cramming
```

Limita entidades por bloque; al superarlo, daño de asfixia. Útil en granjas con muchos mobs/ítems.

## Comandos útiles

```bash
docker compose up -d
docker compose logs -f
docker compose restart
docker compose down
```

## Referencias

- [itzg/docker-minecraft-server](https://github.com/itzg/docker-minecraft-server)
- [QuickSave](https://www.spigotmc.org/resources/quick-save-auto-world-backups.75871/)
- [ChestSort](https://www.spigotmc.org/resources/chestsort-api.59773/)
- [TreeCapitator](https://www.spigotmc.org/resources/treecapitator.18083/)
- [OneSleep](https://www.spigotmc.org/resources/onesleep.96014/)
- [SimpleTpa](https://www.spigotmc.org/resources/simpletpa.64270/)
- [GravesX](https://www.spigotmc.org/resources/graves.74208/)
- [SkinsRestorer](https://www.spigotmc.org/resources/skinsrestorer.2124/)
- [FixLag](https://modrinth.com/plugin/fixlag)
