## 1. Создание класса "Technic"(main.py)
### Требования
Необходимо создать класс "Technic" с тремя параметрами: название, цена и наличие(True, False). С помощью
тернарного оператора по цене определить товар в категорию "Бюджетный"/"Дорогой". 
! Важно, необходимо ограничить добавление других наборов атрибутов и методов.


### Создание объекта класса "Technic"
`laptop = Technic("Ноутбук Acer", 35000, True)`

### Определение категории товара
```
 category = laptop.get_category()
 print(category) # Бюджетный
 ```
- Методы класса
get_category()
Определяет категорию товара на основе цены. Возвращает строку "Бюджетный" или "Дорогой".

## Атрибуты класса
- name (str): Название товара
- price (float): Цена товара
- availability (bool): Наличие товара (True или False)

Класс `Technics` представляет собой модель техники с тремя атрибутами: `name`, `price` и `availability`. 
### Декоратор @total_ordering
### `@total_ordering`
Декоратор, который позволяет создавать методы сравнения в Python классах более простым и эффективным способом. Он позволяет автоматически создать для класса методы сравнения (eq, ne, lt, le, gt, ge) на основе определения лишь части из них.
## Методы класса

### `__slots__ = ('name', 'price', 'availability')`
Магический метод `__slots__` используется для определения списка атрибутов объекта, которые могут быть установлены.
Это может улучшить производительность и экономить память, поскольку он позволяет интерпретатору знать, какое количество памяти должно быть выделено для каждого экземпляра класса.

### `__init__(self, name, price, availability)`

Конструктор класса инициализирует атрибуты объекта.

### `category(self)`

Метод возвращает категорию техники в зависимости от цены: "Дорогой", если цена больше 1000, и "Бюджетный" в противном случае.

### `dir(self)`

Метод возвращает список доступных атрибутов объекта.

### `len(self)`

Метод возвращает длину имени объекта.

### `eq(self, other)`

Метод сравнивает длину имени текущего объекта с длиной имени переданного объекта `other`.

### `lt(self, other)`

Метод сравнивает длину имени текущего объекта с длиной имени переданного объекта `other`.
## 2. Сравнение строк "Название техники"
### Требования:
На основе предыдущего задания необходимо выполнить сравнение строк
"Название техники" по количеству символов:
1. Воспользоваться магическими методами;
2. Воспользоваться декоратором;
## Пример использования

```
laptop1 = Technics("Ноутбук", 20000, True)
laptop2 = Technics("Смартфон", 800, True)

print(laptop1.category)  # Дорогой
if laptop1.name_length > laptop2.name_length:
    print("Название техники", laptop1.name, "длиннее, чем название техники", laptop2.name)
else:
    print("Название техники", laptop2.name, "длиннее, чем название техники", laptop1.name)
```

В данном примере создаются два объекта класса `Technics` - `laptop1` и `laptop2`. Затем выводятся результаты работы методов класса на этих объектах.


# 3.1 Создать функцию для задачи Сервисный центр(tasks1.py)

## Задача:
 
 В базе данных СЦ хранится информация о списке клиентов. Данные о технике и их владельцах записаны в формате 
"Название техники", "Цена ремонта", "Имя владельца", "Телефон владельца":
```
devices_data = [('Ноутбук', 1500, 'Татьяна', '89002001020'), ('Смартфон', 500, 'Анна', '89202202325'),
                 ('Проектор', 300, 'Андрей', '89505205656'), ('Принтер', 750, 'Игорь', '89303303236'),
                 ('Планшет', 2300, 'Игорь', '89303303236'), ('Смартфон', 1000, 'Андрей', '89505205656'),
                 ('Ноутбук', 4800, 'Татьяна', '89002001020'), ('Наушники', 780, 'Марина', '89562002350'),
                 ('Сканер', 550, 'Сергей', '89808564559'), ('Планшет', 1200, 'Анна', '89202202325'),
                 ('Ноутбук', 1100, 'Игорь', '89303303236'), ('Смартфон', 3500, 'Татьяна', '89002001020')]
```

