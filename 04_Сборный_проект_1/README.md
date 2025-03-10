# Исследование о рынке российского кинопроката  

**Заказчик исследования** — Министерство культуры Российской Федерации.  

**Цель:** изучить рынок российского кинопроката и выявить текущие тренды.  
Уделить внимание фильмам, которые получили государственную поддержку. Попробовать ответить на вопрос, насколько такие фильмы интересны зрителю.  

**Данные:** взяты на портале открытых данных Министерства культуры.  
Набор данных содержит информацию о прокатных удостоверениях, сборах и государственной поддержке фильмов, а также информацию с сайта КиноПоиск.

## Используемые библиотеки  
`Pandas`, `Matplotlib`, `Seaborn`

## Вывод  
В рамках исследования данных из открытых источников Министерства культыры РФ с данными о кинофильмах, выходивших в российском кинопрокате, выполнено:

датафреймы mkrf_movies и mkrf_shows объединели в единый датасет df таким образом, что все объекты из датасета mkrf_movies вошли в получившийся датасет.

проверили типы данных для всех столбцов датасета. Значения столбца show_start_date преобразовали в формат datetime. При попытке первода значений столбца ratings в формат float, обнаружили значения в формате xx%, природа возникновения которых неясна. Заменили данные значения на 'NaN'

изучили пропуски в датафрейме. По информации из открытых источников восстановили пропуски в столбце production_country. Пропуски в столбцах film_studio, director, producer и genre заменили на 'unknown'.

проверили датасет на наличие неявных дубликатов, а также на налчие дубликатов по подмножеству. Обнаружили дубликаты по номеру прокатного удостоверения (возможно ошибочно задублировано при выдаче ПУ), а также дубликаты по наименованию и режиссеру фильма (в результате многократного получения прокатных удостоверений одними и теми же фильмами)

провели анализ категориальных значений в столбцах датафрейма. Практически во всех столбцах с категориальными значениями есть общая проблема - наличие пробелов до или после названия значений. Также по открытым источникам заменели наименование некорректных стран - производителей фильмов, также устранили ошибки, образованные в результате использования латинской раскладки для русских слов.

провели анализ содержания столбцов с количественными значениями. Обнаружили нулевые значения в столбце budget, при ненулевых значениях в столбцах господдержки, для этого же фильма.

столбцы с новыми данными, необходимыми для дальнейшего анализа, добавлены в датасет, это:

show_start_year - год проката фильма;

main_director - главный режиссер фильма;

main_genre - основной жанр фильма;

state_support_share - доля государственной поддержки в бюджете фильма

определили количество фильмов выходившее в прокат каждый год (меньше всего в 2010 году - 105, больше всего в 2019 году - 530. Определили, какую долю составляют фильмы с указанной информацией о прокате в кинотеатрах (меньше всего в 2010 году - 0.11, больше всего в 2017 году - 0.71). Построили графики, иллюстрирующие динамику изменения доли фильмов с указанной информацией о прокате, по годам. По итогам проведенного исследования, можно прийти к выводу, что полнее всего в данных представлен 2017 год. Определена минимальная общая сумма проката - 2.43 млн. руб. для 2010 года и максимальная сумма - 49.67 млрд. руб.Определены средняя и медианная сумма сборов для каждого года, результаты представлены в сводной таблице. Проведен анализ о влиянии возрастного ограничения аудитории («6+», «12+», «16+», «18+» и т. д.) на сборы фильма в прокате в период с 2015 по 2019 год. В сумме по периоду с 2015 по 2019 год больше всего сборов собрали фильмы возрастной категории 16+. В зависимости от года имеются изменения по сумме сборов по возрастным категориям. Например, ранее отмеченная категория 16+, в 2015 году собрала в прокате существенно меньше, чем категория 12+ и в 2019 году несущественно меньше, чем 6+. Зависимость общей суммы сборов в каждой категории зависит от количества фильмов для данной категории в том или ином году и от средней суммы сборов с одного фильма, который в свою очередь больше зависит от грамотно проведенных маркетинговых и рекламной компании, привлечения известных артистов или причастности к какой-либо популярной серии фильмов, чем от реальных статистических показателей, таких как жанр или рейтинг.

провели анализ данных по фильмам, вышедшим в российский кинопрокат с 2013 по 2019 год и получившим государственную поддержку. Выявили, какие суммы государственной поддержки выделялись за весь рассматриваемый период (в том числе возвратная и невозвратная поддержка, а также распределение данной помощи по годам. По итогу: в период с 2013-го п 2019-й годы на поддержку российского кинематографа было выделено государственной поддержки:

20 200 688 312 руб., из них:

3 939 000 000 руб. - возвратная поддержка

16 261 688 312 руб. - невозвратная поддержка

Меньше всего поддержки кинематографу было выделено в 2014 году, больше всего в 2017. Доля государственной поддержки в общем бюджете фильмов, для которых она выделялась, колеблется от 0,46 (2017 год) до 0,53 (2016 год).

Проанализирована окупаемость фильмов с государственной поддержкой по общему бюджету и по сумме возвращаемой господдержки:

общую сумму бюджета в прокате смогли окупить 35,35%

возвращаемую сумму господдержки собрали в прокате 73,73%

Определены топ-10 наилучших и наихудших фильмов по окупаемости. Проанализировано наличие взаимосвязи между долей государственной поддержки и рейтингом фильма - закономерностей не выявлено.

Получено среднее значение рейтинга российских фильмов получивших господдержку (5,57) и не получавших таковой (6,14).

Проанализировано кто из режиссеров получил больше и меньше всего государственной поддержки. Сформированы соответесвующие топ-20.

Исследованы суммарные значения господдержки по источникам финансирования: больше всего поддержки выделено "Фондом кино" - 14,18 млрд. рублей, меньше всего выделено при софинансировании "Фондом Кино" и Министерством культуры - 1,19 млрд. рублей.

Проанализировано выделение возвращаемой, невозвращаемой господдержки по годам - выявдено что Фонд Кино с 2014 года часть поддержки выделяет в возвращаемом виде, в то время как Министерство культуры всегда выделяет невозвращаемую поддержку.

Определены средний и медианные рейтинги и суммы сборов фильмов, в зависимости от источника выделения господдержки: фильмы финансируемые Министерством культуры имеют чуть больший рейтинг (как средний, так и медианный), относительно фильмов, финансируемых Фондом кино. При этом фильмы финансируемые Фондом кино показывают средние и медианные сборы на порядок больше, фильмов Минкульта. Cуммарные сборы за рассматриваемый период, для фильмов с господдержкой составили 42,11 млрд. рублей, для фильмов без господдержки - 10,09 млрд. руб.

Рекомендации по повышению эффективности господдержки кинематографа:

возрастные категории: 6+ и 12+ (т.к. показывают наибольшие средние сборы с 1 фильма) жанры: топ жанров с наибольшими медианными сборами представлен на графике выше(топ-5: история, cпортб приключения, биография, мультфильм) режиссеры: топ-20 режиссеров с наибольшими средними сборами представлен в сводной таблице выше (топ-5: А.Мегердичев, А.Сидоров, О.Трофим, Н.Лебедев, К.Шипенко. Рекомендации даны по значениям сборов, а не рейтинга, из за того, что как показало данное исследование, высокий ррейтинг не всегда гарантирует высокие сборы в прокате.
