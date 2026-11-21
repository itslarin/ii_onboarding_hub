# Пример `opencode.json` для OpenAI-совместимого роутера

Файл `opencode.json` кладётся в **корень проекта** (рядом с `pom.xml`)
или в `~/.config/opencode/opencode.json` для глобальной настройки[reference:2].

Ниже — шаблон для кастомного провайдера. Замените `myrouter` на короткое
имя вашего роутера, `baseURL` — на актуальный эндпоинт из документации
роутера, а `model-id` — на доступную модель.

```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "myrouter": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "My Router",
      "options": {
        "baseURL": "https://api.example.com/v1",
        "apiKey": "{env:OPENCODE_API_KEY}"
      },
      "models": {
        "model-id": {
          "name": "Model display name"
        }
      }
    }
  },
  "model": "myrouter/model-id"
}
```

## Что здесь важно
- npm: "@ai-sdk/openai-compatible" — обязательный runtime для
эндпоинтов, которые отвечают по протоколу /v1/chat/completions
(большинство роутеров).

- baseURL должен заканчиваться на /v1 (или на путь, указанный
в документации роутера). Не вставляйте сюда главную страницу сайта.

- apiKey: "{env:OPENCODE_API_KEY}" — это ссылка на переменную
окружения, а не сам ключ. Значение переменной задаётся отдельно
(см. secrets.md).

- model в конце — модель по умолчанию в формате provider_id/model_id.
