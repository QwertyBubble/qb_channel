---
layout: default
title: Phish App Concept
parent: Cyber Threat Intelligence
nav_order: 2
---
# Phish App Concept

What: #notes
{: .fs-3 .ls-10 .text-mono .code-example }

А помните был такой OpenSquat?
Решил [создать] простое приложение для Android (на базе любезно предложенных [Android Studio] шаблонов) и простенький сервер, который будет отдавать файлик с доменами, обновляемый кроном.
Для запуска сервера используем [NodeJs], а для компиляции и запуска клиента Android Studio.
Как идея: можно кастомизировать ответ от сервера, чтобы добавить побольше информации в клиент, можно добавить функциональность истории в приложение, можно добавить отчетность за период месяц/квартал, можно (нужно) предварительно проверять данные в части:
— есть ли за доменом сервер (200 OK по 80/TCP, 443/TCP);
— есть ли выданный доменному имени сертификат ([сабж], [вики]);
— есть ли контент на веб странице;
— etc...

Затем можно подумать в сторону определения приоритета критичности: если есть сервер, есть сертификат, есть контент, то такой домен получает уровень medium, а те, которые не дотянули — low (но всё таки они отправляются на мониторинг, авось через недельку что-то появится 🧐)

----
[сабд]:https://crt.sh/
[вики]:https://en.wikipedia.org/wiki/Certificate_Transparency
[NodeJs]:https://nodejs.org/en/
[создать]:https://github.com/QwertyBubble/phish_app
[Android Studio]:https://developer.android.com/studio