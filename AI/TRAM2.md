---
layout: default
title: Threat Report ATT&CK Mapping 2 (TRAM)
parent: Artificial Intelligence
nav_order: 2
---
# Threat Report ATT&CK Mapping (TRAM)

What: #platform\
Where: #github\
Who: #mitre\
When: 29/10/2019\
How: via docker
{: .fs-3 .ls-10 .text-mono .code-example }

Прошло полтора года с момента прошлой заметки, и полгода с момента выхода [релиза] маппера TTPs от MITRE. Самое время протестировать. В плане установки всё осталось на месте: качаем [docker-compose.yaml], поднимаем демона, > docker-compose up и идём смотреть в браузер на платформу. 
А что поменялось?
— A new machine learning option based on large language models (LLMs).
— LLM models can be fine tuned on your own GPU systems (or Google Colab) using the included Jupyter notebooks.
— Can also run LLM models in Jupyter notebooks, either to run inference on GPU hardware or to get machine-readable results.

Также поменялся массив с обучающими данными — Bootstrap Training Data.
Я взял [отчёт] от команды Unit42 (PaloAlto) и загрузил в TRAM. Платформа поставила отчёт в очередь на анализ и через некоторое время предложила проверить 600 строк, которые она надёргала из отчёта. Ожидал, что это сделают за меня, честно говоря 🥲 Результат анализа можно выгрузить в .json и туда складываются предложенные техники для 600 предложений. Как с этим работать аналитику дальше? Для готового решения из коробки пока рановато, судя по всему. Наверняка всё дело в моделях. Математических. 

Решил зайти с другой стороны и спросить у ChatGPT про техники ATT&CK, загрузив тот же отчёт. "Think like threat intelligence analyst..." и вот это вот всё.
В общем, в матрицу ATT&CK при дефолтных настройках ChatGPT не умеет. Скриншот ниже 🤔

Возможно, истина где-то рядом и надо в обязательном порядке обучать модели, но пока что готового помощника для решения задачки не нашёл.

----
[релиза]:https://github.com/center-for-threat-informed-defense/tram
[docker-compose.yaml]:https://github.com/center-for-threat-informed-defense/tram/wiki/Installation
[отчёт]:https://unit42.paloaltonetworks.com/apateweb-scareware-pup-delivery-campaign/