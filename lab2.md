<img width="1440" height="433" alt="image" src="https://github.com/user-attachments/assets/46653deb-d0d0-44f4-a256-e68e8666a608" />## CI/CD для Docker приложения

University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)

Year: 2025/2026

Group: U4125

Author: Popova Alina Romanovna

Lab: Lab2

Date of create: 13.03.2026

Date of finished: 

1. Создала новый репозиторий - devops_lab_Popova_cicd.
2. В репозиторий добавила файлы - app.py, requirements.txt, Dockerfile.
<img width="1437" height="773" alt="image" src="https://github.com/user-attachments/assets/b56a7d77-c16d-469e-9278-877d35ccfbfc" />
3. Создала новый репозиторий в DockerHub для образа
<img width="1437" height="780" alt="image" src="https://github.com/user-attachments/assets/e823231a-bc39-427a-ac15-b16dd7cc07e7" />
4. Создала файл
<img width="1440" height="779" alt="image" src="https://github.com/user-attachments/assets/33613df8-e9d1-4ca6-8b3b-a03c1060ed6c" />

### Настройка секретов
1. Перешла к настройке секретов:
<img width="1440" height="779" alt="image" src="https://github.com/user-attachments/assets/6b251738-28ba-43fe-82a1-ba9f603deb97"
<img width="1439" height="772" alt="image" src="https://github.com/user-attachments/assets/162fdab4-5baf-4b8a-a360-49b9801fee80" />

## Тестирование пайплайна
3. Cоздала файл test.txt и закоммитила его
<img width="1440" height="487" alt="image" src="https://github.com/user-attachments/assets/784f0f47-4d34-4ac6-a3f6-c87d0360e200" />
4. Перешла в actions для проверки выполнения пайплайна - упало в ошибку
<img width="1440" height="588" alt="image" src="https://github.com/user-attachments/assets/ce432fef-e3fd-4611-8315-a47b23a5e745" />

Ошибка: Annotations
1 error and 1 warning
build
buildx failed with: ERROR: failed to build: invalid tag "<***>/devops_lab_Popova_cicd": invalid reference format

Ошибка связана с форматированием тэга

5. Обновила название докер образа
<img width="1440" height="752" alt="image" src="https://github.com/user-attachments/assets/297efa6f-815e-45f3-ad6a-d21f244c3c34" />

6. Все равно свалилось в ошибку
<img width="1440" height="754" alt="image" src="https://github.com/user-attachments/assets/442aa553-d233-42da-ae2d-b8a58ded2f1f" />

7. Изменила написание названия на нижний регистр
<img width="1440" height="755" alt="image" src="https://github.com/user-attachments/assets/ad255e7c-6251-4891-8a5f-bc3f8da213da" />

8. Выполнила новый коммит
<img width="1440" height="433" alt="image" src="https://github.com/user-attachments/assets/4f163899-edbe-400a-90de-ba89f9081e65" />

9. Пайплайн выполнен успешно
<img width="1440" height="755" alt="image" src="https://github.com/user-attachments/assets/4117595e-b8df-498f-b012-86476fb440fb" />

10. Образ появился в DockerHub
<img width="1440" height="776" alt="image" src="https://github.com/user-attachments/assets/ae19c2cd-d849-4122-8df0-b44255dabddc" />

## Итог

В ходе выполнения лабораторной работы я научилась настройке CI/CD, настройке секретов в GitHub, а также смогла выполнить автоматическую сборку и публикацию Docker образа в Docker Hub.



