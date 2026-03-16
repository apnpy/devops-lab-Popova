## Курсовая работа "Создание персонального сайта с использованием MkDocs"

University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)

Year: 2025/2026

Group: U4125

Author: Popova Alina Romanovna

Lab: Coursework

Date of create: 16.03.2026

Date of finished: 16.03.2026

## Цель
Создать собственный персональный сайт или сайт проекта, используя технологию MkDocs и язык разметки Markdown.

##
Ссылка на мой сайт: https://apnpy.github.io/personal-site/

### Этап 1: Подготовка и установка

1. Установка Python
Ранее Python уже был установлен, проверила его версию и обновила
<img width="601" height="285" alt="image" src="https://github.com/user-attachments/assets/7896d440-9adb-462e-a434-bcccc94eec33" />

2. Установила MkDocs
<img width="599" height="363" alt="image" src="https://github.com/user-attachments/assets/fb1cbb71-a804-4f52-ab9d-2402eabd172e" />

3. Установила тему Material
Тема необходима для улучшения внешнего вида сайта и его функциональности.
<img width="601" height="401" alt="image" src="https://github.com/user-attachments/assets/b1820f9a-b813-4b36-9fa9-edc9a9b61750" />

4. Проверила установленную версию - установлена version 1.6.1
<img width="589" height="26" alt="image" src="https://github.com/user-attachments/assets/0294aa22-4758-46bf-af43-1fc25e4c2d19" />

### Создание нового проекта

1. Создала папку папку для проекта my-personal-site и перешла в нее
<img width="496" height="47" alt="image" src="https://github.com/user-attachments/assets/ae5413af-06ad-4732-9bb0-4dcf146f000d" />

2. Изучила структуру файлов в папке
MkDocs создал базовую структуру сайта
Сейчас в папке 2 файла: mkdocs.yml и index.md
<img width="603" height="343" alt="image" src="https://github.com/user-attachments/assets/8865c55b-0d1f-4fac-9bc4-8907cfca3666" />

mkdocs.yml - главный конфигурационный файл сайта, сейчас там зафиксирована только следующая информация : site_name: My Docs

Файл index.md - Это главная страница сайта.
В файле сейчас содержится полезная информация по проекту с ссылками для ознакомления. 

## Этап 2: Настройка конфигурации

1. Перешла к файлу mkdocs.yml и настроила базовые параметры:
Так как данный сайт будет обо мне - добавила следующую информацию:

site_name: Alina Popova
site_description: Personal website and portfolio
site_author: Alina Popova
site_url: https://alinapopova1603.com

theme:
  name: material
  features:
    - navigation.tabs
    - navigation.sections
    - navigation.top
    - search.highlight
    - search.share

2. Дополнительно добавила навигацию на сайте через раздел nav

nav:
  - Главная: index.md
  - О себе: about.md
  - Проекты: projects.md
  - Контакты: contacts.md
<img width="598" height="483" alt="image" src="https://github.com/user-attachments/assets/0a0a1934-f8f5-4330-9b93-36780f060135" />

## Этап 3: Создание контента

### Главная страница (index.md)

1. Для того, чтобы видеть сразу вносимые изменения я запустила сайт командой - mkdocs serve
<img width="575" height="239" alt="image" src="https://github.com/user-attachments/assets/727fb3d0-b56b-4979-ba9c-82fabaa7a9a2" />

2. В файл index.md я внесла изменения, добавив различные элементы markdown:

- Заголовки разных уровней
- Списки (маркированные и нумерованные)
- Ссылки
- Изображения
- Цитаты
- Таблицу
- Разные выделения текста
<img width="596" height="408" alt="image" src="https://github.com/user-attachments/assets/b8df18ce-a37e-4cf0-b82f-65135e068653" />

### Страница "О себе" (about.md)

1. Наполнила страницу "Обо мне" данными.
<img width="597" height="418" alt="image" src="https://github.com/user-attachments/assets/48f14685-04c2-4e4f-9a65-5a91712d11d1" />

### Страница "Проекты" (projects.md)

1. Для того, чтобы карточки проектов отображались в красивом формате в файл mkdocs.yml добавила расширение:
markdown_extensions:
  - admonition

