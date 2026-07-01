# Источники паттернов (открытые)

Каталог ace-of-slops-ru собран из наблюдений редакторов, исследований детекторов и open-source humanizer-проектов. Список не претендует на полноту: LLM эволюционируют, паттерны дополняются.

## Первичные источники

| Источник | Что взято |
|----------|-----------|
| [ru.wikipedia: Признаки сгенерированности](https://ru.wikipedia.org/wiki/Википедия:Признаки_сгенерированности_текста) | символизм, СМИ-листы, поверхностный анализ, позитивизм, дидактика, «Заключение», «несмотря на…», деепричастия, правило трёх, меризмы, обтекаемые формулировки, жирный шрифт, listicle, тире |
| [en.wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) | структура каталога, content/style/language split |
| [ilyautov/humanizer-ru](https://github.com/ilyautov/humanizer-ru) | 52 паттерна, 12 категорий, жёсткие баны, фингерпринты 2025–2026, метрики perplexity/burstiness |
| [SergeNS-mne/humanizer-ru](https://github.com/SergeNS-mne/humanizer-ru) | 38 русских правил, voice calibration, document-level audit |
| [vc.ru: 38 паттернов](https://vc.ru/ai/2881358-kak-ubrat-patterny-ai-pisaniny-iz-russkogo-teksta) | канцелярит, родительные цепочки, «является», «данный», кальки, правило трёх, отрицательные параллелизмы, типографика |
| [vc.ru: 44 маркера](https://vc.ru/ai/2856452-kak-raspoznat-neyrosetevoy-tekst) | «не просто X, а Y», детекторы RuBERT, burstiness |
| [Хабр: маркеры через архитектуру LLM](https://habr.com/ru/articles/1033450/) | правило трёх, хеджи, промпт-запреты, перечисления |
| [Хабр: 7 метрик humanizer](https://habr.com/ru/articles/1030384/) | listicle-сигнатура, плотность тире, точка с запятой, AI-цитаты |
| [Грамота.ru](https://gramota.ru/journal/stati/tekhnologii/chem-sgenerirovannye-teksty-vydayut-sebya) | существительные vs глаголы, причастия, служебные слова, длина предложений 12–20 |
| [devswha/patina](https://github.com/devswha/patina) | структура skill, scoring, voice, ouroboros |

## Категории → файлы паттернов

| Категория | Файл |
|-----------|------|
| Язык, кальки, канцелярит | `patterns/ru-language.md` |
| Морфология, падежи | `patterns/ru-morphology.md` |
| Структура, listicle, ритм | `patterns/ru-structure.md` |
| Стиль, типографика, burstiness | `patterns/ru-style.md` |
| Содержание, фактура | `patterns/ru-content.md` |
| Filler, хайп | `patterns/ru-filler.md` |
| Тон, чатбот, 2025–2026 | `patterns/ru-communication.md` |

## Метрики детекторов (справочно)

- **Perplexity** — предсказуемость следующего слова; у LLM ниже
- **Burstiness** — разброс длины предложений/абзацев; у LLM ниже
- **MATTR** — лексическое разнообразие; у LLM ниже
- **Lexicon density** — частота AI-маркеров из `lexicon/ai-ru.md`
- **Морфология (RuBERT)** — падежные цепочки и согласования

Score в `core/scoring.md` — эвристика для редактуры, не вердикт детектора.

## Как предложить паттерн

Добавьте `custom/patterns/ru-my.md` или issue с примером «было → стало» и ссылкой на источник.
