# Guía de Instalación para Windows

Esta guía explica los pasos necesarios para configurar el entorno de desarrollo en Windows para el proyecto curso-chatbots.

## Prerrequisitos

Antes de comenzar, asegúrate de tener instalado Python 3.12 o superior en tu sistema. Puedes descargarlo desde [python.org](https://www.python.org/downloads/).

## 1. Instalar uv

`uv` es una herramienta de gestión de entornos virtuales y paquetes de Python más rápida que pip. Para instalarla:

1. Abre PowerShell como administrador
2. Ejecuta el siguiente comando:

```powershell
irm https://astral.sh/uv/install.ps1 | iex
```

3. Verifica que uv se ha instalado correctamente:

```powershell
uv --version
```

## 2. Instalar Make para Windows

El proyecto utiliza Makefile para automatizar tareas. En Windows, necesitas instalar Make:

### Opción 1: Instalar Make con Chocolatey

1. Si no tienes Chocolatey instalado, [instálalo primero](https://chocolatey.org/install)
2. Luego, instala Make:

```powershell
choco install make
```

### Opción 2: Instalar Make con GnuWin32

1. Descarga el instalador desde [GnuWin32](https://gnuwin32.sourceforge.net/packages/make.htm)
2. Ejecuta el instalador y sigue las instrucciones
3. Añade la ruta a Make en tu PATH (generalmente `C:\Program Files (x86)\GnuWin32\bin`)

### Opción 3: Usar Make a través de Git Bash

Si tienes Git para Windows instalado, puedes usar Make desde Git Bash sin instalaciones adicionales.

## 3. Crear el entorno virtual

Una vez instalados uv y Make, crea el entorno virtual:

1. Abre PowerShell o Git Bash en la carpeta del proyecto
2. Ejecuta:

```
make venv
```

Esto creará un entorno virtual Python en la carpeta `.venv`.

## 4. Activar el entorno virtual

Para activar el entorno virtual en Windows:

### En PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### En CMD:

```cmd
.\.venv\Scripts\activate.bat
```

### En Git Bash:

```bash
source .venv/Scripts/activate
```

## 5. Instalar dependencias

Con el entorno virtual activado, instala todas las dependencias:

```
make install
```

Este comando:
- Actualizará pip a la última versión
- Instalará los paquetes listados en requirements.txt
- Instalará PyTorch con soporte para CUDA 12.1

## Comandos adicionales útiles

El Makefile ofrece varios comandos útiles para el desarrollo:

- `make format`: Formatea el código con Black e isort
- `make lint`: Ejecuta herramientas de linting
- `make test`: Ejecuta pruebas con pytest
- `make clean`: Elimina el entorno virtual y archivos temporales
- `make help`: Muestra todos los comandos disponibles

## Solución de problemas

### Política de ejecución en PowerShell

Si encuentras errores de política de ejecución en PowerShell, intenta ejecutar:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Path no encontrado

Si Windows no reconoce los comandos `uv` o `make`, asegúrate de que las rutas estén en tu PATH del sistema.
