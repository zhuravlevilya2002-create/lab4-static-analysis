# Лабораторная работа №4. Статический анализ кода

**Студент:** И.А. Журавлёв
**Группа:** РИВ-430938у
**Дисциплина:** Проектирование информационных систем
**Преподаватель:** С.И. Тимошенко, доц., к.т.н.

## О работе

Освоение методики статического анализа Java-кода с использованием
инструмента **SpotBugs 4.10.4**. В работе выполнены три задания:

1. Воспроизведение примеров дефектов Java-кода из статьи
   «FindBugs помогает узнать Java лучше» (tagir_valeev, 2013)
   и их выявление анализатором.
2. Анализ проекта library (NetBeans-проект, аннотации JSR-305).
3. Анализ библиотеки Colt (численные методы и коллекции Java).

## Состав репозитория

- `src/TestTernary.java` — Пример 1: подводные камни тернарного оператора
- `src/TestDate.java` — Пример 2: небезопасный static DateFormat
- `src/TestBigDecimal.java` — Пример 3: BigDecimal(double) vs BigDecimal(String)
- `src/TestNewline.java` — Пример 4: \n в printf vs %n

## Найденные типы предупреждений (Задание 1)

| Тип | Класс | Пояснение |
|---|---|---|
| BX_UNBOXED_AND_COERCED_FOR_TERNARY_OPERATOR | TestTernary | Распаковка обёрток в тернарном операторе |
| BX_UNBOXING_IMMEDIATELY_REBOXED | TestTernary | Распаковка с последующим боксингом |
| BX_BOXING_IMMEDIATELY_UNBOXED | TestTernary | Боксинг с последующей распаковкой |
| NP_NULL_ON_SOME_PATH | TestTernary | Возможный NullPointerException |
| DM_NUMBER_CTOR, DM_FP_NUMBER_CTOR | TestTernary | Устаревшие конструкторы Number |
| STCAL_INVOKE_ON_STATIC_DATE_FORMAT_INSTANCE | TestDate | Небезопасный static DateFormat |
| DMI_BIGDECIMAL_CONSTRUCTED_FROM_DOUBLE | TestBigDecimal | Потеря точности в BigDecimal(double) |
| VA_FORMAT_STRING_USES_NEWLINE | TestNewline | \n вместо %n в printf |

## Инструмент

- **SpotBugs 4.10.4** — свободный статический анализатор байт-кода Java (LGPL), развитие проекта FindBugs.
- Сайт: https://spotbugs.github.io/

## Лицензия

Учебная работа. Код примеров воспроизводится в образовательных целях по статье «FindBugs помогает узнать Java лучше».
