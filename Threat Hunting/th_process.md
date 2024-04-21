---
layout: default
title: Threat Hunting Process
parent: Threat Hunting
nav_order: 3
---
# Threat Hunting Process

What: #notes
{: .fs-3 .ls-10 .text-mono .code-example }

Захотел сделать подборку материалов ([часть 1] и [часть 2]) по процессу поиска киберугроз.
После прочтения появится понимание по терминам, по инструментарию и как выглядит процесс со стороны. Kaspersky, SANS, исследования, опросы, презентации зарубежных коллег к вашим услугам 🤓

Несколько слов про подходы по процессу:

_Intelligence-Based Threat Hunting_
Подразумевает поиск IOC/TTP в вашей инфраструктуре. Под IOC совсем не обязательно понимать только лишь hash/ip/domain, это также могут быть ключи реестра, например, или User-Agent в сетевом пакете. 

_Leadless Threat Hunting_
Подразумевает выстраивание гипотез на основе собственной экспертизы. Осуществляется сбор и анализ данных с источников событий (конечные хосты пользователей, сервера, межсетевые экраны и пр.) Цель, как и у всех остальных, выявить аномальное, отклоняющееся от нормы, поведение.

_Crown Jewels Threat Hunting_
При таком подходе гипотеза формулируется в фокусе угроз для критичных активов и информации (КТ, ПДн). Допустим, существует ряд критичных активов и необходимо проверять, чтобы подключение к ним осуществлялось только с использованием технических учётных записей (ну, или из белого списка)

_Outcome-Based Threat Hunting_
Текущий подход подразумевает анализ закрытых инцидентов, прошлые оповещения об отправке файл в карантин, уже завершённые расследования для того, чтобы выявить связь и сработать на упреждение для новых векторов атак. Цель: извлечение уроков из прошлого опыта, чтобы гарантировать защиту от повторных атак.

_Compliance-Based Threat Hunting_
В данном случае необходимо следить за обеспечением соответствия внутренним, отраслевым и государственным политикам путём поиска их несоблюдения. Например, кондифиденциальные данные на общедоступном сетевом диске, коммерческая тайна в облаке и т.п.

_Machine Learning-Based Hunting_
Куда же без ML, да? Допустим, что ваше корпоративное решение обучилось на терабайтах данных по пользователю ~~и он уволился~~ и успешно может демонстрировать отклонения от нормы по написанным правилам для behavior indicators of compromise. Подход позволит существенно сэкономить человеческие ресурсы аналитиков.

А ~~завершающим штрихом~~ 🍒 вишенкой на торте пусть будет немного ссылок:
 
a) Коллеги из BI.ZONE в своё время написали [раз], [два], [три] отличные статьи, в которых описывают все этапы атаки ([thedfirreport.com] лайк) со стильной графикой и нестильным EventViewer от MS.
b) Threat Hunting и матрица ATT&CK от ресурса digitalguardian. Изложение также в трёх ([первый], [второй], [третий]) ~~актах~~ статьях о том, как связывать одно с другим, чтобы складывалась целая картинка.
с) Про [подход] и [стратегию] в команде Microsoft Detection and Response Team (DART). Реклама своих решений —  присутствует ✅

----
[часть 1]:https://t.me/qb_channel/25
[часть 2]:https://t.me/qb_channel/27
[раз]:https://cyberpolygon.com/ru/materials/threat-hunting-why-might-you-need-it/
[два]:https://cyberpolygon.com/ru/materials/threat-hunting-in-action/
[три]:https://cyberpolygon.com/ru/materials/hunting-for-advanced-tactics-techniques-and-procedures-ttps/
[thedfirreport.com]:https://thedfirreport.com/
[первый]:https://digitalguardian.com/blog/threat-hunting-mitres-attck-framework-part-1
[второй]:https://digitalguardian.com/blog/threat-hunting-mitres-attck-framework-part-2-%E2%80%93-advanced-use-cases
[третий]:https://digitalguardian.com/blog/threat-hunting-mitre-attck-framework-part-3-high-fidelity
[подход]:https://www.microsoft.com/en-us/security/blog/2022/09/08/part-1-the-art-and-science-of-threat-hunting/
[стратегию]:https://www.microsoft.com/en-us/security/blog/2022/09/21/the-art-and-science-behind-microsoft-threat-hunting-part-2/
