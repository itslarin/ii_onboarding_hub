# Пример `AGENTS.md` для проекта на Kotlin + Spring Boot + Maven

`AGENTS.md` — это файл с правилами для OpenCode. Он кладётся в корень
проекта и **версионируется в Git**, чтобы вся команда работала с одними
и теми же инструкциями[reference:7].

Создать заготовку можно командой `/init` внутри OpenCode — она просканирует
репозиторий и предложит черновик. Но можно начать и с ручного шаблона.

```markdown
# Short Link Service — Kotlin / Spring Boot / Maven

## Project Structure
- `src/main/kotlin/` — основной код на Kotlin
- `src/main/resources/` — `application.yml`, миграции, статические ресурсы
- `src/test/kotlin/` — тесты (JUnit 5, Spring Boot Test)
- `pom.xml` — сборка Maven

## Build & Test Commands
- Сборка: `mvn clean package`
- Тесты: `mvn test`
- Запуск локально: `mvn spring-boot:run`
- Проверка стиля (если подключён): `mvn checkstyle:check`

## Code Standards
- Язык: Kotlin, стиль — официальный Kotlin Coding Conventions.
- Spring Boot: конструкторная инъекция зависимостей, без field injection.
- DTO — отдельно от entity; не возвращать entity из контроллеров.
- Исключения — через `@ControllerAdvice`, не ловить `Exception` без нужды.
- Логирование — через SLF4J (`LoggerFactory.getLogger`), не `println`.

## Testing
- Новый эндпоинт → минимум один интеграционный тест (`@SpringBootTest` + `MockMvc`).
- Тесты называть по шаблону: `should_<expected>_when_<condition>`.
- Перед коммитом: `mvn test` должен проходить.

## Maven Conventions
- Версии зависимостей — в `pom.xml`, без «плавающих» версий в коде.
- Плагины: `spring-boot-maven-plugin`, `kotlin-maven-plugin` уже настроены;
  не менять их конфигурацию без необходимости.
```

## Зачем это нужно
OpenCode будет учитывать эти правила при генерации кода и предложениях
по изменениям.

Файл общий для команды: если правило меняется — меняется в одном месте
и попадает в ревью, как обычный код.

Если у вас уже есть CLAUDE.md, OpenCode может использовать его как
fallback, но AGENTS.md имеет приоритет.
