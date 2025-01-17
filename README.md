# Fibonacci heap

[![CMake](https://github.com/Algorithms-and-Data-Structures-2021/semester-work-fibonacci-heap/actions/workflows/cmake.yml/badge.svg)](https://github.com/Algorithms-and-Data-Structures-2021/semester-work-fibonacci-heap/actions/workflows/cmake.yml)

_Краткое описание семестрового проекта:_


- _Фибоначчиева куча (англ. Fibonacci heap) — структура данных, отвечающая интерфейсу priority queue.
  Имеет меньшую амортизированную сложность, чем такие приоритетные очереди как биномиальная куча и двоичная куча._


- _Фибоначчиева куча представляет собой набор фибоначчиевых деревьев_

    (прим. Фибоначчиево дерево – это k-ичное дерево, для каждого элемента которого выполняется правило: 
    «дочерний элемент не превышает своего родителя». Корни фибоначчиевых деревьев хранятся в виде кольцевого списка.
  Каждый узел фибоначчиева дерева, помимо указателей на левого, правого брата, на родителя и на одного из своих 
  сыновей содержит информацию о количестве дочерних узлов.)
  
**Пример:** 

![img.png](img.png)



- _Фибоначчиевыкучи нашли широкое применение в алгоритмах на графах(поиск минимального остовногодерева, поиск кратчайшего пути в графе)_
  
- _Основные операции:_
  
    - Поиск минимального элемента (_getMinimum_)
    - Добавление нового элемента (_insert_)
    - Объединение двух фибоначчиевых куч (_merge_)
    - Удаление минимального элемента (_removeMinimum_)
    - Изменение элемента (_decreaseKey_)
  
## _Теоритическая сложность операций_
  | Операция    | 	Амортизированная сложность|
  | :---                 |   ---:    |  
  | insert       | O(1)    | 
  | getMinimum  | O(1)       |
  | merge        | O(1)    | 
  | removeMunimum  | O(log n)       |
  | decreaseKey  | O(1)       |


## Команда "Fibonacci team"

| Фамилия Имя          | Вклад (%) | Прозвище              |
| :---                 |   ---:    |  ---:                 |
| Ибаев Даниль         | 50        |  _    _               |
| Анастасия Войтенко   | 50        |  _                  _ |

**Девиз команды**
> _Наши цели ясны. Задачи определены. За работу, товарищи!_

## Структура проекта

_Описание основных частей семестрового проекта._

_Проект состоит из следующих частей:_

- [`src`](src)/[`include`](include) - реализация структуры данных (исходный код и заголовочные файлы);
- [`benchmark`](benchmark) - контрольные тесты производительности структуры данных (операции добавления, удаления,
  поиска и пр.);
- [`examples`](examples) - примеры работы со структурой данных;
- [`dataset`](dataset) - наборы данных для запуска контрольных тестов и их генерация;

## Требования (Prerequisites)

_В этом разделе задаются основые требования к программному и аппаратному обеспечению для успешной работы с проектом._

_Рекомендуемые требования:_

1. С++ компилятор c поддержкой стандарта C++17 (например, _GNU GCC 8.1.x_ и выше).
2. Система автоматизации сборки _CMake_ (версия _3.12.x_ и выше).
3. Интерпретатор _Python_ (версия _3.7.x_ и выше).
4. Рекомендуемый объем оперативной памяти - не менее 4 ГБ.
5. Свободное дисковое пространство объемом ~ 3 ГБ (набор данных для контрольных тестов).

## Сборка и запуск

_Инструкция по сборке проекта, генерации тестовых данных, запуска контрольных тестов и примеров работы._

_Постарайтесь написать инструкцию так, чтобы незнакомый с проектом человек смог самостоятельно всё запустить._

### Пример (Windows)

#### Сборка проекта

_Опишите процесс сборки проекта._

Склонируйте проект к себе на устройство через [Git for Windows](https://gitforwindows.org/) (либо используйте
возможности IDE):

```shell
git clone https://github.com/Algorithms-and-Data-Structures-2021/semester-work-template.git
```

Для ручной сборки проекта в терминале введите:

```shell
# переход в папку с проектом
cd C:\Users\username\asd-projects\semester-work-template

# создание папки для файлов сборки (чтобы не засорять папку с проектом) 
mkdir -p build && cd build 

# сборка проекта
cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo && cmake --config RelWithDebInfo --build . 
```

#### Генерация тестовых данных

_Опишите формат хранения (JSON, XML, CSV, YAML и т.д.) и процесс генерации тестовых данных._

_Разрешается использовать собственный формат хранения данных._

Генерация тестового набора данных в
формате [comma-seperated values (CSV)](https://en.wikipedia.org/wiki/Comma-separated_values):

```shell
# переход в папку генерации набора данных
cd dataset

# запуск Python-скрипта
python generate_csv_bench_dataset.py --samples 1000 <output> [args ...]
```

- `--samples` - количество генерируемых элементов;
- `<output>` - выходной файл и т.д.

Тестовые данные представлены в CSV формате (см.
[`dataset/data/dataset-example.csv`](dataset/data/dataset-example.csv)):

```csv
id, full_name
0, "Ramil Safin"
1, "Bulat Abbyasov"
...
```

**Примечание**. Для удобства запуска контрольных тестов рекомендуется организовывать данные в директориях, например:

```shell
dataset/data/
  add/
    01/
      100.csv
      ...
      5000000.csv
    02/ ...
    03/ ...
    ...
    10/ ...
  search/
    01/
      100.csv
      ...
      5000000.csv
    ...
    10/ ...
  ...
```

По названию директории `/dataset/data/add` можно понять, что здесь хранятся наборы данных для контрольных тестов по
**добавлению** элементов в структуру данных. Названия файлов `100.csv`. `5000000.csv` и т.д. хранят информацию о размере набора данных (т.е. количество элементов). 

#### Контрольные тесты (benchmarks)

_Опишите, как запустить контрольные тесты, что они из себя представляют, какие метрики замеряют (время работы,
потребление памяти и пр.)._

Для запуска контрольных тестов необходимо предварительно сгенерировать или скачать готовый набор тестовых данных.

**Примечание**. Во избежание "захламления" репозитория большим объёмом данных рекомендуется указать ссылку на архив с
набором данных, который при необходимости можно скачать по ссылке. Наборы данных должны находиться в папке семестровой
работы на [Google Drive](https://drive.google.com/drive/folders/17-qridbMXFnz3E-6UjOj0WD1H0jWtpz3?usp=sharing).

##### Список контрольных тестов

| Название                  | Описание                                | Метрики         |
| :---                      | ---                                     | :---            |
| `random_search_benchmark` | поиск элементов по случайному индексу   | _время_         |
| `add_benchmark`           | добавление элементов в структуру данных | _время, память_ |
| ...                       | ...                                     | ...             |

##### Примеры запуска

```shell
./benchmark <input> <output> --trials 50
```

- `<input>` - входной файл с набором данных в формате CSV;
- `<output>` - выходной файл с результатами контрольного теста;
- `--trials` - количество прогонов на наборе данных и т.д.

Добавление 10000 случайных элементов в структуру данных (повторить операцию 50 раз и вычислить среднее время работы и
потребляемую память):

```
./add_benchmark.exe ../dataset/data/add/10000.csv metrics.txt --trials 50
``` 

где `<input> = ../dataset/data/add/10000.csv` и `<output> = metrics.txt`.

**Примечание**. Файл с метриками не обязателен, можете выводить данные в стандартный поток вывода (т.е. консоль).

## Источники

  _Список использованных при реализации структуры данных источников:_

- _Статья "Приоритетная очередь на основе бинарной, биномиальной и фибонначиевой куч" :_ https://www.rsdn.org/article/submit/heap/heaps.xml#ERFAE
-  _Статья "Фибоначчиева куча" Университет ИТМО_
- https://ru.wikipedia.org "Фибоначчиева куча"
- Лучшая лекция от ИТМО: https://www.youtube.com/watch?v=IXcdJuRbqPU&t=3530s


_**Это не плагиат, это уважение чужого труда и помощь своим сокурсникам более подробно разобраться в теме.**_
