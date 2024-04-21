---
layout: default
title: OpenSquat
parent: Cyber Threat Intelligence
nav_order: 1
---
# OpenSquat

What: #tool\
Where: #github\
Who: Andre Tenreiro\
When: since 11/10/2020\
How: [video]
{: .fs-3 .ls-10 .text-mono .code-example }

Сегодняшний гость - утилита OpenSquat, которая используется для поиска в списке зарегистрированных доменов имён похожих на домен вашей компании. Своего рода превентивная защита от фишинговых атак, омографов IDN, [бит]-  и [тайп]-сквоттинга, также в списке возможностей данной утилиты есть проверка на открытые 80/TCP и 443/TCP, а в работе использует формулы вычисления [расстояния Левенштейна] (советский и российский математик) и [сходство Джаро-Винклера].

По умолчанию подтягивает массив из доменных имён с [сайта], но мне показалось, что там недостаёт зоны .ru. Поэтому было принято решение немного поменять конфигурационный файл, заменив "родную" ссылку на:

```markdown
self.URL = ("https://domains-monitor.com/api/v1/$TOKEN/get/dailyupdate/list/text/")
```

Токен API можно получить, зарегистрировавшись на сайте domains-monitor.com, временной интервал выгрузки и её формат выбрать по своему усмотрению.
По итогам, мы ведём поиск по 1,5к+ зонам, включая совсем уж редкие.

Далее, есть возможность отправлять запросы к VT, дабы проверять репутацию доменного имени, однако, по дефолту, обращаясь к https://www.virustotal.com/ui/domain/ результат будет один:

```markdown
{'error': {'code': 'NotFoundError', 'message': 'Resource not found.'}}
```

в ответ на запрос любого домена, не важно какая у того репутация. В связи с этим, опять меняем исходный код, расширяя функциональность OpenSquat работой с API VT (ограничения бесплатной версии: 4 запроса в минуту и не более 500 запросов в день).

Корректировки:
```markdown
self.URL = "https://www.virustotal.com/api/v3/domains/" + self.domain

headers = {
"X-Apikey": "$APIKEY"
}

malicious = (
self.content
['data']
['attributes']
['last_analysis_stats']
['malicious'] )
```
Готово, вы восхитительны 😊
 
Последним этапом планируем в cron ежедневную задачу на запуск скрипта и мониторим раз в день results.txt

----
[video]:https://asciinema.org/a/361931
[сайта]:https://feeds.opensquat.com/
[бит]:https://habr.com/ru/post/125821/
[тайп]:https://www.kaspersky.ru/resource-center/definitions/what-is-typosquatting
[расстояния Левенштейна]:https://habr.com/ru/post/676858/
[сходство Джаро-Винклера]:https://ru.wikipedia.org/wiki/%D0%A1%D1%85%D0%BE%D0%B4%D1%81%D1%82%D0%B2%D0%BE_%D0%94%D0%B6%D0%B0%D1%80%D0%BE_%E2%80%94_%D0%92%D0%B8%D0%BD%D0%BA%D0%BB%D0%B5%D1%80%D0%B0