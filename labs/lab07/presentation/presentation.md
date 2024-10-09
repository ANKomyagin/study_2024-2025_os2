---
## Front matter
lang: ru-RU
title: Лабораторная работа №7
subtitle: Управление журналами событий в системе
author:
  - Комягин А. Н.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 09 октября 2024

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'


##Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
---


## Цель

Получить навыки работы с журналами мониторинга различных событий в системе.

# Выполнение лабораторной работы

# Мониторинг журнала системных событий в реальном времени

## Запустим мониторинг событий

![](./image/1.PNG){width=100%}

## отображение ошибки в мониторинге

![](./image/2.PNG){width=100%}

## logger hello

![](./image/3.PNG){width=100%}

## мониторинг сообщений безопасности

![](./image/4.PNG){width=100%}

## Установка Apache и запуск веб-службы

![](./image/5.PNG){width=100%}

## журнал ошибок веб-службы

![](./image/6.PNG){width=100%}

## /etc/httpd/conf/httpd.conf

![](./image/7.PNG){width=80%}

## файл мониторинга

![](./image/8.PNG){width=80%}

##  перезагрузка конфигураций

![](./image/9.PNG){width=80%}

## Мониторинг отладки

![](./image/10.PNG){width=80%}

## мониторинг

![](./image/11.PNG){width=80%}

# Использование journalctl

## содержимое журнала событий

![](./image/12.PNG){width=80%}

## реальное время

![](./image/13.PNG){width=80%}

## последние строки журнала

![](./image/14.PNG){width=80%}

## сообщения об ошибках

![](image/15.PNG){width=70%}

## сообщения со вчерашнего дня

![](image/16.PNG){width=70%}

## доп информация о sshd

![](image/17.PNG){width=70%}

# Постоянный журнал journald

## доп информация о sshd

![](image/18.PNG){width=70%}

# Контрольные вопросы

## 1. Какой файл используется для настройки rsyslogd?

   - Основной файл конфигурации для rsyslogd — это /etc/rsyslog.conf.

## 2. В каком файле журнала rsyslogd содержатся сообщения, связанные с аутентификацией?


   - Сообщения, связанные с аутентификацией, обычно записываются в файл /var/log/auth.log (или /var/log/secure в некоторых дистрибутивах).

## 3. Если вы ничего не настроите, то сколько времени потребуется для ротации файлов журналов?


   - По умолчанию ротация файлов журналов происходит раз в неделю (это может варьироваться в зависимости от конфигурации системы и используемого инструмента ротации, например, logrotate).

## 4. Какую строку следует добавить в конфигурацию для записи всех сообщений с приоритетом info в файл /var/log/messages.info?

   - Добавим строку: *.info /var/log/messages.info.

## 5. Какая команда позволяет вам видеть сообщения журнала в режиме реального времени?

   - Команда tail -f /var/log/syslog (или другой соответствующий файл журнала).

## 6. Какая команда позволяет вам видеть все сообщения журнала, которые были написаны для PID 1 между 9:00 и 15:00?

   - Используем команду: journalctl _PID=1 --since "YYYY-MM-DD 09:00" --until "YYYY-MM-DD 15:00" (замените YYYY-MM-DD на нужную дату).

## 7. Какая команда позволяет вам видеть сообщения journald после последней перезагрузки системы?

   - Команда: journalctl -b.

## 8. Какая процедура позволяет сделать журнал journald постоянным?

   - Чтобы сделать журнал journald постоянным, нужно отредактировать файл конфигурации /etc/systemd/journald.conf и установить параметр Storage=persistent. Затем перезапустите службу journald с помощью команды systemctl restart systemd-journald.



# Вывод

## Вывод

В ходе выполнения лабораторной работы я получил навыки работы с журналами мониторинга различных событий в системе.






















