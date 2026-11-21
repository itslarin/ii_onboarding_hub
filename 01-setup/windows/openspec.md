# Установка OpenSpec (Windows)

OpenSpec можно установить как standalone-бинарник (без Node.js) или через npm.
Выберите один способ.

## Вариант A: standalone-бинарник (без Node.js)

Откройте **PowerShell** и выполните:

```powershell
irm https://openspec.dev/cli/install.ps1 | iex
```

Скрипт скачает бинарник и предложит положить его в папку на PATH.
Если этого не произошло, переместите openspec.exe вручную в папку,
которая есть в PATH (например, %LOCALAPPDATA%\Programs\openspec).

Проверка:

```powershell
openspec --version
```
openspec --version выводит номер версии

## Вариант B: через npm
Требуется Node.js (см. 01-nodejs.md).

Выполните в powershell или cms
```powershell
npm install -g @fission-ai/openspec@latest
```

Проверка:

```powershell
openspec --version
```
openspec --version выводит номер версии

## Если openspec не находится
Проверьте, что папка с openspec.exe добавлена в PATH. Для npm-варианта
это обычно %APPDATA%\npm.
