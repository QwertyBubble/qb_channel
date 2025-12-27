---
layout: default
title: Attribution & Clusterization
parent: Cyber Threat Intelligence
nav_order: 14
---
# Feedly Connector

What: #platform\
Where: #github\
Who: Filigran\
When: 28/06/2019\
How: via docker
{: .fs-3 .ls-10 .text-mono .code-example }

Друзья, здравствуйте!

Короткая заметка про коннектор Feedly для OpenCTI.

По умолчанию, разработчики устанавливают интервал запросов к своим серверам [в один час]. Но надо также принять во внимание квоту на API-запросы, которую они устанавливают в рамках trial-периода для нашей учётной записи. А квота там на всего на 500 запросов, которые израсходуются меньше, чем за три дня🤷‍♂️ 
Т.к. OpenCTI используется просто как новостной хаб, то нам необязательно часто обращаться к серверам Feedly для получения данных. Главное, чтобы данные в принципе поступали без перерывов. Устанавливаем интервал в 180 минут и следим, чтобы квоты хватило на весь наш триальный период.

Подробнее про Feedly рассказывал вот [здесь]\
А про коннектор [тут]

Безлимитных вам API-запросов! 🤓

Со средой 🍸

----
[в один час]:https://github.com/OpenCTI-Platform/connectors/blob/master/external-import/feedly/docker-compose.yml
[здесь]:https://t.me/qb_channel/32
[тут]:https://t.me/qb_channel/51