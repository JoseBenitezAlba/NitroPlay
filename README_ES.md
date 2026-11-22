# NitroPlay

**PS5 Remoto.** Cliente comunitario de juego remoto para PlayStation 4 y PlayStation 5, basado en chiaki-ng. Incluye la interfaz en español, nitidez ajustable en Configuración → Vídeo y 30 estilos visuales: 29 temas y el estilo original.

En la aplicación, el nombre visible es **PS5 Remoto**.

## Temas

**Consolas:** PS5 clásico, PS4, PlayStation 3, PlayStation 2 y PlayStation 1 - clásico.

**Juegos:** Marvel's Spider-Man, God of War, Horizon, The Last of Us, Ghost of Tsushima, Astro Bot, Gran Turismo, Ratchet & Clank, Returnal, Uncharted, Bloodborne, Demon's Souls, Death Stranding, Crash Bandicoot, Spyro the Dragon, Metal Gear Solid, Final Fantasy VII, Tekken 3, Shadow of the Colossus, ICO, LittleBigPlanet, inFAMOUS, Killzone y Sackboy: A Big Adventure.

**Original:** chiaki-ng.

En **Configuración → General → Tema** puedes previsualizar y elegir un estilo. La elección se guarda para el siguiente inicio. Los motivos ilustrados son propios, están inspirados en cada juego y solo aparecen en el menú de consolas; no cubren la transmisión.

## Abrir en Arch Linux

Desde la carpeta del repositorio, una vez compilado:

```bash
./scripts/iniciar-es.sh
```

Esta compilación nativa utiliza la configuración nativa de Chiaki (`~/.config/Chiaki`). La configuración de la aplicación Flatpak se guarda por separado; el lanzador no la migra. Para vincular la consola hace falta el *PSN Account-ID* (o el *PSN Online-ID* en una PS4 con firmware anterior a 7.0) y un PIN de Remote Play de 8 dígitos.

El lanzador selecciona español por defecto. Si abres el binario directamente, la traducción puede seguir el idioma del sistema.

## Compilar en Arch Linux

Con las dependencias de desarrollo de chiaki-ng y las herramientas Linguist de Qt 6 instaladas:

```bash
cmake -S . -B build-es/cmake -G Ninja -DCMAKE_BUILD_TYPE=Release -DCHIAKI_USE_SYSTEM_CURL=ON -DCHIAKI_ENABLE_STEAMDECK_NATIVE=OFF -DCMAKE_POLICY_VERSION_MINIMUM=3.5
cmake --build build-es/cmake --parallel
ctest --test-dir build-es/cmake --output-on-failure
mkdir -p build-es/bin build-es/lib
cp build-es/cmake/gui/chiaki build-es/bin/
cp build-es/cmake/third-party/cpp-steam-tools/libcpp-steam-tools.so build-es/lib/
./scripts/iniciar-es.sh
```

La compilación depende de las versiones locales de Qt y de las bibliotecas multimedia. Vuelve a compilar después de actualizarlas.

## Windows y macOS

Todavía no hay paquetes publicados de esta versión para Windows ni macOS. Puedes compilarla desde este repositorio con CMake y Qt 6. La guía general de compilación está en [docs/diy/buildit.md](docs/diy/buildit.md): está en inglés y habla de chiaki-ng, pero el proceso es el mismo en este árbol de código.

La documentación original de instalación de chiaki-ng (paquetes de Flathub, Homebrew o Releases) no sirve para instalar NitroPlay: esos paquetes no incluyen la interfaz en español, la nitidez ni los temas de esta versión.

## Créditos y licencia

NitroPlay se publica bajo la GNU Affero General Public License v3.0 (AGPL-3.0). Es un proyecto comunitario no oficial basado en chiaki-ng y en Chiaki. No está afiliado, patrocinado ni certificado por Sony Interactive Entertainment.

La guía principal, con requisitos, primeros pasos y solución de problemas, está en [README.md](README.md).