Имена некоторых клиентов повторяются, т.к. обращались в СЦ несколько раз. Необходимо оптимизировать хранение данных таким 
образом, чтобы для каждого клиента при выводе на печать, данные о всей технике отображались в одной строке:
```
Сергей 89808564559: Смартфон - 1000.0; Сканер - 550.0;
```
## Что использовалось?

* Python 3.10.4
* SQLAlchemy 2.0.7
* SQLite 3

## Как запустить?

1. Создайте виртуальную среду и установите необходимые зависимости:

   ```
   python -m venv venv
   pip install sqlalchemy
   ```

2. Клонируйте проект с GitHub `git clone ...`
3. Раскоментируйте код в файле `task3.py` для наполнения базы данных тестовыми данными
4. Запустите файл `main.py`:
   
   ```
   python main.py
   ```
5. Или используйте PyCharm(не реклама:)) для запуска проекта:
   

Когда программа запущена, она сначала создаст объект базы данных (SQLite) и таблиц, определенных в модели (`Client` и `Device`). Затем она добавит несколько клиентов в базу данных со случайно выбранными устройствами и расширенной информацией: имя клиента, его номер телефона и название его устройства.
  
После этого программа выполнит запрос к базе данных для извлечения информации о всех клиентах и списках устройств каждого клиента, выведет эти данные в консоли.

## Как это работает?
 
В данном примере мы используем библиотеку SQLAlchemy для создания объектной модели на основе таблиц, которые мы бы хотели иметь в базе данных. Мы начинаем путем создания экземпляра класса Engine, который является связующим звеном между логическим представлением модели (ORM) и физической реализацией базы данных (SQLite). 
 
Затем мы определяем два класса - `Client` и `Device`, каждый из которых имеет свою таблицу в базе данных. Между этими двумя классами есть отношение «один-ко-многим», поскольку один клиент может иметь много устройств.

Далее мы используем метод create_all () объекта Base для создания запрошенной структуры таблицы в самой базе данных.

Наконец, мы выполняем запрос к БД для получения списка всех клиентов и выводим эту информацию на экран.

# 3.2 Создать функцию для задачи Имя файла (tasks2.py)

## Задача:
Фирма для названия файлов всегда использует одинаковую длину. Длина определяется исходя из самого длинного
названия, передаваемого в списке. Важно, в название файла не должны дублироваться символы. Если строка короче
самой длинной, необходимо дополнить нижним подчеркиванием до необходимого размера.

### Решение:
Решение данной задачи представлено в файле `tasks2.py` с помощью функции `generate_file_names`

# 3.3 Итоговая задача(`tasks3.py`)
В файле `tasks3.py` реализован вызов функций с задачами 3.1 и 3.2 

# 4. Задача БД 
## Объединить таблицы "Города" и "Заказчики":
1. Объединение таблиц "Заказчики" и "Города":
```
SELECT *
FROM Заказчики
JOIN Города
ON Заказчики.код_города = Города.код;
```
2. Объединение таблиц "Заказчики" и "Города" по таблице "Заказчики".
LEFT JOIN вернет все строки из левой таблицы (в данном случае - Заказчики), включая те, которые не имеют соответствующих значений в правой таблице (в данном случае - Города).

```
SELECT Заказчики.*, Города.название
FROM Заказчики
LEFT JOIN Города
ON Заказчики.код_города = Города.код;
```
3. Объединение таблиц "Заказчики" и "Города" по таблице "Города". 
RIGHT JOIN вернет все строки из правой таблицы (в данном случае - Города), включая те, которые не имеют соответствующих значений в левой таблице (в данном случае - Заказчики).
```
SELECT Заказчики.*, Города.название
FROM Заказчики
RIGHT JOIN Города
ON Заказчики.код_города = Города.код;
```
Примечание: в обоих запросах используется оператор JOIN для объединения таблиц по полю, в котором содержится код города. Также используется оператор `*`, чтобы выбрать все столбцы из обеих таблиц. При необходимости можно указать нужные столбцы для выборки.