2. Сформировала карточки по проектам
<img width="588" height="630" alt="image" src="https://github.com/user-attachments/assets/33d47242-14b0-4691-8cf3-65768020e03d" />

### Страница "Контакты" (contacts.md)

1. Создала страницу с контактами, использовала эмодзи и ссылки 
<img width="581" height="330" alt="image" src="https://github.com/user-attachments/assets/3ed175ac-30d9-40af-b143-15ef81fe89aa" />


## Этап 4: Дополнительные возможности

1. Создала папку images и использовала фото на сайте
<img width="598" height="252" alt="image" src="https://github.com/user-attachments/assets/21add95d-0403-42a9-8340-2f672b4f8d7a" />

2.Дополнительно создала страницы "Достижения" и "Резюме" и наполнила их данными.
<img width="650" height="336" alt="image" src="https://github.com/user-attachments/assets/a56dc247-9b9e-4a8c-8187-3005f8bb02a0" />
<img width="537" height="782" alt="image" src="https://github.com/user-attachments/assets/a35c8b4e-1566-4ea4-8c43-5ecad79a72d4" />

3. Настроила цвета темы в файле mkdocs.yml
4. Добавила Лого
5. Настроила футер

<img width="511" height="543" alt="image" src="https://github.com/user-attachments/assets/af38f1d1-4def-4fe6-92e3-0e041254f75b" />
## Публикация сайта

1. Создала новый репозиторий - personal-site
<img width="1440" height="769" alt="image" src="https://github.com/user-attachments/assets/a2804c2f-667c-4f2c-84f1-7ed52418e479" />
2. Связала локальный проект с удаленным репозиторием
git remote add origin https://github.com/apnpy/personal-site.git
git push -u origin main

На данном этапе было много проблем - скрины не сохраниись. Были сложности с подключение к проекту и авторизацией, после того как я создала токен и авторизовалась под ним проблемы ушла
3. Собрала и опубликовала образ
mkdocs gh-deploy

Теперь сай доступен по ссылке: https://apnpy.github.io/personal-site/

Итоговый сайт:
**Главная:**
<img width="1440" height="857" alt="image" src="https://github.com/user-attachments/assets/e28b5a94-c937-47b4-8624-c7eddfd14fcf" />
<img width="1439" height="858" alt="image" src="https://github.com/user-attachments/assets/97c577e2-a8ec-4bb7-96d8-0dc5d6eaefe4" />

**Обо мне:**
<img width="1438" height="856" alt="image" src="https://github.com/user-attachments/assets/38cc1fd9-4fa1-4f5b-983c-85915fe65826" />
<img width="1440" height="853" alt="image" src="https://github.com/user-attachments/assets/91a8ce17-bbbb-4fa9-b055-1f3e5004178c" />
<img width="1440" height="861" alt="image" src="https://github.com/user-attachments/assets/3615cc88-ad35-49ec-ba33-3d3118ec2f28" />

**Проекты:**
<img width="1440" height="858" alt="image" src="https://github.com/user-attachments/assets/52f96057-05a0-4e26-9666-9647a0ba9e1a" />
<img width="1440" height="841" alt="image" src="https://github.com/user-attachments/assets/a641a163-ae42-4d9c-a249-4412419768b5" />
<img width="1439" height="856" alt="image" src="https://github.com/user-attachments/assets/340caeaa-2600-492c-9e3f-757041da4ed1" />

**Контакты:**
<img width="1440" height="857" alt="image" src="https://github.com/user-attachments/assets/9a5e5415-4385-468a-9120-c37024706ce6" />

**Резюме:**
<img width="1440" height="852" alt="image" src="https://github.com/user-attachments/assets/ccdfd078-069c-4e7a-931e-734476f65f13" />
<img width="1440" height="853" alt="image" src="https://github.com/user-attachments/assets/531a746d-88b4-4a26-9bd9-970eb9aced7f" />
<img width="1440" height="854" alt="image" src="https://github.com/user-attachments/assets/ba8281a0-71a5-4531-a2b3-f843643fc088" />

**Достижения:**
<img width="1440" height="857" alt="image" src="https://github.com/user-attachments/assets/bc3407ba-a785-4c2f-866f-4b449aba1641" />

