# kobento-desktop

Kobento desktop players for [RemoteCompose](https://github.com/androidx/androidx/tree/androidx-main/compose/remote)
documents.

```
kobento-desktop/
├── viewer/    rcviewer — the macOS (Metal) / Linux (CPU/OpenGL) desktop viewer on the rcplayer
│              runtime from kobento-libs. Loads .rc/.rcd, animated images, video and zip decks;
│              screenshots, PDF and video export. See viewer/README.md.
└── compose/   a Compose Multiplatform desktop (JVM) player (Gradle). See compose/README.md.
```

## Build

rcviewer builds on the engine from [kobento-libs](https://github.com/camaelon/kobento-libs),
a sibling checkout (or `-DKOBENTO_LIBS_DIR=…`):

```sh
git clone https://github.com/camaelon/kobento-libs ../kobento-libs
cmake -S . -B build && cmake --build build -j
build/viewer/rcviewer ../kobento-libs/samples/balls_animation_example.rc
```

The Compose player: `cd compose && ./gradlew :composeApp:run`.

This repository is not endorsed or supported by Google.
