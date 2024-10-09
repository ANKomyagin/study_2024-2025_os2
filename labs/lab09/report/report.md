---
## Front matter
title: "Лабораторная работа №9"
subtitle: "Управление SELinux"
author: "Комягин Андрей Николаевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получить навыки работы с контекстом безопасности и политиками SELinux.

# Выполнение лабораторной работы

## Управление режимами SELinux

Получим полномочия администратора, проверим статус службы Very Secure FTP, Установим службу Very Secure FTP (рис. [-@fig:001]).

![Установка службы Very Secure FTP](image/1.PNG){#fig:001 width=70%}

Запустим службу Very Secure FTP. Проверим статус службы Very Secure FTP (рис. [-@fig:002]).

![Статус Very Secure FTP](image/2.PNG){#fig:002 width=70%}

Добавим службу Very Secure FTP в автозапуск при загрузке операционной системы. Удалим службу
из автозапуска (рис. [-@fig:003]).

![автозапуск](image/3.PNG){#fig:003 width=70%}

Выведем на экран символические ссылки, ответственные за запуск различных сервисов, добавим службу Very Secure FTP в автозапуск и выведем на экран символические ссылки(рис. [-@fig:004]).

![символические ссылки](image/4.PNG){#fig:004 width=70%}

Выведем на экран список зависимостей юнита (рис. [-@fig:005]).

![Список зависимостей](image/5.PNG){#fig:005 width=70%}

Выведем на экран список юнитов, которые зависят от данного юнита(рис. [-@fig:006]) 

![Список юнитов, зависящих от юнита](image/6.PNG){#fig:006 width=70%}

## Конфликты юнитов

Некоторые юниты могут конфликтовать друг с другом и, соответственно, не могут работать одновременно

Установим iptables (рис. [-@fig:007])

![установка iptables](image/7.PNG){#fig:007 width=70%}

Проверим статус firewalld и iptables, попробуем запустить firewalld и iptables (рис. [-@fig:008]).

![запуск конфликтующих юнитов](image/8.PNG){#fig:008 width=70%}

Конфликты юнитов(рис. [-@fig:009])

![Конфликты юнитов](image/9.PNG){#fig:009 width=70%}

1. Настройки конфликтов **firewalld.service**

- Conflicts=iptables.service ip6tables.service ebtables.service ipset.service nftables.service

- Это означает, что firewalld не может работать одновременно с iptables и другими упомянутыми сервисами. Если firewalld запущен, то все перечисленные сервисы будут остановлены.

2. Настройки конфликтов **/iptables.service**

- Отсутствие явных конфликтов в этом файле, но подразумевается, что он будет конфликтовать с firewalld, поскольку оба сервиса пытаются управлять правилами межсетевого экрана.

Выгрузим службу iptables, заблокируем запуск iptables, попробуем запустить iptables. Попробуем добавить iptables в автозапуск(рис. [-@fig:010])

![блокировка iptables](image/10.PNG){#fig:010 width=70%}

## Изолируемые цели


Перейдем в каталог systemd и найдите список всех целей, которые можно изолировать(рис. [-@fig:011])

![Изолируемые цели](image/11.PNG){#fig:011 width=70%}

Переключим операционную систему в режим восстановления(рис. [-@fig:012])

![режим восстановления](image/12.PNG){#fig:012 width=70%}

## Цель по умолчанию

Выведем на экран цель, установленную по умолчанию.  (рис. [-@fig:013])

![цель по умолчанию](image/13.PNG){#fig:013 width=70%}

Перегрузим систему командой reboot. Вновь перегрузим систему командой reboot. Убедимся, что система загрузилась в графическом режиме(рис. [-@fig:014])

![режимы системы](image/14.PNG){#fig:014 width=70%}



# Контрольные вопросы

1. Что такое юнит (unit)? Приведите примеры.

   Юнит в контексте systemd — это абстракция, представляющая собой объект, который управляется системой и может быть запущен или остановлен. Существует несколько типов юнитов, включая:

   - Сервисные юниты (service): представляют собой службы, которые выполняют определенные задачи (например, httpd.service для Apache).
   
   - Целевые юниты (target): группы других юнитов, которые могут быть активированы вместе (например, multi-user.target).
   
   - Монтажные юниты (mount): представляют собой точки монтирования файловых систем.
   
   - Сокетные юниты (socket): управляют сокетами для межпроцессного взаимодействия.

2. Какая команда позволяет вам убедиться, что цель больше не входит в список автоматического запуска при загрузке системы?

   Для этого используется команда:
   
      **sudo systemctl disable <имя_цели>**
   

3. Какую команду вы должны использовать для отображения всех сервисных юнитов, которые в настоящее время загружены?

   Для отображения всех загруженных сервисных юнитов используйте команду:
   
      **systemctl list-units --type=service**
   

4. Как создать потребность (wants) в сервисе?

   Для создания зависимости типа "wants" можно использовать команду:
   
      **sudo systemctl add-wants <имя_юнита> <имя_сервиса>**
   

5. Как переключить текущее состояние на цель восстановления (rescue target)?

   Для переключения на цель восстановления используйте команду:
   
      **sudo systemctl isolate rescue.target**
   

6. Поясните причину получения сообщения о том, что цель не может быть изолирована.

   Сообщение о том, что цель не может быть изолирована, может возникнуть, если цель имеет активные зависимости или другие юниты, которые не могут быть остановлены без нарушения работы системы. Это может происходить из-за активных служб или процессов, которые требуют других юнитов.

## 7. Вы хотите отключить службу systemd, но, прежде чем сделать это, вы хотите узнать, какие другие юниты зависят от этой службы. Какую команду вы бы использовали?

   Для отображения зависимостей используйте команду:
   
      **systemctl list-dependencies <имя_службы>**

# Вывод

В ходе выполнения лабораторной работы я получил навыки управления системными службами операционной системы посредством systemd.

# Список литературы{.unnumbered}

[Туис, курс Администрирование операционных систем](https://esystem.rudn.ru/course/view.php?id=5946)
