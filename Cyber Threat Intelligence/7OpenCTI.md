---
layout: default
title: OpenCTI ( Part III of V )
parent: Cyber Threat Intelligence
nav_order: 7
---
# OpenCTI ( Part III of V )

What: #platform\
Where: #github\
Who: Filigran\
When: 28/06/2019\
How: via docker
{: .fs-3 .ls-10 .text-mono .code-example }

Мы уже [подняли] платформу, [разобрались] со всем набором токенов и вдохнули жизнь добавили в неё актуальных данных из мира ИБ. А как ещё можно складировать новости и собирать информацию? 🌐

Когда поработаешь долгое время с веб-интерфейсом Feedly, обязательно заметишь нехватку поиска по прочитанным новостям. А иногда хотелось бы почитать, скажем, что "полезного" сделали CharmingCypress за последний год? Хотелось бы с отчётами и по тематике ИБ, а не про кипарисы 🌱 И вот 27 августа прошлого года Filigran внедряет в свой продукт в релизе 5.10.0 по заведённой от сооснователя [фиче]  RSS Feeds.

Функциональность нововведения достаточно проста. Идём в Data → Ingestion → RSS Feeds. Нажимаем на кнопку добавления фида и заполняем необходимые данные. Можно указать описание источника, тип, TLP и некоторые другие параметры. На этом вся настройка заканчивается, нам остаётся только подождать пока посты начнут загружаться в платформу.

Какие плюсы:\
✅ будут добавляться не только новости с отчётами, но и теги, которые обычно идут в довесок к новостям. и по этим тегам можно искать нужную информацию.

Какие минусы:\
❌ не будут выстраиваться новые связи или парсится акторы с TTPs. это будет просто новостной хаб.\
❌ нельзя добавить новости списком, придётся каждый источник добавлять вручную. Работы буквально на час/два, но если у вас есть идеи по автоматизации, то напишите)

Если не хочется заморачиваться с токенами из предыдущего поста, то возможно вам подойдёт вот этот бюджетный вариант с агрегацией новостного фона.

----
[подняли]:https://t.me/qb_channel/43
[разобрались]:https://t.me/qb_channel/51
[фиче]:https://github.com/OpenCTI-Platform/opencti/issues/2864