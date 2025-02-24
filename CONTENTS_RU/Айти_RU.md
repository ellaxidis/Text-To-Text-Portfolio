🤖 **Qwen AI**

---

## 📌 **Роль: Программист**

📝 **Задание: Написать код на Python для анализа данных о продажах компании Apple за последние пять лет (2020-2025)**

---

# Программа анализа продаж компании "Apple" за последние пять лет

Для написания кода, мы будем следовать этапам разработки программного обеспечения, начиная с анализа требований и заканчивая созданием продукта. Процесс включает несколько ключевых шагов: анализ данных, использование библиотек для обработки (NumPy и Pandas), поиск закономерностей (сезонность, тренды, аномалии) и представление результатов в виде графиков и таблиц.

**Вот пример структурированной программы на Python, которая выполняет указанные требования:**

```python
# Импорт необходимых библиотек
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Загрузка данных из CSV-файла
def load_data(filepath):
    """
    Функция для загрузки данных из файла.
    :param filepath: Путь к файлу с данными
    :return: DataFrame с данными
    """
    data = pd.read_csv(filepath)
    return data

# Предварительная обработка данных
def preprocess_data(data):
    """
    Обработка данных: удаление пропущенных значений, преобразование типов данных.
    :param data: Исходные данные
    :return: Обработанные данные
    """
    # Преобразование даты в формат datetime
    data['Date'] = pd.to_datetime(data['Date'])
    # Удаление строк с пропущенными значениями
    data.dropna(inplace=True)
    return data

# Анализ трендов
def analyze_trends(data):
    """
    Анализ трендов продаж во времени.
    :param data: Данные для анализа
    :return: DataFrame с трендами
    """
    # Группировка данных по годам и месяцам для выявления трендов
    trends = data.groupby([data['Date'].dt.year, data['Date'].dt.month])['Sales'].mean()
    return trends

# Выявление сезонности
def analyze_seasonality(data):
    """
    Выявление сезонных колебаний в продажах.
    :param data: Данные для анализа
    :return: DataFrame с сезонностью
    """
    # Группировка данных по месяцам для анализа сезонности
    seasonality = data.groupby(data['Date'].dt.month)['Sales'].mean()
    return seasonality

# Определение аномалий
def detect_anomalies(data):
    """
    Выявление аномалий в данных.
    :param data: Данные для анализа
    :return: Список аномальных точек
    """
    mean = np.mean(data['Sales'])
    std_dev = np.std(data['Sales'])
    anomalies = data[(data['Sales'] > mean + 3 * std_dev) | (data['Sales'] < mean - 3 * std_dev)]
    return anomalies

# Визуализация результатов
def plot_results(trends, seasonality, anomalies):
    """
    Построение графиков для трендов, сезонности и аномалий.
    :param trends: Тренды продаж
    :param seasonality: Сезонность продаж
    :param anomalies: Аномалии в данных
    """
    fig, ax = plt.subplots(3, 1, figsize=(10, 15))

    # График трендов
    trends.plot(ax=ax[0], title='Тренды продаж', ylabel='Средние продажи')

    # График сезонности
    seasonality.plot.bar(ax=ax[1], title='Сезонность продаж', ylabel='Средние продажи')

    # График аномалий
    ax[2].scatter(anomalies['Date'], anomalies['Sales'], color='red')
    ax[2].set_title('Аномалии в продажах')
    ax[2].set_ylabel('Продажи')

    plt.tight_layout()
    plt.show()

# Основная функция
def main():
    # Путь к файлу с данными
    filepath = 'apple_sales_data.csv'

    # Загрузка и предварительная обработка данных
    data = load_data(filepath)
    data = preprocess_data(data)

    # Анализ данных
    trends = analyze_trends(data)
    seasonality = analyze_seasonality(data)
    anomalies = detect_anomalies(data)

    # Вывод результатов в виде таблицы
    print("Таблица трендов:")
    print(trends)
    print("\nТаблица сезонности:")
    print(seasonality)
    print("\nТаблица аномалий:")
    print(anomalies)

    # Визуализация результатов
    plot_results(trends, seasonality, anomalies)

if __name__ == "__main__":
    main()
```

