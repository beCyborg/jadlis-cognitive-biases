Русский · [English](README.en.md)

# Проверка решения на 111 искажений

Плагин `cognitive-biases` для Claude Code. Команда — `/cognitive-biases`.

## Было → стало

Раздел заполняется по контракту README 2026-09 (фаза 3 плана «GitHub beCyborg как витрина Jadlis»).

## Как это работает

Доказательный советник по когнитивным искажениям: 111 искажений в пяти тирах по размеру эффекта и репликации, структурный Bias Scan ситуации, протокол дебайсинга по каждому искажению, разбор популярных мифов.

## Установка и первый запуск

```bash
claude plugin marketplace add https://github.com/beCyborg/jadlis-start.git
claude plugin install cognitive-biases@jadlis --config MEMORY_DIR=~/advisors-memory
```

## Границы, стоимость, обновление

Конспекты книг — производные работы, лицензии нет: см. [NOTICE.md](NOTICE.md). Правки принимаются только в источнике (`jadlis-advisors-source`), этот репо генерируется.

```bash
claude plugin marketplace update jadlis
claude plugin update cognitive-biases@jadlis
```
