# ReciPro_macOS_memo
Method for running ReciPro on macOS（結晶学ソフトウェアReciProをmacOSで動作させる手法についてのメモ）

ReciPro: https://github.com/seto77/ReciPro

## Strategy
Sikarugir (Wine wrapper) + Mesa3D (for OpenGL-based functions)

Sikarugir: https://github.com/Sikarugir-App/Sikarugir

mesa-dist-win: https://github.com/pal1000/mesa-dist-win/

## Environment
M5 Macbook Pro (Tahoe 26.5)

## Step-by-step instructions (basic)
1. Install Sikarugir via homebrew
2. Create a new wrapper with the default template (`Template 1.0.11`) and the engine of `WS12WineCX24.0.7_7`.
3. Run Contents/Configure.app in the created wrapper, and install `gdiplus` via winetricks.
4. Open winecfg and change the OS from Windows 10 to Windows 7.
5. Extract the portable version of ReciPro (`ReciPro-v.4.938-win-x64-portable.zip`) and place the `ReciPro` folder in Contents/SharedSupport/prefix/drive_c.
6. Launch ReciPro.exe. The initialization will not be completed, but just check "Disable OpenGL" option and exit.
7. Launch ReciPro.exe again, then you can use basic functions.

## Advanced setting (OpenGL)
8. If you want to enable OpenGL-based functions, download `mesa3d-20.3.3-release-msvc.7z` from the mesa-dist-win repository and extract it. (I didn't test if newer versions work successfully.)
9. Copy all the files inside the `x64` folder and paste them into the `ReciPro` folder.
10. Open winecfg>library and set override for opengl32.dll. (i.e. enter 'opengl32' in the box, add it ignoring the warning message, and set the order of 'native, builtin').
11. Launch ReciPro.exe, remove the check from "Disable OpenGL" option, and exit.
12. Launch ReciPro.exe again.

## Known issues
- Some letters and arrows are not displayed correctly. 
- [Note on Jun 12, 2026] Problem with angstrom signs has been solved with ReciPro v4.938 by downloading .ttf files from the dejavu-fonts repository (https://github.com/dejavu-fonts/dejavu-fonts/releases/tag/version_2_37).


## Reference
- reddit post (https://www.reddit.com/r/macgaming/comments/126xvrq/running_modern_opengl_windows_games_on_crossover/?utm_source=app_first_navigation&mweb_loid=t2_2g2ymwdk4u)

