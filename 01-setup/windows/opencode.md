# Установка OpenCode (Windows)

> Перед установкой убедитесь, что Node.js уже установлен (см. `01-nodejs.md`),
> если вы планируете способ через `npm`.

Выполните указанные команды в powershell или cmd

```powershell
npm install -g opencode-ai
```

Проверка:

```powershell
opencode --version
```
opencode --version выводит номер версии. Версия должна быть 2.x

## Если opencode не находится
Проверьте, что каталог установки добавлен в PATH. В случае npm —
убедитесь, что глобальные пакеты npm доступны в PATH (обычно
%APPDATA%\npm).
