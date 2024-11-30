---
## Front matter
lang: ru-RU
title: Лабораторная работа №13
subtitle: "Фильтр пакетов"
author:
  - Комягин А.Н.
institute:
  - Российский университет дружбы народов, Москва, Россия
  
date: 30 ноября 2024

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
---

# Цель

## Цель

- Получить навыки настройки пакетного фильтра в Linux.

# Выполнение лабораторной работы

##  Просмотр текущей зоны и доступных зон

![Просмотр текущей зоны и доступных зон](image/1.PNG)

##  Добавление службы с конфигурацией Runtime

![Добавление службы с конфигурацией Runtime](image/5.PNG)

## Добавление службы с конфигурацией Permanent

![Добавление службы с конфигурацией Permanent](image/8.PNG)

## Добавление службы с конфигурацией Permanent

![Перезагрузка firewalld и просмотр информации](image/9.PNG)

## Работа через графический интерфейс

![Графический интерфейс](image/11.PNG)

# Ответы на контрольные вопросы

## 1. Какая служба должна быть запущена перед началом работы с менеджером конфигурации брандмауэра firewall-config?

Нужно запустить службу firewalld, это можно сделать командой systemctl start firewalld.

## 2. Какая команда позволяет добавить UDP-порт 2355 в конфигурацию брандмауэра в зоне по умолчанию?

Команда firewall-cmd --add-port=2355/udp --permanent.

## 3. Какая команда позволяет показать всю конфигурацию брандмауэра во всех зонах?

Команда firewall-cmd --list-all-zones.

## 4. Какая команда позволяет удалить службу vnc-server из текущей конфигурации брандмауэра?

Команда firewall-cmd --remove-service=vnc-server --permanent.

## 5. Какая команда firewall-cmd позволяет активировать новую конфигурацию, добавленную опцией --permanent?

Команда firewall-cmd --reload.

## 6. Какой параметр firewall-cmd позволяет проверить, что новая конфигурация была добавлена в текущую зону и теперь активна?

Команда firewall-cmd --list-all.

## 7. Какая команда позволяет добавить интерфейс eno1 в зону public?

Команда firewall-cmd --zone=public --add-interface=eno1 --permanent.

## 8. Если добавить новый интерфейс в конфигурацию брандмауэра, пока не указана зона, в какую зону он будет добавлен?

Он будет добавлен в зону по умолчанию.

# Вывод

## Я получил навыки настройки пакетного фильтра в Linux.
	
