# Business Decision-Making: Hypothesis Prioritization and Testing

**EN** · [RU](#принятие-решений-в-бизнесе-приоритизация-и-проверка-гипотез)

Research for a large online store. The marketing team prepared a list of ideas for growing revenue. The task has two parts: decide which ideas to test first, then read the results of an A/B test and decide whether to stop it. The data has three tables: 9 hypotheses scored on a 10-point scale (Reach, Impact, Confidence, Efforts), 1,197 orders from the A/B test (order ID, user ID, date, revenue, group) and the daily number of visitors in groups A and B for August 2019.

**What was done**
- Data check and preparation: no missing values or duplicates, column names brought to one style, dates converted to datetime.
- Hypothesis prioritization with two frameworks, ICE and RICE, and a comparison of how the ranking changes when reach is taken into account.
- Exploratory analysis of the A/B test: cumulative revenue, average order value and orders per visitor by group, and the relative difference between group B and group A.
- Search for anomalies: scatter plots and the 95th and 99th percentiles of orders per user and order value. Users with 4 or more orders or with an order of 58,233.2 or more were treated as anomalies.
- Statistical tests (Mann-Whitney, significance level 0.05) on the number of orders per visitor and the average order value, on raw data and on data cleaned of anomalies.
- A decision on the test and conclusions for the business.

**Result:**
- **Prioritization:** by ICE the leader is a birthday discount (16.2), followed by two new traffic channels (13.3) and a subscription form for an email list (11.2). By RICE the subscription form is far ahead (112), followed by product recommendation blocks (56), new traffic channels and promo banners on the home page (40 each). The birthday discount drops to 5th place because it reaches very few users. The most promising ideas by both frameworks are the subscription form and new traffic channels.
- **A/B test:** group B has more orders per visitor than group A, and the difference is statistically significant: +13.8% on raw data (p = 0.017) and +15.1% on cleaned data (p = 0.014). The average order value does not differ significantly. On raw data group B looks 25.9% higher (p = 0.729), but this comes from a few huge orders, one of them over 1.2 million. After cleaning the difference is -1.4% (p = 0.959). By the end of the test the gain in orders per visitor became stable at about 10–15%.

**Recommendations:** stop the test and declare group B the winner. The change tested on group B brings more orders without lowering the average order value, so it can be rolled out to all users.

**Next steps**
- Check that the test was set up correctly: whether some users ended up in both groups and whether the visitors were split evenly between A and B.
- Compare revenue per visitor between the groups, so the decision rests on one metric that combines both conversion and order value.
- Add confidence intervals for the difference between the groups, so the size of the effect is clear, not only the fact that it exists.

**Stack:** Python, pandas, NumPy, matplotlib, SciPy (stats), datetime. ICE and RICE frameworks, A/B testing, Mann-Whitney test.

---

## Принятие решений в бизнесе: приоритизация и проверка гипотез

[EN](#business-decision-making-hypothesis-prioritization-and-testing) · **RU**

Исследование для крупного интернет-магазина. Отдел маркетинга подготовил список идей, которые должны увеличить выручку. Задача состоит из двух частей: решить, какие идеи проверять в первую очередь, а затем проанализировать результаты A/B-теста и решить, можно ли его остановить. Данные - три таблицы: 9 гипотез с оценками по 10-балльной шкале (Reach, Impact, Confidence, Efforts), 1 197 заказов из A/B-теста (ID заказа, ID пользователя, дата, выручка, группа) и ежедневное число посетителей в группах A и B за август 2019 года.

**Что сделано**
- Проверка и подготовка данных: пропусков и дубликатов нет, названия столбцов приведены к одному стилю, даты переведены в datetime.
- Приоритизация гипотез двумя фреймворками, ICE и RICE, и сравнение того, как меняется порядок, если учитывать охват.
- Исследовательский анализ A/B-теста: кумулятивные выручка, средний чек и число заказов на посетителя по группам, а также относительная разница группы B и группы A.
- Поиск аномалий: точечные графики и 95-й и 99-й перцентили числа заказов на пользователя и стоимости заказов. Аномальными считались пользователи с 4 и более заказами или с заказом от 58 233,2.
- Статистические тесты (Манна-Уитни, уровень значимости 0,05) по числу заказов на посетителя и среднему чеку - на «сырых» данных и на данных, очищенных от аномалий.
- Решение по тесту и выводы для бизнеса.

**Результат:**
- **Приоритизация:** по ICE лидирует скидка в день рождения (16,2), за ней идут два новых канала привлечения трафика (13,3) и форма подписки для email-рассылок (11,2). По RICE с большим отрывом первая форма подписки (112), дальше блоки рекомендаций товаров (56), новые каналы трафика и баннеры с акциями на главной странице (по 40). Скидка в день рождения опускается на 5-е место, потому что затрагивает очень мало пользователей. Самые перспективные идеи по обоим фреймворкам - форма подписки и новые каналы трафика.
- **A/B-тест:** в группе B больше заказов на посетителя, чем в группе A, и разница статистически значима: +13,8% на «сырых» данных (p = 0,017) и +15,1% на очищенных (p = 0,014). Средний чек значимо не отличается. На «сырых» данных в группе B он выше на 25,9% (p = 0,729), но это результат нескольких очень крупных заказов, один из них больше 1,2 млн. После очистки разница составляет -1,4% (p = 0,959). К концу теста прирост числа заказов на посетителя стабилизировался на уровне примерно 10–15%.

**Рекомендации:** остановить тест и признать победу группы B. Изменение, которое проверяли на группе B, даёт больше заказов и не снижает средний чек, поэтому его можно распространить на всех пользователей.

**Следующие шаги**
- Проверить, что тест настроен корректно: не попали ли одни и те же пользователи в обе группы и поровну ли разделились посетители между A и B.
- Сравнить группы по выручке на посетителя, чтобы решение опиралось на одну метрику, которая учитывает и конверсию, и средний чек.
- Добавить доверительные интервалы для разницы между группами, чтобы был виден размер эффекта, а не только сам факт различия.

**Стек:** Python, pandas, NumPy, matplotlib, SciPy (stats), datetime. Фреймворки ICE и RICE, A/B-тестирование, тест Манна-Уитни.

<a href="Business Decision-Making_RUS.ipynb" style="text-decoration:none;">
  <div style="display:inline-block; padding:10px 20px; font-size:18px; font-weight:bold; color:white; background-color:#007bff; border-radius:5px;">
    Go to the project / Перейти к проекту
  </div>
</a>
