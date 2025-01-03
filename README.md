# Multimedia

# Проектная структура

Данный репозиторий содержит следующие компоненты:

## Папка `data`
Папка `data` содержит датасеты, которые используются для анализа и выполнения лабораторных работ.

## Папка `labs`
Папка `labs` включает в себя лабораторные работы, каждая из которых представлена отдельным файлом.

## Файл `labs.ipynb`
Файл `labs.ipynb` объединяет все лабораторные работы в один Jupyter Notebook для удобства выполнения и проверки.

---

## Выбор метрик

### Для классификации:
В таблице для задач классификации указаны значения **F1-score**, так как она учитывает баланс между точностью (*precision*) и полнотой (*recall*).

### Для регрессии:
Для регрессии в таблице указаны **MAE (Mean Absolute Error)** в качестве основной метрики. Причины:
- **MAE** показывает среднюю ошибку в тех же единицах, что и целевая переменная, что делает её легко интерпретируемой.  
- Данные моего набора включают цены автомобилей в индийских лакхах (*Lakh*, где **1 Lakh = 100,000 индийских рупий**). Для понимания в рублях:
  - На декабрь 2024 года курс составляет примерно **1 INR ≈ 1.13 RUB**.
  - Таким образом, **1 Lakh ≈ 113,000 рублей**.  
  Например, значение **MAE = 2.5** означает, что в среднем модель ошибается на 2.5 Lakh, что примерно эквивалентно **282,500 рублей**.

---

## Таблица 1. Метрика качества на тестовом наборе данных

| Алгоритм           | Задача           | Бейзлайн     | Улучшенный бейзлайн | Самостоятельная реализация алгоритма | Улучшенная Самостоятельная реализация алгоритма |
|---------------------:|:------------------:|:----------------:|:---------------------:|:---------------------------------------:|:---------------|
| **KNN**            | классификация (F1)   |      0.7220          |    0.7356                 |       0.7220               |     0.7671     |
|                     | регрессия     (MAE)   |         2.2733       |       1.5649              |           2.2738                            |      1.5587          |
| **Линейные модели** | классификация  (F1)   |        0.7786        |      0.7206               |          0.7621                             |    0.7506      |
|                     | регрессия     (MAE)    |      4.0184          |         2.2134            |           3.9653                            |    2.2124    |
| **Решающее дерево** | классификация  (F1)   |         0.7282       |       0.7277              |         0.7228                              |   0.7382    |
|                     | регрессия    (MAE)     |       2.1894         |       1.7250              |           2.1929                            |     2.0484   |
| **Случайный лес**   | классификация   (F1)  |        0.7675        |        0.7891             |               0.7659                        |   0.7934     |
|                     | регрессия   (MAE)      |        1.6492        |         1.2796            |             2.7901                          |    2.3272       |
| **Градиентный бустинг** | классификация (F1) |     0.7937           |         0.7521            |           0.8000                            |      0.7847  |
|                     | регрессия   (MAE)      |        1.933        |       1.1508              |           1.9350                            |      1.1080       |
### Общие выводы

Улучшенные бейзлайны в задачах регрессии почти всегда показывают значительное снижение MAE, особенно для таких алгоритмов, как KNN, решающее дерево и градиентный бустинг, тогда как в классификации результаты улучшений менее стабильны и иногда уступают исходным версиям, например, у линейных моделей и градиентного бустинга. Самостоятельные реализации часто близки к базовым показателям, но их улучшенные версии дают наибольший прирост, особенно в регрессии. Среди алгоритмов лучшими оказались случайный лес и градиентный бустинг, которые стабильно показывают высокие результаты в обеих задачах. В то же время линейные модели и KNN демонстрируют менее стабильные улучшения. В целом, улучшения эффективнее для регрессии, а ансамблевые методы лучше справляются со сложными зависимостями.

