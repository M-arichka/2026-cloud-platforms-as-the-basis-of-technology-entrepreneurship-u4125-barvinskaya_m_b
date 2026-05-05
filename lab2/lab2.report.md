University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: Cloud platforms as the basis of technology entrepreneurship\
Year: 2025/2026\
Group: U4125\
Author: Barvinskaya Mariya Borisovna \
Lab: Lab2\
Date of create: 05.05.2026\
Date of finished:
# "Исследование Cloud Run"
## 1. В консоли Google Cloud создаю новый сервис Cloud Run на основе стандартного образа us-docker.pkg.dev/cloudrun/container/hello
<img width="1743" height="740" alt="создаю сервис" src="https://github.com/user-attachments/assets/aa667b2f-ef54-4aa9-a931-95c2d900f9d4" />

## 2. Разворачиваю сервис в Cloud Run - после перехода по предоставленной ссылке: https://barvinskaya-hello-lab-2-307056602443.europe-west1.run.app/. Отображается сообщение "It's running!", что подтверждает корректную работу контейнера и доступность сервиса:
<img width="1864" height="741" alt="развернула сервис" src="https://github.com/user-attachments/assets/40e72e4a-cd19-4d84-83cc-a7d378cc465d" />
<img width="1002" height="808" alt="открыла сайт" src="https://github.com/user-attachments/assets/d4086cba-ad7d-4837-a4c3-df5e401980e6" />

## 3. В разделе метрик проанализирую основные показатели работы сервиса: отображается количество входящих запросов (Requests), задержка обработки запросов (Latency), а также использование ресурсов (CPU и память). Наблюдается небольшое количество запросов и низкая нагрузка на ресурсы, поскольку сервис использовался в тестовом режиме:
<img width="1882" height="740" alt="Метрики" src="https://github.com/user-attachments/assets/52cbef54-1b59-404e-83d8-672d8270e208" />

## 4. В разделе логов отображаются записи всех обращений к сервису.
<img width="1660" height="549" alt="логи" src="https://github.com/user-attachments/assets/bc081434-e3e1-4191-b23f-24ed9271af95" />

## 5. Через Edit & deploy new revision меняю порт контейнера с 8080 на 8090:
<img width="793" height="561" alt="image" src="https://github.com/user-attachments/assets/072d6fbd-f36e-4d97-9b1f-c3170b42023d" />

Cloud Run является прокси между интернетом и контейнером — он принимает весь входящий трафик и сам перенаправляет его в контейнер. При смене порта в настройках Cloud Run делает единственное действие: передаёт новое значение внутрь контейнера через переменную окружения PORT=8090 и начинает форвардить туда запросы.\

Образ hello не использует хардкод порта — при запуске он читает PORT и слушает именно его. Поэтому сервис продолжил работать без ошибок независимо от того, какое значение выставлено в настройках.\

Сломалось бы это только в том случае, если бы приложение игнорировало PORT и всегда слушало фиксированный порт в коде — тогда Cloud Run стучался бы на 8090, а контейнер не отвечал.\
Переход по URL сервиса  https://barvinskaya-hello-lab-2-307056602443.europe-west1.run.app/ подтвердил успешную работу: отобразилась стандартная страница "It's running!" с информацией о созданной ревизии и проекте.\
<img width="753" height="765" alt="image" src="https://github.com/user-attachments/assets/4a8ea780-2887-453b-a453-95a6ece0e32f" /> \
Логи новой ревизии (с портом 8090) не отличаются от логов исходной — контейнер запустился штатно, так как Cloud Run корректно передал новое значение через PORT. Это подтверждает, что изменение порта в настройках сервиса не нарушает работу образа hello.
## 6. Через Manage traffic был настраеваю сплит трафика между двумя ревизиями:
<img width="1658" height="498" alt="image" src="https://github.com/user-attachments/assets/c7e753a0-5f6c-4aa5-8061-afee66253033" />
## 7. Проверяю метрики и логи сервиса: все работеат в штатном режиме
<img width="1115" height="655" alt="image" src="https://github.com/user-attachments/assets/d7a7a24f-d7c9-4889-a325-9a74afed8ae9" />
<img width="1100" height="622" alt="image" src="https://github.com/user-attachments/assets/fd9023dd-8897-4c4b-976d-816db51d664f" />\

Вывод: Cloud Run - удобный механизм деплоя контейнеров с автоматическим управление, обеспечивает стабильную работу даже при изменении конфигурации.
В конце завершаю проект и удаляю сервис
