# Real Estate Market Dependencies Analysis

**EN** · [RU](#анализ-зависимостей-на-рынке-недвижимости)

Research of the housing market in St. Petersburg and its suburbs: prepare the listings data and find which parameters drive the price of an apartment. The data is an archive of 23,699 apartment sale listings in St. Petersburg and nearby towns, published from 2014 to 2019. Each listing has 22 fields: some are entered by the seller (price, total, living and kitchen area, rooms, floor, ceiling height, balconies), and some are added automatically from map data (distance to the city center, the airport, the nearest park and pond, number of parks and ponds within 3 km). There is also the publication date and how many days the listing was online.

**What was done**
- Data check: missing values in 14 of 22 columns. Each column got its own treatment with a reason: zeros where an empty field most likely means "none" (balconies, apartment status, parks and ponds within 3 km), medians by number of rooms for living and kitchen area, medians by type of locality for the distance to the center, and empty values were kept where filling would distort the data (distance to parks, ponds and the airport). The 49 rows without a locality were removed.
- Anomalies: ceiling heights below 2 m and above 4.5 m (up to 100 m in the raw data) were replaced with the median of 2.65 m, "0 rooms" was treated as a studio with one room, and a price of 12,190 rubles for a 109 sq.m. apartment was corrected as a value entered in thousands.
- Implicit duplicates in locality names (е/ё, "поселок" vs "городской поселок" and so on) were removed: 364 unique names became 305.
- New fields: price per square meter, day of the week, month and year of publication, floor type (first, last, other) and distance to the center in km.
- Distributions of area, price, rooms, floor, distance to the center and publication date, plus a look at how long apartments stay on sale.
- Price dependence on area (correlations), number of rooms, floor, publication date, locality and distance to the center of St. Petersburg.

**Result:** a typical listing is a 1–3 room apartment of 30–75 sq.m. for 2.5–5 million rubles, about 10–15 km from the center. Half of the apartments are sold within 95 days, sales within 45 days can be called fast and over 198 days long.
- **Area** matters most: the correlation of total area with price is 0.65. Living area (0.56) and kitchen area (0.45) are weaker, most likely because they simply grow with the total area.
- **Rooms:** the median price grows from 3.6 million for one room to 6.2 million for three and 14 million for five.
- **Floor:** apartments on the first floor are the cheapest (median 3.9 million), the last floor is also cheaper (4.3 million) than the others (4.85 million).
- **Location:** among the 10 localities with the most listings, a square meter costs the most in St. Petersburg (about 114,800 rubles) and Pushkin (103,100), and the least in Vyborg (58,100).
- **Publication date** matters little: by day of the week the median price differs by less than 4%, by month by about 8% (the lowest in May and June). By year, the median price fell from about 7.6 million in 2014 to 4.5 million in 2016, stayed flat until 2018 and grew to about 5 million in 2019.
- **Distance to the center:** the notebook originally divided the price by the distance, and such a value falls with distance by construction. The calculation was replaced with the median price for each kilometer, the result will be updated after the notebook is re-run.

**Recommendations:** many fields are left empty by sellers, so some of them could be made mandatory or offered as a drop-down list. A locality field with autocomplete would remove the different spellings of the same place.

**Next steps**
- Re-run the distance analysis and compare the price per square meter, not the full price, by distance, so that large apartments in the center do not distort the picture.
- Remove the effect of filling missing values: 13% of listings got the median of 95 days on sale, and this creates a false peak on the histogram. The sale time is better analysed only on the real values.
- Check the dependencies together, not one by one: for example, a regression of price per square meter on area, floor, distance and locality would show which factors matter on their own.

**Stack:** Python, pandas, matplotlib. Data preprocessing, exploratory data analysis, correlation analysis.

---

## Анализ зависимостей на рынке недвижимости

[EN](#real-estate-market-dependencies-analysis) · **RU**

Исследование рынка жилья Санкт-Петербурга и пригородов: подготовить данные объявлений и понять, от каких параметров зависит цена квартиры. Данные - архив из 23 699 объявлений о продаже квартир в Санкт-Петербурге и ближайших населённых пунктах, опубликованных с 2014 по 2019 год. У каждого объявления 22 поля: часть вводит продавец (цена, общая, жилая площадь и площадь кухни, комнаты, этаж, высота потолков, балконы), часть добавляется автоматически по картографическим данным (расстояние до центра, аэропорта, ближайшего парка и водоёма, число парков и водоёмов в радиусе 3 км). Есть также дата публикации и число дней, которое объявление провисело на сайте.

**Что сделано**
- Проверка данных: пропуски в 14 из 22 столбцов. Для каждого столбца выбран свой способ с объяснением: нули там, где пустое поле скорее всего означает «нет» (балконы, статус апартаментов, парки и водоёмы в радиусе 3 км), медианы по числу комнат для жилой площади и площади кухни, медианы по типу населённого пункта для расстояния до центра, а там, где заполнение исказило бы данные (расстояние до парков, водоёмов и аэропорта), пропуски оставлены. 49 строк без названия населённого пункта удалены.
- Аномалии: высота потолков ниже 2 м и выше 4,5 м (в исходных данных встречалось до 100 м) заменена медианой 2,65 м, «0 комнат» принято за студию с одной комнатой, а цена 12 190 рублей за квартиру 109 кв. м исправлена как введённая в тысячах.
- Устранены неявные дубликаты в названиях населённых пунктов (е/ё, «поселок» и «городской поселок» и т. д.): из 364 уникальных названий осталось 305.
- Новые поля: цена квадратного метра, день недели, месяц и год публикации, тип этажа (первый, последний, другой) и расстояние до центра в км.
- Распределения площади, цены, числа комнат, этажа, расстояния до центра и даты публикации, а также анализ того, сколько квартиры находятся в продаже.
- Зависимость цены от площади (корреляции), числа комнат, этажа, даты публикации, населённого пункта и расстояния до центра Петербурга.

**Результат:** типичное объявление - 1–3-комнатная квартира площадью 30–75 кв. м за 2,5–5 млн рублей примерно в 10–15 км от центра. Половина квартир продаётся за 95 дней, продажу быстрее 45 дней можно считать быстрой, дольше 198 дней - долгой.
- **Площадь** влияет сильнее всего: корреляция общей площади с ценой - 0,65. У жилой площади (0,56) и площади кухни (0,45) связь слабее, скорее всего потому, что они просто растут вместе с общей площадью.
- **Комнаты:** медианная цена растёт с 3,6 млн за однокомнатную до 6,2 млн за трёхкомнатную и 14 млн за пятикомнатную.
- **Этаж:** дешевле всего квартиры на первом этаже (медиана 3,9 млн), на последнем тоже дешевле (4,3 млн), чем на остальных (4,85 млн).
- **Место:** среди 10 населённых пунктов с наибольшим числом объявлений квадратный метр дороже всего в Санкт-Петербурге (около 114 800 рублей) и Пушкине (103 100), дешевле всего - в Выборге (58 100).
- **Дата публикации** почти не важна: по дням недели медианная цена различается меньше чем на 4%, по месяцам - примерно на 8% (ниже всего в мае и июне). По годам медианная цена упала примерно с 7,6 млн в 2014 году до 4,5 млн в 2016-м, до 2018 года почти не менялась и выросла примерно до 5 млн в 2019-м.
- **Расстояние до центра:** в ноутбуке цена изначально делилась на расстояние, а такая величина падает с расстоянием сама по себе. Расчёт заменён на медианную цену для каждого километра, результат будет обновлён после перезапуска ноутбука.

**Рекомендации:** многие поля продавцы оставляют пустыми, поэтому часть из них можно сделать обязательными или предлагать выбор из выпадающего списка. Поле населённого пункта с автодополнением уберёт разные написания одного и того же места.

**Следующие шаги**
- Перезапустить анализ расстояния и сравнивать по расстоянию цену квадратного метра, а не полную цену, чтобы большие квартиры в центре не искажали картину.
- Убрать влияние заполнения пропусков: 13% объявлений получили медиану 95 дней продажи, из-за этого на гистограмме появился ложный пик. Срок продажи лучше анализировать только по реальным значениям.
- Проверить зависимости вместе, а не по одной: например, регрессия цены квадратного метра на площадь, этаж, расстояние и населённый пункт покажет, какие факторы важны сами по себе.

**Стек:** Python, pandas, matplotlib. Предобработка данных, исследовательский анализ, корреляционный анализ.

<a href="real_estate_market_dependencies.ipynb" style="text-decoration:none;">
  <div style="display:inline-block; padding:10px 20px; font-size:18px; font-weight:bold; color:white; background-color:#007bff; border-radius:5px;">
    Go to the project / Перейти к проекту
  </div>
</a>
