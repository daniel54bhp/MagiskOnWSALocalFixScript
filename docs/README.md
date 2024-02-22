#SPANISH/ESPAÑOL
# Magisk en WSA (con Google Apps)

:warning: Para los desarrolladores de forks: Por favor, no compilen usando GitHub Actions, ya que GitHub contará el uso de GitHub Actions de sus forks contra este repositorio principal, lo que puede provocar que este repositorio principal sea deshabilitado por el personal de GitHub como [MagiskOnWSA](https://github.com/LSPosed/MagiskOnWSA) debido a numerosos forks compilando GitHub Actions, y contando el uso de Actions de los forks contra este repositorio principal.

## Soporte para generar desde estos sistemas

- Linux (x86_64 o arm64)

  Se requieren las siguientes dependencias:

  | DistrOS             |                                                         |            |              |                    |               |              |
  |:-------------------:|---------------------------------------------------------|------------|--------------|--------------------|---------------|--------------|
  | Debian              | `lzip patchelf e2fsprogs python3 aria2 attr unzip sudo` | `whiptail` | `qemu-utils` | `python3-venv`     | `python3-pip` | `p7zip-full` |
  | openSUSE Tumbleweed | Igual que arriba                                       | `dialog`   | `qemu-tools` | `python3-venvctrl` | Igual que arriba                |
  | Arch                | Igual que Debian                                       | `libnewt`  | `qemu-img`   |  Igual que Debian   | `python-pip`  | `p7zip`      |

  Se utiliza la biblioteca `requests` de python3.

  Versión de Python ≥ **3.7.2**.

  - Uso recomendado

    - Ubuntu (Puedes usar [WSL2](https://apps.microsoft.com/store/search?publisher=Canonical%20Group%20Limited))

      Listo para usar directamente.

    - Debian (Puedes usar [WSL2](https://apps.microsoft.com/store/detail/debian/9MSVKQC78PK6))

      Listo para usar directamente.

    - openSUSE Tumbleweed (Puedes usar [WSL2](https://apps.microsoft.com/store/detail/opensuse-tumbleweed/9MSSK2ZXXN11))

      Listo para usar directamente.

    `run.sh` manejará automáticamente todas las dependencias.

    No es necesario escribir ningún comando.

## Características

- Integra Magisk y GApps en unos pocos clics en cuestión de minutos.
- Mantén cada compilación actualizada.
- Soporte tanto para ARM64 como para x64.
- Soporte para MindTheGapps.
- Elimina Amazon Appstore.
- Soluciona el problema del diálogo de VPN que no se muestra (usa nuestra [aplicación VpnDialogs](https://github.com/LSPosed/VpnDialogs)).
- Añade la función de administración de dispositivos.
- Instalación no supervisada.
- Activa automáticamente el modo de desarrollador en Windows 11.
- Actualización a la nueva versión preservando datos con un script de un clic.
- Fusiona todos los paquetes de idiomas.

## Guía de texto

1. Dale una estrella (si te gusta).
2. Clona el repositorio localmente:

   ```bash
   git clone https://github.com/LSPosed/MagiskOnWSALocal.git --depth 1
   ```

3. Ejecuta `cd MagiskOnWSALocal`.
4. Ejecuta `./scripts/run.sh`.
5. Selecciona la versión de WSA y su arquitectura (en su mayoría x64).
6. Selecciona la versión de Magisk.
7. Elige qué marca de GApps quieres instalar:
   - MindTheGapps

     No hay otra variante que podamos elegir.
8. Selecciona la solución de root (none significa sin root).
9. Si estás ejecutando el script por primera vez, tomará algo de tiempo completarlo. Después de que el script se complete, se generarán dos nuevas carpetas llamadas `output` y `download` en la carpeta `MagiskOnWSALocal`. Ve a la carpeta `output`. Mientras ejecutas el script `./run.sh` en el paso 3, si seleccionaste `Sí` para `¿Quieres comprimir la salida?` entonces en la carpeta `output` verás un archivo comprimido llamado `WSA-with-magisk-stable-MindTheGapps_2207.40000.8.0_x64_Release-Nightly`o si no habrá una carpeta con el nombre `WSA-with-magisk-stable-MindTheGapps_2207.40000.8.0_x64_Release-Nightly`. Si hay una carpeta, ábrela y pasa al paso 10. NOTA: El nombre del archivo comprimido o la carpeta generada en la carpeta `output` puede ser diferente para ti. Dependerá de las elecciones hechas al ejecutar `./run.sh`.
10. Extrae el archivo comprimido y abre la carpeta creada después de la extracción del archivo.
11. Aquí busca el archivo `Run.bat` y ejecútalo.
    - Si previamente tienes una instalación de MagiskOnWSA, desinstalará automáticamente la anterior mientras **preserva todos los datos del usuario** e instalará la nueva, así que no te preocupes por tus datos.
    - Si tienes una instalación oficial de WSA, primero debes desinstalarla. (En caso de que quieras preservar tus datos, puedes hacer una copia de seguridad de `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache\userdata.vhdx` antes de la desinstalación y restaurarla después de la instalación.)
    - Si las ventanas emergentes desaparecen **sin pedir permiso administrativo** y WSA no se instala correctamente, deberías ejecutar manualmente `Install.ps1` como Administrador:
        1. Presiona `Win+x` y selecciona `Windows Terminal (Admin)`.
        2. Ingresa `cd "{X:\ruta\a\tu\carpeta\extraída}"` y presiona `Enter`, y recuerda reemplazar `{X:\ruta\a\tu\carpeta\extraída}` incluyendo las `{}`, por ejemplo `cd "D:\wsa"`
        3. Ingresa `PowerShell.exe -ExecutionPolicy Bypass -File .\Install.ps1` y presiona `Enter`.
        4. El script se ejecutará y se instalará WSA.
        5. Si esta solución no funciona, tu PC no es compatible con WSA.
12. Se lanzará Magisk/Play Store. Disfruta instalando LSPosed-Zygisk con Zygisk habilitado o Riru y LSPosed-Riru.

---

## P

reguntas frecuentes

<details open>

- ¿Puedo eliminar la carpeta instalada?

  No.

- ¿Cómo puedo actualizar WSA a una versión más nueva?

  1. Actualiza los scripts de compilación:

      ```bash
      git pull
      ```

      Para más información sobre el uso de git, consulta <https://git-scm.com/book>

  2. Vuelve a ejecutar el script, reemplaza el contenido de tu instalación anterior y vuelve a ejecutar `Install.ps1`. No te preocupes, tus datos se conservarán.

- ¿Cómo puedo obtener el logcat de WSA?

  `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalState\diagnostics\logcat`

- ¿Cómo puedo actualizar Magisk a una versión más nueva?

  Haz lo mismo que al actualizar WSA.

- ¿Cómo pasar Play Integrity (anteriormente conocido como SafetyNet)?

  Como todos los demás emuladores, no hay forma.

- ¿La virtualización no está habilitada?

  `Install.ps1` te ayuda a habilitarlo si no está habilitado. Después de reiniciar, vuelve a ejecutar `Install.ps1` para instalar WSA. Si aún no funciona, debes habilitar la virtualización en la BIOS. Es una historia larga, así que pregunta a Google para obtener ayuda.

- ¿Cómo remontar el sistema como lectura-escritura?

  No hay forma en WSA ya que está montado como solo lectura por Hyper-V. Puedes modificar el sistema haciendo un módulo de Magisk. O modifica directamente el sistema.img. Pregunta a Google para obtener ayuda.

- No puedo `adb connect localhost:58526`, ¿qué hago?

  Asegúrate de que el modo desarrollador esté habilitado. Si el problema persiste, verifica la dirección IP de WSA en la página de configuración e intenta `adb connect ip:5555`.

- ¿Por qué el módulo en línea de Magisk está vacío?

  Magisk elimina activamente el repositorio de módulos en línea. Puedes instalar el módulo localmente o mediante `adb push module.zip /data/local/tmp` y `adb shell su -c magisk --install-module /data/local/tmp/module.zip`.

- ¿Puedo usar Magisk v23.0 estable o una versión inferior?

  No. Magisk tiene errores que impiden que se ejecute en WSA. Magisk v24+ los ha solucionado. Así que debes usar Magisk v24 o posterior.

- ¿Cómo me deshago de Magisk?

  Elige `none` como solución de root.

- ¿Cómo instalar GApps personalizados?

  [Tutorial](Custom-GApps.md)

- ¿Dónde puedo descargar MindTheGapps?

  Puedes descargarlo desde aquí [MindTheGapps](https://androidfilehost.com/?w=files&flid=322935) ([mirror](http://downloads.codefi.re/jdcteam/javelinanddart/gapps)).

  Ten en cuenta que no hay una compilación previa para x86_64, así que debes compilarla tú mismo ([Repositorio](https://gitlab.com/MindTheGapps/vendor_gapps)).

  O puedes descargar el paquete construido para 12.1 y 13 para x86_64 desde [esta página](https://sourceforge.net/projects/wsa-mtg/files/x86_64/).

- ¿Puedo cambiar de OpenGApps a MindTheGapps y mantener los datos de usuario en una compilación anterior?

  No. Debes borrar los datos después de cambiar la marca de GApps. De lo contrario, verás que las GApps instaladas no son reconocidas.

- WSA con OpenGApps integrado no arranca.

  OpenGApps aún no ha lanzado una versión construida para Android 12L y 13, solo construida para Android 11, que puede no ser compatible y por lo tanto causar bloqueos. Considera cambiar a MindTheGapps.

- ¿Cómo instalar KernelSU?

  [Tutorial](KernelSU.md)

</details>

---

## Créditos

- [StoreLib](https://github.com/StoreDev/StoreLib): API para descargar WSA
- [Magisk](https://github.com/topjohnwu/Magisk): La solución de root más famosa en Android
- [The Open GApps Project](https://opengapps.org): Una de las soluciones de paquetes de Google Apps más famosas
- [WSA-Kernel-SU](https://github.com/LSPosed/WSA-Kernel-SU) y [kernel-assisted-superuser](https://git.zx2c4.com/kernel-assisted-superuser/): El kernel `su` para depurar la Integración de Magisk
- [WSAGAScript](https://github.com/ADeltaX/WSAGAScript): El primer script de integración de GApps para WSA
- [erofs-utils](https://github.com/sekaiacg/erofs-utils): `erofs-utils` precompilado con erofsfuse habilitado

_El repositorio se proporciona como una utilidad._

_Android es una marca comercial de Google LLC. Windows es una marca comercial de Microsoft Corporation._


#ENGLISH

# Magisk on WSA (with Google Apps)

:warning: For fork developers: Please don't build using GitHub Actions, as GitHub will count your forked GitHub Actions usage against this upstream repository, which may cause this upstream repository gets disabled by GitHub staff like [MagiskOnWSA](https://github.com/LSPosed/MagiskOnWSA) because of numerous forks building GitHub Actions, and counting the forks' Action usage against this upstream repository.

## Support for generating from these systems

- Linux (x86_64 or arm64)

  The following dependencies are required:

  | DistrOS             |                                                         |            |              |                    |               |              |
  |:-------------------:|---------------------------------------------------------|------------|--------------|--------------------|---------------|--------------|
  | Debian              | `lzip patchelf e2fsprogs python3 aria2 attr unzip sudo` | `whiptail` | `qemu-utils` | `python3-venv`     | `python3-pip` | `p7zip-full` |
  | openSUSE Tumbleweed | Same as above                                           | `dialog`   | `qemu-tools` | `python3-venvctrl` | Same as above                |
  | Arch                | Same as Debian                                          | `libnewt`  | `qemu-img`   |  Same as Debian    | `python-pip`  | `p7zip`      |

  The python3 library `requests` is used.

  Python version ≥ **3.7.2**.

  - Recommended use

    - Ubuntu (You can use [WSL2](https://apps.microsoft.com/store/search?publisher=Canonical%20Group%20Limited))

      Ready to use right out of the box.

    - Debian (You can use [WSL2](https://apps.microsoft.com/store/detail/debian/9MSVKQC78PK6))

      Ready to use right out of the box.

    - openSUSE Tumbleweed (You can use [WSL2](https://apps.microsoft.com/store/detail/opensuse-tumbleweed/9MSSK2ZXXN11))

      Ready to use right out of the box.

    `run.sh` will handle all dependencies automatically.

    No need to type any commands.

## Features

- Integrate Magisk and GApps in a few clicks within minutes
- Keep each build up to date
- Support both ARM64 and x64
- Support MindTheGapps
- Remove Amazon Appstore
- Fix VPN dialog not showing (use our [VpnDialogs app](https://github.com/LSPosed/VpnDialogs))
- Add device administration feature
- Unattended installation
- Automatically activates developers mode in Windows 11
- Update to the new version while preserving data with a one-click script
- Merged all language packs

## Text Guide

1. Star (if you like).
2. Clone the repo to local:

   ```bash
   git clone https://github.com/LSPosed/MagiskOnWSALocal.git --depth 1
   ```

3. Run `cd MagiskOnWSALocal`.
4. Run `./scripts/run.sh`.
5. Select the WSA version and its architecture (mostly x64).
6. Select the version of Magisk.
7. Choose which brand of GApps you want to install:
   - MindTheGapps

     There is no other variant we can choose.
8. Select the root solution (none means no root).
9. If you are running the script for the first time, it will take some time to complete. After the script completes, two new folders named `output` and `download` will be generated in the `MagiskOnWSALocal` folder. Go to the `output` folder. While running the `./run.sh` script in the step 3, if you selected `Yes` for `Do you want to compress the output?` then in `output` folder you will see a compressed file called `WSA-with-magisk-stable-MindTheGapps_2207.40000.8.0_x64_Release-Nightly`or else there will be folder with the `WSA-with-magisk-stable-MindTheGapps_2207.40000.8.0_x64_Release-Nightly`. If there is a folder open it and skip to step 10. NOTE: The name of compressed file or the folder generated in the `output` folder may be different for you. It will be dependent on the choices made when executing `./run.sh`.
10. Extract the compressed file and open the folder created after the extraction of the file.
11. Here look for file `Run.bat` and run it.
    - If you previously have a MagiskOnWSA installation, it will automatically uninstall the previous one while **preserving all user data** and install the new one, so don't worry about your data.
    - If you have an official WSA installation, you should uninstall it first. (In case you want to preserve your data, you can backup `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache\userdata.vhdx` before uninstallation and restore it after installation.)
    - If the popup windows disappear **without asking administrative permission** and WSA is not installed successfully, you should manually run `Install.ps1` as Administrator:
        1. Press `Win+x` and select `Windows Terminal (Admin)`.
        2. Input `cd "{X:\path\to\your\extracted\folder}"` and press `enter`, and remember to replace `{X:\path\to\your\extracted\folder}` including the `{}`, for example `cd "D:\wsa"`
        3. Input `PowerShell.exe -ExecutionPolicy Bypass -File .\Install.ps1` and press `Enter`.
        4. The script will run and WSA will be installed.
        5. If this workaround does not work, your PC is not supported for WSA.
12. Magisk/Play Store will be launched. Enjoy by installing LSPosed-Zygisk with Zygisk enabled or Riru and LSPosed-Riru.

---

## FAQ

<details open>

- Can I delete the installed folder?

  No.

- How can I update WSA to a newer version?

  1. Update build scripts:

      ```bash
      git pull
      ```

      For more usage of git, referred to <https://git-scm.com/book>

  2. Rerun the script, replace the content of your previous installation and rerun `Install.ps1`. Don't worry, your data will be preserved.

- How can I get the logcat from WSA?

  `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalState\diagnostics\logcat`

- How can I update Magisk to a newer version?

  Do the same as updating WSA.

- How to pass Play Integrity (formerly known as SafetyNet)?

  Like all the other emulators, no way.

- Virtualization is not enabled?

  `Install.ps1` helps you enable it if not enabled. After rebooting, rerun `Install.ps1` to install WSA. If it's still not working, you have to enable virtualization in BIOS. That's a long story so ask Google for help.

- How to remount the system as read-write?

  No way in WSA since it's mounted as read-only by Hyper-V. You can modify the system by making a Magisk module. Or directly modify the system.img. Ask Google for help.

- I cannot `adb connect localhost:58526`, what to do?

  Make sure developer mode is enabled. If the issue persists, check the IP address of WSA on the setting page and try `adb connect ip:5555`.

- Why the Magisk online module is empty?

  Magisk actively removes the online module repository. You can install the module locally or by `adb push module.zip /data/local/tmp` and `adb shell su -c magisk --install-module /data/local/tmp/module.zip`.

- Can I use Magisk v23.0 stable or a lower version?

  No. Magisk has bugs preventing itself from running on WSA. Magisk v24+ has fixed them. So you must use Magisk v24 or later.

- How can I get rid of Magisk?

  Choose `none` as the root solution.

- How to install custom GApps?

  [Tutorial](Custom-GApps.md)

- Where can I download MindTheGapps?

  You can download from here [MindTheGapps](https://androidfilehost.com/?w=files&flid=322935) ([mirror](http://downloads.codefi.re/jdcteam/javelinanddart/gapps)).

  Note that there is no x86_64 pre-build, so you need to build it by yourself ([Repository](https://gitlab.com/MindTheGapps/vendor_gapps)).

  Or you can download the built package for 12.1 and 13 for x86_64 from [this page](https://sourceforge.net/projects/wsa-mtg/files/x86_64/).

- Can I switch OpenGApps to MindTheGapps and keep user data in a previous build?

  No. You should wipe data after changing the GApps brand. Otherwise, you will find that the installed GApps are not recognized.

- WSA with OpenGApps integrated fails to start.

  OpenGApps has not yet released a version built for Android 12L and 13, only built for Android 11, which may not be compatible and thus cause crashes. Consider switching to MindTheGapps.

- How to install KernelSU?

  [Tutorial](KernelSU.md)

</details>

---

## Credits

- [StoreLib](https://github.com/StoreDev/StoreLib): API for downloading WSA
- [Magisk](https://github.com/topjohnwu/Magisk): The most famous root solution on Android
- [The Open GApps Project](https://opengapps.org): One of the most famous Google Apps packages solution
- [WSA-Kernel-SU](https://github.com/LSPosed/WSA-Kernel-SU) and [kernel-assisted-superuser](https://git.zx2c4.com/kernel-assisted-superuser/): The kernel `su` for debugging Magisk Integration
- [WSAGAScript](https://github.com/ADeltaX/WSAGAScript): The first GApps integration script for WSA
- [erofs-utils](https://github.com/sekaiacg/erofs-utils): Pre-build `erofs-utils` with erofsfuse enabled

_The repository is provided as a utility._

_Android is a trademark of Google LLC. Windows is a trademark of Microsoft Corporation._
