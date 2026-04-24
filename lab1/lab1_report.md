University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: Cloud platforms as the basis of technology entrepreneurship\
Year: 2025/2026\
Group: U4125\
Author: Barvinskaya Mariya Borisovna \
Lab: Lab1\
Date of create: 24.04.2026\
Date of finished:\

# Обзор Google Cloud и исследование основных сервисов
- Создала service account с ролью Storage Admin:
<img width="1475" height="731" alt="image" src="https://github.com/user-attachments/assets/3132430b-fea3-445c-bc32-296eb44a6d39" />

- Создала минимальный compute engine (виртуальную машину) с Machine type e2-micro в режиме spot:
<img width="1149" height="407" alt="image" src="https://github.com/user-attachments/assets/9e4d0efd-fc31-442d-914e-7a06c4c3913b" />

- Нашла бакет
<img width="1107" height="136" alt="image" src="https://github.com/user-attachments/assets/457571d3-09dd-4ee5-8171-64efebd079d3" />

- Скопирывала все файлы в локальную папку на VM:
<img width="1113" height="181" alt="image" src="https://github.com/user-attachments/assets/835d01f2-d8a9-4081-8383-7ae8d2aadf8a" />

-  Используя команду ls -lah отобразила, что эти файлы хранятся у меня на VM:
<img width="656" height="152" alt="image" src="https://github.com/user-attachments/assets/50bc519d-3b0c-4533-a7d8-04ace994ee37" />

- Поменяла права доступа для своего service account с Storage Admin на Compute Viewer, попробовала повторить пункт с копированием данных
<img width="571" height="377" alt="image" src="https://github.com/user-attachments/assets/509dd3b8-1ce3-4c8e-9a95-bbd673d870b8" />

- 
