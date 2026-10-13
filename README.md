# HW3: Seoul Bike Sharing Demand

## Датасет

**Назва:** Seoul Bike Sharing Demand

**Офіційне джерело:** UCI Machine Learning Repository
https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand

**Опис:** погодинні дані про оренду велосипедів у системі прокату Сеула разом із погодними показниками. Один рядок відповідає одній годині однієї доби. Період спостережень: з 01.12.2017 по 30.11.2018.

## Формування вибірки

Вибірка не формувалась: використано **повний файл** `SeoulBikeData.csv` без фільтрації, семплування чи випадкового відбору рядків. Файл завантажено у Colab, прочитано з `dtype=str` і `keep_default_na=False` (щоб нічого не перетворювалось при імпорті) та записано в staging-таблицю.

## Кількість рядків

| Шар | Таблиця | Рядків |
|---|---|---|
| Сирий файл | `SeoulBikeData.csv` | 8760 |
| Staging | `hw3_data_staging` | 8760 |
| Clean | `hw3_data_clean` | 8760 |

8760 = 365 днів × 24 години. Колонок у вихідному файлі: 14.

## Структура роботи

- `hw3_data_staging`: усі колонки `TEXT`, сирий імпорт.
- `hw3_data_clean`: типізована таблиця (`DATE`, `TIMESTAMPTZ`, `NUMERIC(p,s)`, `BOOLEAN`, `TEXT`) з `PRIMARY KEY`, `NOT NULL` та `CHECK`-обмеженнями.
- Перенесення даних виконано через `INSERT INTO ... SELECT` з очищенням.
- Інструменти: PostgreSQL, SQLAlchemy, pandas, Google Colab.