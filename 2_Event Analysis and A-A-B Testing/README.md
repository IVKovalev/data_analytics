# Event Analysis and A/A/B Testing

**EN** · [RU](#анализ-событий-и-aab-тестирование)

Product analytics for a food delivery startup's mobile app. The task has two parts: build the sales funnel and find where users drop off, then read an A/A/B test of a new app font. The dataset is an event log of 244,126 records (25 July – 7 August 2019) with 4 fields: event name, user ID, timestamp and experiment group (246 and 247 are control groups A1 and A2, 248 is test group B with the new font).

**What was done**
- Data cleaning: removed 413 full duplicates (0.17%), converted Unix timestamps to datetime and checked that no user is in more than one group.
- Data validation: the event histogram showed that the log is nearly empty before 1 August, so only the 7 full days of August were kept. This cost 1.2% of events and 0.2% of users, and all three groups stayed balanced (2,484 / 2,513 / 2,537 users). The median was used for events per user (20) because a few users have up to ~2,300 events.
- Funnel analysis by unique users: Main screen → Offers → Cart → Payment success, with step-to-step conversion and a plotly funnel chart. The Tutorial was left out, because only 840 users opened it and it is not a required step.
- A/A test (A1 vs A2) to check that the groups were split correctly, then A1 vs B, A2 vs B and A1+A2 vs B at every funnel step, using a two-proportion z-test.
- Sensitivity to the significance level: the same tests at α = 0.1 and with the Bonferroni correction (α = 0.0125).

**Result:** the biggest drop-off is at the first step: only 62% of users go from the Main screen to Offers. After that, 81% go on to the Cart and 95% from the Cart to payment, so 47.7% of users who see the Main screen end up paying. The A/A test found no differences between A1 and A2, so the split is correct. The new font showed no statistically significant effect at any step against either control group or both combined (α = 0.05 and with the Bonferroni correction). The only difference at α = 0.1 (Cart, A1 vs B, p = 0.08) is most likely a false positive from multiple testing. Recommendation: the new font gives no advantage. Work on the Main screen → Offers step instead (recommendations, promotions, product sets), and run the test longer before making a final decision.

**Next steps**
- Apply the correction to the whole family of tests (16 comparisons, not 4), for example with the Holm method, and calculate the minimum detectable effect for ~2,500 users per group to show how small a change the test could find.
- Build a strict sequential funnel (only users who passed the previous step) and check users who reach payment without the Main screen or Cart.
- Look at the test results by day to check for a novelty effect and the stability of the metrics.

**Stack:** Python, pandas, NumPy, matplotlib, plotly, SciPy (stats), math.

---

## Анализ событий и A/A/B-тестирование

[EN](#event-analysis-and-aab-testing) · **RU**

Продуктовая аналитика мобильного приложения стартапа по продаже продуктов питания. Задача из двух частей: построить воронку продаж и найти, где теряются пользователи, затем оценить результаты A/A/B-теста нового шрифта в приложении. Данные - лог событий из 244 126 записей (25 июля – 7 августа 2019 года) с 4 полями: название события, идентификатор пользователя, время события и номер группы эксперимента (246 и 247 - контрольные группы A1 и A2, 248 - тестовая группа B с новым шрифтом).

**Что сделано**
- Очистка данных: удалены 413 явных дубликатов (0,17%), Unix-время переведено в datetime, проверено, что ни один пользователь не попал в несколько групп.
- Проверка данных: гистограмма событий показала, что до 1 августа лог почти пустой, поэтому оставлены только 7 полных дней августа. Потери составили 1,2% событий и 0,2% пользователей, все три группы остались сбалансированными (2 484 / 2 513 / 2 537 пользователей). Для числа событий на пользователя использована медиана (20), так как у отдельных пользователей до ~2 300 событий.
- Анализ воронки по уникальным пользователям: Главный экран → Каталог → Корзина → Успешная оплата, с конверсией между шагами и визуализацией воронки в plotly. Обучение (Tutorial) исключено: его открыли только 840 пользователей, и это не обязательный шаг.
- A/A-тест (A1 и A2) для проверки корректности разбиения на группы, затем сравнения A1 и B, A2 и B, A1+A2 и B на каждом шаге воронки с помощью z-теста для двух долей.
- Чувствительность к уровню значимости: те же тесты при α = 0,1 и с поправкой Бонферрони (α = 0,0125).

**Результат:** больше всего пользователей теряется на первом шаге: с Главного экрана в Каталог переходят только 62%. Дальше в Корзину переходят 81%, из Корзины к оплате - 95%, так что до оплаты доходят 47,7% пользователей, увидевших Главный экран. A/A-тест не нашёл различий между A1 и A2, значит, разбиение корректное. Новый шрифт не дал статистически значимого эффекта ни на одном шаге ни против одной из контрольных групп, ни против их объединения (при α = 0,05 и с поправкой Бонферрони). Единственное различие при α = 0,1 (Корзина, A1 и B, p = 0,08) скорее всего ложноположительное из-за множественных проверок. Рекомендация: новый шрифт преимуществ не даёт. Работать стоит над переходом с Главного экрана в Каталог (рекомендации, акции, наборы продуктов), а тест продлить, прежде чем принимать окончательное решение.

**Следующие шаги**
- Применить поправку ко всему семейству тестов (16 сравнений, а не 4), например методом Холма, и рассчитать минимальный обнаруживаемый эффект для ~2 500 пользователей в группе, чтобы показать, насколько малое изменение тест мог заметить.
- Построить строгую последовательную воронку (только пользователи, прошедшие предыдущий шаг) и проверить пользователей, которые доходят до оплаты, минуя Главный экран или Корзину.
- Посмотреть результаты теста по дням, чтобы проверить эффект новизны и стабильность метрик.

**Стек:** Python, pandas, NumPy, matplotlib, plotly, SciPy (stats), math.

<a href="Event Analysis and A-A-B Testing_ENG.ipynb" style="text-decoration:none;">
  <div style="display:inline-block; padding:10px 20px; font-size:18px; font-weight:bold; color:white; background-color:#007bff; border-radius:5px;">
    Go to the project / Перейти к проекту
  </div>
</a>
