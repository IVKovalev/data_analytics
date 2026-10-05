# Business Performance Analysis

**EN** · [RU](#анализ-бизнес-показателей)

Research for an entertainment app that has been losing money for several months despite large investments in advertising. The task is to find out why the ads do not pay off and what the marketing team should change. The data covers about 150,000 users acquired from 1 May to 27 October 2019 in three tables: a server log of 309,901 sessions (country, device, acquisition channel, session start and end), 40,212 purchases, and 1,800 rows of daily advertising costs by channel.

**What was done**
- Data check and preparation: no missing values or duplicates, column names brought to one style, dates converted to datetime, channel names checked for implicit duplicates.
- User profiles: the first visit of each user gives the acquisition date, channel, device and country, and the daily cost of each channel is split between the users it brought in to get each user's acquisition cost (CAC).
- Own functions for cohort metrics: Retention Rate, conversion, LTV and ROI, with an analysis horizon and exclusion of cohorts that have not yet "lived" the full horizon, plus functions for the charts (curves by lifetime and dynamics by acquisition date with a moving average).
- Audience overview: users and the share of paying users by country, device and channel.
- Marketing costs: total spend, split by channel, weekly and monthly dynamics, and the average CAC per channel.
- Payback analysis as of 1 November 2019 with a 14-day horizon (the business plan says a user should pay off within two weeks). Organic users were excluded because they cost nothing. LTV, ROI, CAC, conversion and retention were analysed in total and broken down by device, country and channel.
- Conclusions and recommendations for the marketing department.

**Result:** the advertising does not pay off. Total spend was about 105,500, and by day 14 the ROI comes close to 100% but never crosses it. User quality (LTV) stays stable, so the problem is the growing cost of acquisition, not worse users. The losses come from one place:
- **USA:** the biggest market (100,000 users, 6.9% of them pay, against about 4% in Europe), and the only country where the ads do not pay off. Ads pay off in the UK, France and Germany.
- **TipTop and FaceBoom:** these two channels work only in the USA and take 83% of the budget (52% and 31%). TipTop's CAC grew every month from July and reached 2.8 per user on average, 2.5 times more than FaceBoom (1.1). FaceBoom has the highest share of paying users (12.2%), but these users come back worse than even organic ones.
- **Devices:** ads do not pay off on iPhone and Mac. Most likely this is because these are the main devices of the US audience, not because of the devices themselves.

**Recommendations:** reconsider the price and terms of the TipTop contract, and change the payment model with TipTop and FaceBoom in the USA so that they are rewarded for keeping users, not only for the first purchase. Part of the budget can move to channels that already pay off in Europe.

**Next steps**
- Put exact numbers next to the charts: a table of 14-day ROI, CAC and LTV for each channel and country, so the conclusions do not depend on reading the curves by eye.
- Separate the effect of the country from the effect of the device: compare iPhone and Mac users outside the USA and inside the USA by channel.
- Look at payback over a longer horizon (30–60 days) to see whether US users pay off later, and check the June dip in ROI against the start of the large TipTop campaign.

**Stack:** Python, pandas, NumPy, matplotlib, datetime. Cohort analysis, unit economics (LTV, CAC, ROI), Retention Rate, conversion.

---

## Анализ бизнес-показателей

[EN](#business-performance-analysis) · **RU**

Исследование для развлекательного приложения, которое уже несколько месяцев терпит убытки, несмотря на большие вложения в рекламу. Задача - понять, почему реклама не окупается, и что стоит изменить отделу маркетинга. Данные охватывают около 150 000 пользователей, привлечённых с 1 мая по 27 октября 2019 года, и состоят из трёх таблиц: серверный лог на 309 901 сессию (страна, устройство, канал привлечения, начало и конец сессии), 40 212 покупок и 1 800 строк ежедневных расходов на рекламу по каналам.

**Что сделано**
- Проверка и подготовка данных: пропусков и дубликатов нет, названия столбцов приведены к одному стилю, даты переведены в datetime, названия каналов проверены на неявные дубликаты.
- Профили пользователей: по первому визиту определены дата привлечения, канал, устройство и страна, а дневные расходы каждого канала разделены между привлечёнными им пользователями, так получена стоимость привлечения каждого пользователя (CAC).
- Собственные функции для когортных метрик: Retention Rate, конверсия, LTV и ROI с горизонтом анализа и исключением когорт, которые ещё не «прожили» весь горизонт, а также функции для графиков (кривые по лайфтайму и динамика по дате привлечения со скользящим средним).
- Обзор аудитории: число пользователей и доля платящих по странам, устройствам и каналам.
- Расходы на маркетинг: общая сумма, распределение по каналам, динамика по неделям и месяцам, средний CAC по каналам.
- Анализ окупаемости на 1 ноября 2019 года с горизонтом 14 дней (по бизнес-плану пользователь должен окупиться за две недели). Органические пользователи исключены, так как за них ничего не платят. LTV, ROI, CAC, конверсия и удержание разобраны в целом и в разрезе устройств, стран и каналов.
- Выводы и рекомендации для отдела маркетинга.

**Результат:** реклама не окупается. Всего на неё потрачено около 105 500, и к 14-му дню ROI приближается к 100%, но так и не переходит этот порог. Качество пользователей (LTV) остаётся стабильным, значит, проблема в растущей стоимости привлечения, а не в том, что пользователи стали хуже. Убытки идут из одного места:
- **США:** самый большой рынок (100 000 пользователей, из них платят 6,9% против примерно 4% в Европе) и единственная страна, где реклама не окупается. В Великобритании, Франции и Германии реклама окупается.
- **TipTop и FaceBoom:** эти два канала работают только в США и забирают 83% бюджета (52% и 31%). CAC у TipTop рос каждый месяц начиная с июля и в среднем достиг 2,8 на пользователя, это в 2,5 раза больше, чем у FaceBoom (1,1). У FaceBoom самая высокая доля платящих (12,2%), но эти пользователи возвращаются хуже, чем даже органические.
- **Устройства:** реклама не окупается на iPhone и Mac. Скорее всего, это связано с тем, что это главные устройства американской аудитории, а не с самими устройствами.

**Рекомендации:** пересмотреть цену и условия договора с TipTop, а также изменить модель оплаты с TipTop и FaceBoom в США, чтобы каналы получали вознаграждение за удержание пользователей, а не только за первую покупку. Часть бюджета можно перенести в каналы, которые уже окупаются в Европе.

**Следующие шаги**
- Подкрепить графики точными цифрами: таблица ROI, CAC и LTV на 14-й день по каждому каналу и стране, чтобы выводы не зависели от чтения кривых на глаз.
- Отделить влияние страны от влияния устройства: сравнить пользователей iPhone и Mac вне США и внутри США по каналам.
- Посмотреть окупаемость на более длинном горизонте (30–60 дней), чтобы понять, окупаются ли американские пользователи позже, и сопоставить июньский провал ROI со стартом большой кампании в TipTop.

**Стек:** Python, pandas, NumPy, matplotlib, datetime. Когортный анализ, юнит-экономика (LTV, CAC, ROI), Retention Rate, конверсия.

<a href="Business Performance Analysis_ENG.ipynb" style="text-decoration:none;">
  <div style="display:inline-block; padding:10px 20px; font-size:18px; font-weight:bold; color:white; background-color:#007bff; border-radius:5px;">
    Go to the project / Перейти к проекту
  </div>
</a>
