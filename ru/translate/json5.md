# .json5

## Структура файла

json5-файл файл является расширением стандарта json и имеет [похожую структуру](json.md) с некоторыми дополнениями:
- Левая сторона может быть как в кавычках, так и без кавычек 
- Правая сторона может иметь переносы строк, который обозначается служебными символами `\n\`
- Левая и правая сторона может быть заключена как в двойные кавычки `"`, так и в одинарные `'`

```json5
{
    languageName: "Русский",
    application: {
        youHaveToRegister: 'Привет, {{ user_name }}! \n\
            \n\
            Нажми кнопку "ОБНОВИТЬ".'
    }
}
```

## Правила перевода

1. Правила перевода такие же как в [json](json.md)
2. Конец строки не переводится

## Пример правильного перевода

```json5
{
    languageName: "Russian",
    application: {
        youHaveToRegister: 'Hi {{user_name}}! \n\
            \n\
            Press button "UPDATE".'
    }
}
```

## Пример неправильного перевода

```
{
    "languageName": Russian, - Ошибка! пропали кавычки вокруг Russian
    "application": {
        "youHaveToRegister": 'Hi user_name! \n\ - Ошибка! пропали двойные скобки `{{ }}` вокруг user_name
                                                - Ошибка! пропал служебный символ переноса строки `\n\`
            Press button "UPDATE".' 
    }
}
```