# Market Analysis of Public Catering Establishments in Moscow

**EN** · [RU](#анализ-рынка-общественного-питания-москвы)

Market research for an investment fund planning to open a catering business in Moscow, with a focus on a coffee shop. The dataset has 8,406 establishments from Yandex Maps and Yandex Business (summer 2022) and 14 fields: category, address, district, coordinates, opening hours, rating, price category, average bill, cappuccino price, seats and chain status.

**What was done**
- Data cleaning: found implicit duplicates with a normalised `name + address` key (lower case, no spaces), which caught records like `More poke` / `More Poke`. Missing values in price, average bill and seats were left as they are on purpose, because filling them by category or district averages would distort the price and size analysis.
- Features from free text: the street was taken from the address, and a 24/7 flag was parsed from the opening hours text.
- Market analysis by category, size, chain status, district, street, rating and price. Medians were used instead of means where outliers are large (seats go up to 1,288).
- Geo-analytics with folium: choropleth maps of the average rating and the average bill by administrative district (GeoJSON boundaries), a marker-cluster map of all establishments, and a density heatmap.
- Coffee shop deep dive: count by district, 24/7 coverage, ratings, the median cappuccino price by district, and the link between price and rating.
- Recommendations and a presentation for the investor.

**Result:** coffee shops are the third largest category (1,413 venues, 16.8% of the market). Ratings and prices are highest in the centre and the west, and lowest in the south-east. Recommended location for a new coffee shop: the **North-Western District**. It has the fewest coffee shops (62), the median cappuccino price is slightly above average (165 RUB), and ratings are high, so the service bar is high too. Price and rating are only weakly correlated (r = 0.15).

**Stack:** Python, pandas, NumPy, matplotlib, seaborn, folium (Choropleth, MarkerCluster, HeatMap), requests, GeoJSON.

Presentation: [Yandex Disk](https://disk.yandex.ru/i/f00gMRuBv3bssg)

---

## Анализ рынка общественного питания Москвы

[EN](#market-analysis-of-public-catering-establishments-in-moscow) · **RU**

Исследование рынка для инвестиционного фонда, который планирует открыть заведение общепита в Москве, с фокусом на кофейню. В наборе данных 8 406 заведений из Яндекс Карт и Яндекс Бизнеса (лето 2022 года) и 14 полей: категория, адрес, округ, координаты, часы работы, рейтинг, ценовая категория, средний чек, цена капучино, количество мест и признак сетевого заведения.

**Что сделано**
- Очистка данных: неявные дубликаты найдены по нормализованному ключу `название + адрес` (нижний регистр, без пробелов), так нашлись записи вроде `More poke` / `More Poke`. Пропуски в ценовой категории, среднем чеке и количестве мест намеренно не заполнялись: заполнение средними по категории или округу исказило бы анализ цен и размеров заведений.
- Признаки из текстовых полей: из адреса выделена улица, из текста часов работы получен признак круглосуточной работы.
- Анализ рынка по категориям, размеру, сетевому признаку, округам, улицам, рейтингам и ценам. Там, где сильные выбросы (мест бывает до 1 288), вместо среднего использовалась медиана.
- Геоаналитика на folium: фоновые картограммы (choropleth) среднего рейтинга и среднего чека по административным округам (границы из GeoJSON), карта всех заведений с кластеризацией маркеров и тепловая карта плотности.
- Детальный анализ кофеен: количество по округам, круглосуточные заведения, рейтинги, медианная цена капучино по округам, связь цены и рейтинга.
- Рекомендации и презентация для инвестора.

**Результат:** кофейни - третья по размеру категория (1 413 заведений, 16,8% рынка). Рейтинги и цены выше в центре и на западе, ниже всего на юго-востоке. Рекомендуемое место для новой кофейни - **Северо-Западный округ**: там меньше всего кофеен (62), медианная цена капучино чуть выше средней (165 ₽), а рейтинги высокие, значит, и планка качества сервиса высокая. Цена и рейтинг связаны слабо (r = 0,15).

**Стек:** Python, pandas, NumPy, matplotlib, seaborn, folium (Choropleth, MarkerCluster, HeatMap), requests, GeoJSON.

Презентация: [Яндекс Диск](https://disk.yandex.ru/i/f00gMRuBv3bssg)

<a href="Market Analysis of Public Catering in Moscow_ENG.ipynb" style="text-decoration:none;">
  <div style="display:inline-block; padding:10px 20px; font-size:18px; font-weight:bold; color:white; background-color:#007bff; border-radius:5px;">
    Go to the project / Перейти к проекту
  </div>
</a>
