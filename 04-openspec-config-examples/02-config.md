
# Заполнение `openspec/config.yaml`

`config.yaml` — главный инструмент настройки OpenSpec под команду. Он
позволяет задать схему по умолчанию, внедрить контекст проекта (его увидит
AI при генерации **любого** артефакта) и добавить правила для конкретных
артефактов.

Откройте `openspec/config.yaml` и приведите к виду ниже. Замените
`your-org/shortlink` на фактический репозиторий, если хотите ссылаться
на него в контексте.

```yaml
schema: spec-driven

context: |
  Project: Short Link Service (демо-проект онбординга)
  Tech stack: Kotlin, Spring Boot, Maven
  Language level: Kotlin 2.x, JVM 21
  Build tool: Maven (pom.xml)
  Testing: JUnit 5, Spring Boot Test, MockMvc
  API style: REST, JSON
  Persistence: Spring Data JPA (H2 для локального запуска, PostgreSQL в проде)
  Code style: Kotlin Coding Conventions, constructor injection
  We value backwards compatibility for public APIs
  No field injection; DTOs separate from entities

rules:
  proposal:
    - Include rollback plan
    - Identify affected modules (controller / service / repository)
    - State what is explicitly out of scope
  specs:
    - Use Given/When/Then format for scenarios
    - Reference existing patterns before inventing new ones
  design:
    - Show sequence diagram for complex flows
    - List required database migrations (if any)
  tasks:
    - Break tasks into chunks of max 2 hours
    - End every task with a commit

operations:
  apply:
    guidance:
      - Run focused tests before the full suite
      - Keep test summaries concise
  archive:
    guidance:
      - Summarize the archive outcome before finishing
```

## Что здесь важно
- schema: spec-driven — базовая схема OpenSpec. Позволяет не писать
--schema spec-driven в каждой команде.

- context — внедряется во все артефакты. Сюда — только общепроектные
факты, которые нужны AI при создании спек, дизайна и задач. Лимит — 50 KB;
если превысить, значение будет проигнорировано с предупреждением.

- rules — правила для конкретных артефактов (proposal, specs,
design, tasks). Они появляются в промпте только при генерации
соответствующего артефакта.

- operations.apply.guidance / archive.guidance — необязательные
рекомендации для операций apply и archive. Не ограничивают содержимое
артефактов, а направляют поведение агента во время выполнения.

## Проверка
bash:
```bash
openspec config list
```

Команда покажет текущие настройки. Если config.yaml содержит синтаксическую
ошибку, OpenSpec может проигнорировать файл с предупреждением (кроме
openspec validate, который завершится с ошибкой).

- config.yaml заполнен
- openspec config list не показывает предупреждений о невалидном YAML
- В context нет секретов и временных заметок
