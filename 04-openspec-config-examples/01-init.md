# 1. Инициализация OpenSpec (`openspec init`)

Выполняется **в корне проекта**, рядом с `pom.xml`.

## 1.1 bash:
```bash
openspec init
```

init спросит, какие AI-инструменты вы используете. Выберите OpenCode.

Если хотите пропустить интерактивный выбор:

## 1.2 bash:
```bash
openspec init --tools opencode
```

## Что создаётся
После init в проекте появляются:

```text
openspec/
├── config.yaml      # проектный конфиг (schema, context, rules)
├── specs/           # спеки (пока пусто)
├── changes/         # in-motion изменения (пока пусто)
└── archive/         # завершённые изменения переезжают сюда
```

Плюс workflow-файлы (skills) в общей папке .agents/skills/, откуда
OpenCode их подхватывает.

- openspec/ создан в корне проекта
- openspec/config.yaml существует
- OpenCode выбран как AI-инструмент (в выводе init упоминается OpenCode)

## Если OpenCode не видит skills
Если ваш OpenCode работает в IDE, **перезапустите IDE после init**, чтобы
он подхватил новые skills. В терминальном OpenCode skills
доступны сразу.

## Безопасно ли запускать init повторно
Да. Повторный init «освежает» уже настроенные инструменты и добавляет новые,
если вы выбрали ещё какой-то AI-инструмент. Ваши правки в config.yaml
при этом не перезаписываются.
