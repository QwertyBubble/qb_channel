---
layout: default
title: SIGMA 2.0
parent: Cyber Threat Intelligence
nav_order: 13
---
# SIGMA 2.0

What: #sigma\
Where: #vscode\
Who: humpalum\
When: 15/03/2022\
How: via extension
{: .fs-3 .ls-10 .text-mono .code-example }

Друзья, здравствуйте!

Третий пост про SIGMA будет посвящён обновлению репозитория этого проекта. На этой неделе было много различных новостей и публикаций материалов, но вот про обновление маловато информации. Исправляем 🤓

После прочтения всех статей выделил для себя два главных изменения:\
1️⃣ теперь можно писать корреляционные правила на SIGMA;\
2️⃣ появилась бОльшая связность между правилами за счёт обновленного атрибута filter. Если все привыкли использовать атрибут filter только для того, чтобы в блоке condition написать selection and not filter, теперь можно создать отдельную папку с исключениями и следить за ними, добавляя правила. [Подробнее] про фильтры. Связность также можно показывать за счёт атрибута related ([пример]).

Что насчёт корреляции? Теперь появилась возможность описать непосредственно корреляционную логику с помощью SIGMA. Пример:\
➖ несколько неудачных событий на одном хосте;\
➖ неудачное событие на одном хосте, но с нескольких источников;\
➖ несколько событий произошли в заданный временной интервал.

Представляют из себя совсем отдельный файлик с блоком correlation, вида:
~~~
title: Multiple failed logons for a single user (possible brute force attack)
status: test
correlation:
    type: event_count
    rules:
        - failed_logon
    group-by:
        - TargetUserName
        - TargetDomainName
    timespan: 5m
    condition:
        gte: 10
~~~
где в блоке rules перечислены правила, участвующие в корреляции.

Более подробно про корреляцию можно почитать у самих разработчиков проекта в их [блоге] тут и на [гитхабе].

В оригинальном посте также [заявлено], что с приходом второй версии появились новые модификаторы для различного типа полей, но как будто бы они появились уже в [начале] этого года. Кстати, у коллег релиз версии 2.0.0 получился несколько растянутым на весь 2024, ну или просто с минорной версионностью не стали заморачиваться. 

А ещё коллеги полностью [отказались] от Rx-схемы структуры правил и перешли на JSON. Практически уверен, что всё дело в удобстве сопровождения.

Итоговая обновлённая спецификация [тут], а дифф версий можно почитать [здесь].

Понятно, что вручную поддерживать всю эту функциональность очень сложно. На помощь разумеется приходит библиотека [pySigma], а ещё ждём, когда humpalum выпустит очередное обновление своего приложения для VS Code, а то с 24 января тишина.

Красивых вам правил! 

Всем хороших выходных и берегите себя  👌

----
[пример]:https://github.com/SigmaHQ/sigma/blob/master/rules/windows/registry/registry_set/registry_set_windows_defender_tamper.yml
[блоге]:https://blog.sigmahq.io/introducing-sigma-correlations-52fe377f2527
[гитхабе]:https://github.com/SigmaHQ/sigma-specification/blob/main/specification/sigma-correlation-rules-specification.md
[заявлено]:https://blog.sigmahq.io/introducing-sigma-specification-v2-0-25f81a926ff0

[Подробнее]:https://blog.sigmahq.io/introducing-sigma-filters-204bd8496273
[пример]:https://github.com/SigmaHQ/sigma/blob/master/rules/windows/registry/registry_set/registry_set_windows_defender_tamper.yml
[блоге]:https://blog.sigmahq.io/introducing-sigma-correlations-52fe377f2527
[гитхабе]:https://github.com/SigmaHQ/sigma-specification/blob/main/specification/sigma-correlation-rules-specification.md
[заявлено]:https://blog.sigmahq.io/introducing-sigma-specification-v2-0-25f81a926ff0
[начале]:https://github.com/SigmaHQ/sigma-specification/blob/ebc2f178cf8a280f08200f438cf852753d784dd7/appendix/appendix_modifier.md
[отказались]:https://github.com/SigmaHQ/sigma-specification/tree/main/json-schema
[тут]:https://github.com/SigmaHQ/sigma-specification/blob/main/specification/sigma-rules-specification.md
[здесь]:https://github.com/SigmaHQ/sigma-specification/blob/main/other/version-2-changes.md
[pySigma]:https://github.com/SigmaHQ/pySigma