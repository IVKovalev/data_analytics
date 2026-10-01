# Market Analysis of Video Games

**EN** · [RU](#анализ-рынка-видеоигр)

Research for an online video game store: find what makes a game sell, so the store can pick promising products and plan its advertising for 2017, and describe the typical player in each region. The dataset has 16,715 games from open sources (sales up to 2016) and 11 fields: name, platform, year of release, genre, sales in North America, Europe, Japan and other regions (millions of copies), critic score, user score and ESRB age rating.

**What was done**
- Data cleaning: column names were brought to one style, `tbd` in the user score was treated as a missing value, and the missing release year was filled with the year of the same game on other platforms. A wrong year was corrected (a DS game dated 1985). Missing ESRB ratings got a separate "no data" category.
- Total sales across all regions were added for each game.
- Platform life cycle: games came out for a typical platform over 9 years (median), and a new generation appears several years before the old one fades. Based on this, the analysis used the current period of 2014–2016.
- Market analysis by platform, genre and sales per game, with box plots of sales for each platform.
- The effect of reviews on sales: scatter plots and Pearson correlation of critic and user scores with sales for the top platforms.
- Regional player profiles for North America, Europe and Japan: top 5 platforms, top 5 genres and sales by ESRB rating.
- Hypothesis testing with Welch's t-test (`equal_var=False`): user scores of Xbox One vs PC, and of Action vs Sports.

**Result:** the most promising platforms are **PS4** and **Xbox One**. In 2014–2016 they have the highest sales (about 288 and 140 million copies), and both are only 4 years into their life cycle. Action and Shooter lead in total sales, but Shooter games sell best per game (about 1.3 million copies, against 0.3 million for Action). Critic scores are moderately linked to sales (r = 0.40–0.53 for PS4, PS3 and X360), and user scores are not linked at all (r from −0.17 to −0.04). The regions are different:
- **North America:** PS4 and Xbox One, Shooter and Action, M-rated (17+) games sell best.
- **Europe:** PS4 has more than half of the top 5 platform sales; Action and Shooter; M-rated games lead.
- **Japan:** the handheld 3DS (almost half of the top 5 sales), Role-Playing and Action; most games sold have no ESRB rating, as Japan uses its own system.

The user scores of Action and Sports games do not differ significantly (p = 0.11). The Xbox One vs PC test gave p = 0.0005, but the missing user scores were filled with 0 before the test, so this result needs to be checked again.

**Next steps**
- Run the hypothesis tests again on games with real scores only, without the zeros that replaced missing values, and for the current period of 2014–2016.
- Check whether the 2016 data is complete before reading the drop in sales that year as a trend.
- Compare platforms and genres by median sales per game, not only by totals, so a few hits do not decide the ranking.

**Stack:** Python, pandas, NumPy, matplotlib, seaborn, SciPy (stats), missingno.

---

## Анализ рынка видеоигр

[EN](#market-analysis-of-video-games) · **RU**

Исследование для интернет-магазина видеоигр: найти, от чего зависит успех игры, чтобы выбрать перспективные продукты и спланировать рекламу на 2017 год, и описать типичного игрока каждого региона. В наборе данных 16 715 игр из открытых источников (продажи до 2016 года) и 11 полей: название, платформа, год выпуска, жанр, продажи в Северной Америке, Европе, Японии и других регионах (млн копий), оценка критиков, оценка пользователей и возрастной рейтинг ESRB.

**Что сделано**
- Очистка данных: названия столбцов приведены к одному стилю, значение `tbd` в оценке пользователей обработано как пропуск, пропущенный год выпуска заполнен годом выхода той же игры на других платформах. Исправлен неверный год (игра для DS с датой 1985). Для пропусков в рейтинге ESRB выделена отдельная категория «нет данных».
- Для каждой игры добавлены суммарные продажи по всем регионам.
- Жизненный цикл платформ: игры для типичной платформы выходят 9 лет (медиана), а новое поколение появляется за несколько лет до угасания старого. Исходя из этого, для анализа выбран актуальный период 2014–2016 годов.
- Анализ рынка по платформам, жанрам и продажам на одну игру, диаграммы размаха продаж для каждой платформы.
- Влияние отзывов на продажи: диаграммы рассеяния и корреляция Пирсона оценок критиков и пользователей с продажами для топовых платформ.
- Портреты игроков Северной Америки, Европы и Японии: топ-5 платформ, топ-5 жанров и продажи по рейтингу ESRB.
- Проверка гипотез t-тестом Уэлча (`equal_var=False`): оценки пользователей Xbox One и PC, а также жанров Action и Sports.

**Результат:** самые перспективные платформы - **PS4** и **Xbox One**. В 2014–2016 годах у них самые высокие продажи (около 288 и 140 млн копий), и обе прошли только 4 года своего жизненного цикла. Action и Shooter лидируют по суммарным продажам, но лучше всего на одну игру продаются шутеры (около 1,3 млн копий против 0,3 млн у Action). Оценки критиков умеренно связаны с продажами (r = 0,40–0,53 для PS4, PS3 и X360), а оценки пользователей не связаны совсем (r от −0,17 до −0,04). Регионы различаются:
- **Северная Америка:** PS4 и Xbox One, Shooter и Action, лучше всего продаются игры с рейтингом M (17+).
- **Европа:** у PS4 больше половины продаж топ-5 платформ; Action и Shooter; лидируют игры с рейтингом M.
- **Япония:** портативная 3DS (почти половина продаж топ-5), Role-Playing и Action; у большинства проданных игр нет рейтинга ESRB, так как в Японии используется своя система.

Оценки пользователей жанров Action и Sports значимо не различаются (p = 0,11). Тест Xbox One и PC дал p = 0,0005, но пропуски в оценках пользователей перед тестом были заполнены нулями, поэтому этот результат нужно перепроверить.

**Следующие шаги**
- Повторить проверку гипотез только на играх с реальными оценками, без нулей вместо пропусков, и за актуальный период 2014–2016 годов.
- Проверить полноту данных за 2016 год, прежде чем считать падение продаж в этом году трендом.
- Сравнивать платформы и жанры по медианным продажам на одну игру, а не только по суммам, чтобы рейтинг не определяли несколько хитов.

**Стек:** Python, pandas, NumPy, matplotlib, seaborn, SciPy (stats), missingno.

<a href="Analysis of the computer games market ENG.ipynb" style="text-decoration:none;">
  <div style="display:inline-block; padding:10px 20px; font-size:18px; font-weight:bold; color:white; background-color:#007bff; border-radius:5px;">
    Go to the project / Перейти к проекту
  </div>
</a>
