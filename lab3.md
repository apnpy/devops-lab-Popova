## Лабораторная работа №3 "Мониторинг с Prometheus и Grafana"

University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)

Year: 2025/2026

Group: U4125

Author: Popova Alina Romanovna

Lab: Lab3

Date of create: 14.03.2026

Date of finished: 16.03.2026

## Цель
Научиться настраивать локальную систему мониторинга, собирать метрики с помощью Prometheus и создавать дашборды в Grafana для визуализации данных.

## Настройка мониторинга с Prometheus и Grafana

1. Создала папку prometheus для конфигурации
2. Создать файл prometheus/prometheus.yml со следующим содержимым: global: scrape_interval: 15s
<img width="894" height="501" alt="image" src="https://github.com/user-attachments/assets/10bc9cd4-8952-46ff-a3d7-6c74beeaa2f8" />
<img width="464" height="199" alt="image" src="https://github.com/user-attachments/assets/a63a5529-f64f-4e0b-b571-019651dd6fd5" />

Prometheus будет забирать метрики каждые 15 секунд, забирать метрики будет из двух серисов: Prometheus и Node Exporter

Алгоритм будет следующий: Node Exporter → собирает метрики системы ->
Prometheus → забирает метрики каждые 15 сек ->
Grafana → строит графики

### Запуск Node Exporter

1. Запустила контейнер Node Exporter для сбора системных метрик через терминал
Докер не нашел образ Node Exporter на локальном компьютере, поэтому скачал его.
После этого докер запустил контейнер

<img width="574" height="353" alt="image" src="https://github.com/user-attachments/assets/2d574654-c68f-45c3-b422-c0c9c8ad0192" />

2. Проверила работу контейнера
В отчет приходит большое количество метрик - контейнер работает.
<img width="893" height="454" alt="image" src="https://github.com/user-attachments/assets/a18be253-2421-4010-a48c-c135cae5470a" />

### Запуск Prometheus

1. Создала Том для данных prometheus
<img width="607" height="47" alt="image" src="https://github.com/user-attachments/assets/76478ada-f9d5-4a56-9c85-4a5229d876f1" />

2. Создала общую сеть для того чтобы prometheus и grafana могли вместе работать
<img width="614" height="48" alt="image" src="https://github.com/user-attachments/assets/7a3eabb6-3e94-438e-ba00-8e9361cd4b3a" />

3. Запустила контейнер Prometheus
<img width="915" height="351" alt="image" src="https://github.com/user-attachments/assets/1d864b93-5068-4f19-8c44-fd4fa8e33471" />
4. Перешла в браузере по ссылке http://localhost:9090 - страница не открывается. 
<img width="1440" height="778" alt="image" src="https://github.com/user-attachments/assets/8b74ca3c-d711-4531-82d6-99c20e7d9f41" />

4. Занялась анализом причины не работающей страницы
<img width="1182" height="74" alt="image" src="https://github.com/user-attachments/assets/5a54bc4d-2ac7-4d52-9cc0-825b1a2e151d" />
Командой docker ps проверила запущен ли контейнер - контейнер падает с ошибкой и докер пытается его перезапустить.

5. Посмотрела логи 
<img width="1185" height="379" alt="image" src="https://github.com/user-attachments/assets/54681014-8023-4f45-a7f7-4e0dabae6d70" />

Ошибка в файле prometheus.yml

6. Внесла изменения в содержимое файла
Было: <img width="410" height="192" alt="image" src="https://github.com/user-attachments/assets/f9caf877-39f5-47d5-a64a-d3c6b7160825" />

Стало: <img width="375" height="203" alt="image" src="https://github.com/user-attachments/assets/53fbd263-fe30-4366-9ad9-9643b7149b47" />

7. Проверим запущен ли контейнер теперь
<img width="1090" height="72" alt="image" src="https://github.com/user-attachments/assets/23409539-a72c-435e-b18f-d2fb36ad373a" />

Страница также открывается - проблема устранена
<img width="1090" height="72" alt="image" src="https://github.com/user-attachments/assets/4b297b55-2ca3-4c8a-ac8b-c1a56f7c1cb6" />

### Запуск Grafana

1. Создала том для хранения данных графана
<img width="568" height="42" alt="image" src="https://github.com/user-attachments/assets/874405a0-16a5-4aff-889a-317a21dfaf6f" />
2. Запустила контейнер Grafana
<img width="600" height="350" alt="image" src="https://github.com/user-attachments/assets/258f1a21-7603-4cda-ad7d-946666759d1b" />
3. Проверила графану в браузере - открывается успешно.
Также изменила пароль
<img width="1440" height="855" alt="image" src="https://github.com/user-attachments/assets/0fcb2427-8de8-4f7e-b5fe-1578fb4c6a71" />


### Настройка Grafana

1. Добавила источник данных - prometheus
<img width="1438" height="816" alt="image" src="https://github.com/user-attachments/assets/bbadd038-af8e-43c6-bb73-40dfe836e2ab" />
2. Настройила дашборд, добавила метрику node_cpu_seconds_total
<img width="1440" height="857" alt="image" src="https://github.com/user-attachments/assets/755d60d3-59b5-4166-918c-62460adb3caf" />


### Тестирование системы

1. Проверила все контейнеры
<img width="1141" height="97" alt="image" src="https://github.com/user-attachments/assets/898b3fea-690c-4c1e-841c-0d7a1d46ae7c" />
Кнтейнеры работают, но почему-то метрики не собираются:
<img width="1440" height="777" alt="image" src="https://github.com/user-attachments/assets/38d58731-2f60-4d18-b19b-095a3492bd1e" />

2. Анализирую причину отсутствия метрик
<img width="677" height="65" alt="image" src="https://github.com/user-attachments/assets/d7a75dc9-d9cc-4da8-be6f-b891d6410b04" />
Проверила к какой сети подключены контейнеры - контейнеры в разных docker сетях

3. Подключила node-exporter к сети monitoring
<img width="667" height="79" alt="image" src="https://github.com/user-attachments/assets/7efa16c0-852c-4f81-bcfa-e03059a9d167" />

4. Теперь prometheus может собирать метрики
<img width="1440" height="571" alt="image" src="https://github.com/user-attachments/assets/fc51f07d-5c8d-4f35-ab54-fec6e13c77e1" />

5. Grafana начала строить график
<img width="1440" height="863" alt="image" src="https://github.com/user-attachments/assets/fb6fd172-6768-4093-a41d-c41b35e1aaf9" />

6. Дашборд в графане
<img width="1440" height="780" alt="image" src="https://github.com/user-attachments/assets/c9dd2746-995f-47a9-a2c4-92470d13036b" />

## Итог
Я научилась настраивать локальную систему мониторинга, собирать метрики с помощью Prometheus и создавать дашборды в Grafana для визуализации данных.
