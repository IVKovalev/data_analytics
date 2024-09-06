# Research on Real Estate Listings
## Data and Their Source

The dataset is provided in a CSV file. It contains an archive of real estate Marketplace listings spanning several years, featuring apartment sales in St. Petersburg and surrounding areas.

For each apartment on sale, two types of data are available. The first set of data is provided by the user, and the second set is automatically obtained based on map data.

## Data Description
- airports_nearest — distance to the nearest airport in meters (m)
- balcony — number of balconies
- ceiling_height — ceiling height in meters (m)
- cityCenters_nearest — distance to the city center in meters (m)
- days_exposition — number of days the listing was posted (from publication to removal)
- first_day_exposition — publication date
- floor — floor number
- floors_total — total number of floors in the building
- is_apartment — apartment status (boolean type)
- kitchen_area — kitchen area in square meters (m²)
- last_price — price at the time of delisting
- living_area — living area in square meters (m²)
- locality_name — name of the locality
- open_plan — open floor plan (boolean type)
- parks_around3000 — number of parks within a 3 km radius
- parks_nearest — distance to the nearest park in meters (m)
- ponds_around3000 — number of ponds within a 3 km radius
- ponds_nearest — distance to the nearest pond in meters (m)
- rooms — number of rooms
- studio — studio apartment (boolean type)
- total_area — total area of the apartment in square meters (m²)
- total_images — number of images of the apartment in the listing

### The following Python libraries are used in the project:
```python
import matplotlib.pyplot as plt
import pandas as pd
``` 

<img src="https://github.com/IVKovalev/data_analytics/blob/main/exploratory_data_analysis/screenshot.PNG" alt="Скриншот" width="400"/>

### Это заголовок третьего уровня
#### Это заголовок четвёртого уровня

**этот текст имеет полужирное начертание**
*А этот текст имеет курсивное начертание*
***И ничто нам не мешает сделать и курсивное, и полужирное начертание***

- Это первый элемент маркированного списка
- Это второй элемент маркированного списка
    - вложенный элемент маркированного списка

> Именно так оформляются цитаты 

1. Нумерованный список начинается так
2. Можно продолжить так
    1. Вложенные элементы описываются так
    2. И так

| Markdown              | Поддерживает           | Таблицы                     |
| :-------------------- | ---------------------: |:---------------------------:|
| с выравниванием слева | с выравниванием справа | и с выравниванием по центру |

[Текст ссылки](адрес://ссылки.здесь "Заголовок ссылки")
[Подробнее о Markdown по ссылке](https://daringfireball.net/projects/markdown/)

```python
print("Это фрагмент кода на python")
``` 