Этот код демонстрирует процесс разработки программного обеспечения, где каждый компонент хорошо документирован и разделен на логические части, что делает его легко читаемым и поддерживаемым. Программа использует библиотеки NumPy и Pandas для анализа данных, а также matplotlib для визуализации результатов.

*Примечание: Все данные представлены исключительно в ознакомительных целях и не являются официальной финансовой отчетностью компании Apple.*

---

## 📌 **Роль: UX/UI-дизайнер**

📝 **Задание: Создать макет мобильного приложения для онлайн-магазина одежды**

---

# Макет мобильного приложения онлайн-магазина одежды

## Главный экран (Главная)
| Заголовок      | Описание                                                                 |
|----------------|--------------------------------------------------------------------------|
| **Логотип**    | Расположен в верхней части, слева. Легкий и минималистичный стиль.       |
| **Поиск**      | Центральная позиция в шапке. Простой прямоугольник с иконкой поиска.     |
| **Категории**  | Горизонтальный скроллбар с категориями товаров.                          |
| **Баннер**     | Плавная анимация смены изображений. Актуальные предложения или новинки.   |

## Навигационное меню
| Иконка         | Название           | Описание                                         |
|----------------|--------------------|--------------------------------------------------|
| 🏠             | Главная            | Ведет на главную страницу.                      |
| 🔍             | Поиск              | Открывает расширенный поиск.                    |
| 💬             | Чат                | Доступ к клиентской поддержке или чату.          |
| 🛒             | Корзина            | Содержит выбранные товары.                      |
| 📱             | Профиль            | Настройки аккаунта и история заказов.            |

## Экран категории
| Заголовок      | Описание                                                                 |
|----------------|--------------------------------------------------------------------------|
| **Название категории** | Большой текст, выделенный пастельным цветом.                       |
| **Список товаров**    | Карточки товаров с изображением, названием и ценой.                  |
| **Фильтры**          | Выпадающее меню для сортировки по размеру, цвету, цене.              |

## Экран товара
| Заголовок      | Описание                                                                 |
|----------------|--------------------------------------------------------------------------|
| **Изображение** | Большая картинка товара с возможностью зума.                             |
| **Описание**   | Краткое описание товара, материалы, уход.                                |
| **Цена**       | Ярко выделена, рядом кнопка "Добавить в корзину".                        |
| **Размеры**    | Выбор размера через круглые кнопки.                                       |

## Корзина
| Заголовок      | Описание                                                                 |
|----------------|--------------------------------------------------------------------------|
| **Список**     | Все добавленные товары с возможностью удаления.                           |
| **Итого**      | Общая сумма заказа с кнопкой "Перейти к оплате".                         |

## Профиль
| Заголовок      | Описание                                                                 |
|----------------|--------------------------------------------------------------------------|
| **Информация** | Личные данные пользователя.                                              |
| **Заказы**     | История покупок с фильтром по статусам.                                  |
| **Настройки**  | Изменение пароля, уведомлений и других параметров.                       |

### Цветовая палитра
- Основной фон: Белый (#FFFFFF)
- Акценты: Мягкий голубой (#AED9E0), светло-зеленый (#C5E1A5)
- Текст: Темно-серый (#424242)

### Примечания
- Все элементы управления размещены в нижней части экрана для удобства использования одной рукой.
- Использован минимализм в дизайне для создания легкости и свежести.

Этот макет создан с учетом современных трендов UI/UX-дизайна 2025 года, таких как минимализм, удобство использования и эстетичность оформления.

---

&copy; 2025 Елизавета Тепляшина. Все материалы оригинальны и используются в ознакомительных целях. 18+
