# СЕТИ

## Требования к программам
1) Все возможные ошибки должны обрабатываться корректно.
2) Должен быть стиль кода


## lab 0 (wireshark)

  ![image](https://github.com/user-attachments/assets/dffb848e-74b8-47c7-84fb-1fb6d54fe27d)


  1) Установите wireshark
  2) Изучите доступные сетевые интерфейсы
      - Запустите Wireshark и ознакомьтесь со списком доступных сетевых интерфейсов
      - Разберитесь, что такое сетевой интерфейс, и чем они могут отличаться друг от друга (например, Wi-Fi, Ethernet, виртуальные интерфейсы и т.д.).
      - Определите, какой интерфейс в данный момент активен (используется для передачи данных)
  3) Запустите захват сетевого трафика
  4) Сгенерируйте HTTP-трафик
      - Откройте веб-браузер и перейдите на любой сайт, использующий протокол HTTP (не HTTPS, чтобы трафик был незашифрованным). Например, http://xcal1.vodafone.co.uk/.
  5) Примените фильтр для отображения HTTP-трафика
  6) Изучите содержимое пакетов
      - Выберите один из HTTP-запросов и изучите его структуру. Обратите внимание на такие поля, как: IP-адреса источника и назначения, Порт источника и назначения, Заголовки HTTP (например, метод запроса, путь, версия протокола).
      - Аналогично изучите HTTP-ответ, обращая внимание на код состояния (например, 200 OK) и другие заголовки.


## lab 1 (маршрут построен)

![image](https://github.com/user-attachments/assets/8361564a-221e-4fa6-a052-5ec501d26d15)

теперь, когда вы знаете, что есть какие-то там протоколы и что-то там куда-то отправляется, было бы неплохо заняться этой отправкой 

1) Ответьте на следующие вопросы:
    - Зачем нужен маршрутизатор в сети?
    - Чем маршрутизатор отличается от коммутатора? На каком уровне модели OSI они работают?
    - Может ли интернет или передача сообщений между компьютерами работать без маршрутизатора? Обоснуйте ответ.
    - Что такое MAC-адрес и IP-адрес? В чём их отличие и для чего они используются?
2) Вам необходимо разработать две программы, моделирующие работу сети:
    -  Программа "Клиентский компьютер"
        - Задайте MAC-адрес и IP-адрес для каждого клиента
        - Программа должна уметь отправлять ping-запросы другим узлам в сети.
    -  Программа "Маршрутизатор"
        - Маршрутизатор должен принимать все запросы от клиентов и корректно маршрутизировать их до нужного узла.
        - Маршрутизатор должен уметь обрабатывать несколько запросов одновременно
        - Маршрутизатор не знает IP-адреса клиентов заранее — они определяются динамически в процессе работы
    - Система должна оставаться работоспособной при добавлении новых узлов или отключении существующих
    - Проверьте, что произойдёт, если двум узлам в сети назначить одинаковые IP-адреса.
    - Проверьте, что произойдёт, если двум узлам в сети назначить одинаковые MAC-адреса.

## lab 2 (динамическая адресация)

![image](https://github.com/user-attachments/assets/8c09eee8-f2d3-4526-925d-bb97fef85b31)

1) Ответьте на следующие вопросы:  
    - Зачем нужен DHCP-сервер в сети?
    - Что произойдёт, если в одной сети будет несколько DHCP-серверов?
    - Как клиент обнаруживает DHCP-сервер в сети?
  
2)  Разработка DHCP-сервера
    = Реализуйте DHCP-сервер, который будет автоматически назначать IP-адреса клиентам в сети.
    - Реализуйте механизм, который предотвращает выдачу одинаковых IP-адресов разным узлам.
    - Учтите, что изначально клиенты не знают IP-адрес DHCP-сервера — он должен быть обнаружен автоматически.
3)  Модификация клиентской программы
    - Модифицируйте программу "Клиентский компьютер" из предыдущей лабораторной работы так, чтобы она могла автоматически получать IP-адрес от DHCP-сервера.
4) Интеграция с маршрутизатором
    - Убедитесь, что маршрутизатор корректно работает с клиентами, которые получают IP-адреса автоматически.
    - Проверьте, что система остаётся работоспособной при добавлении новых узлов и отключении существующих.
    

## lab 3 (днс)

![image](https://github.com/user-attachments/assets/7f219568-1c62-47ad-857b-0e9b37cdb41c)

1) Ответьте на следующие вопросы:
    - Что такое DNS и зачем он нужен?
    - Как DNS-сервер связывает доменные имена с IP-адресами?
    - Какие типы DNS-записей существуют?
    - Как новый клиент в сети может обнаружить DNS-сервер?
2) Разработка DNS-сервера
    - Реализуйте DNS-сервер, который будет хранить записи о доменных именах и соответствующих им IP-адресах.
    - DNS-сервер должен поддерживать регистрацию новых доменных имён от клиентов (узлов).
    - Реализуйте механизм разрешения доменных имён в IP-адреса (DNS-запросы и ответы).
3) Модификация клиентских узлов
   - Каждый клиентский узел должен быть хостом с уникальной HTML-страницей
4) Взаимодействие между узлами
    - С любого узла в сети должна быть возможность получить HTML-страницу с другого узла, обратившись к нему по доменному имени.
5) Обнаружение DNS-сервера
    - Реализуйте механизм, с помощью которого новый клиент может автоматически обнаружить DNS-сервер в сети.
     
## lab 4 (цензура)

![image](https://github.com/user-attachments/assets/61e9fae3-0f3a-45b0-8c96-d28297672f84)

1) Ответьте на следующие вопросы:
    - Зачем нужен контроль и фильтрация сетевого трафика?
    - Какие методы используются для блокировки нежелательного трафика.
    - Какие данные необходимо сохранять для мониторинга сетевой активности?
2) Реализация системы мониторинга
    - Добавьте в систему(подумайте, где это лучше сделать и почему) функционал для логирования всех операций в сети.
    - Сохраняйте следующую информацию
        -  Кто отправил данные.
        -  Кому отправлены данные.
        -  Тип данных (например, HTTP, DNS, запрещённые протоколы).
        -  Время отправки и размер данных.
3) Реализация системы фильтрации
    - Блокируйте сообщения, начинающиеся с ключевых слов SPAM или DDOS.
    - Блокируйте трафик, использующий протокол BitTorrent (вернее его эмуляцию в вашей системе).
    - При блокировке трафика сохраняйте информацию о попытке отправки запрещённых данных.
4) Реализация обхода ограничений
    - Разработайте механизм, позволяющий обойти ограничения
    - Протестируйте, как система фильтрации реагирует на попытки обхода ограничений.
    

## lab 5 (nat)

![image](https://github.com/user-attachments/assets/607a7965-5136-42ed-9da8-11e81a82f3ca)

1) Ответьте на следующие вопросы:
    - Что такое NAT и зачем он нужен?
    - Какие типы NAT существуют?
    - Как NAT помогает экономить IP-адреса и повышать безопасность сети?
    - Как маршрутизатор определяет, принадлежит ли IP-адрес локальной сети или внешней?
2) Добавление поддержки NAT на маршрутизаторе
    - Добавьте поддержку определения, принадлежит ли IP-адрес локальной сети или внешней.
    - Локальные (приватные) IP-адреса должны заменяться на публичный IP-адрес маршрутизатора при отправке пакетов во внешнюю сеть.
    - Публичный IP-адрес должен заменяться на соответствующий локальный IP-адрес при получении ответов из внешней сети.
3) Создание внешнего узла
    - Добавьте в сеть один узел, который будет находиться "вне" локальной сети
    - Задайте ему IP статически
4) Обеспечение взаимодействия узлов
    - Убедитесь, что узлы из локальной сети могут обращаться к внешнему узлу через маршрутизатор с использованием NAT.
    - Проверьте, что маршрутизатор корректно транслирует адреса и возвращает ответы на запросы из локальной сети.
   


## lab 6 (bpf)
![image](https://github.com/user-attachments/assets/91bbf314-7fd4-486e-8f45-75ebb7c8d943)

1) Ответьте на следующие вопросы:
    - что такое BPF и зачем он нужен.
    - в чем отличие BPF и eBPF.
    - Какие преимущества дает использование eBPF для фильтрации трафика по сравнению с традиционными методами.
2) Создайте eBPF-программу, которая будет фильтровать входящие TCP-пакеты на основе IP-адреса источника и порта
    - Убедитесь, что у вас установлен Linux с поддержкой eBPF
    - Установите необходимые инструменты: clang, llvm, bpftool, libbpf
    - Установите утилиту tcpdump для анализа сетевого трафика.
    - Запустите tcpdump для мониторинга сетевого трафика.
    - Попробуйте отправить TCP-пакет с IP-адреса 192.168.1.1 и порта 8080. Убедитесь, что пакет отбрасывается.
    - Проверьте, что пакеты с других IP-адресов и портов проходят через фильтр.
    - Чтобы отправить TCP-пакет с конкретного IP-адреса и порта, можно использовать инструменты для генерации сетевого трафика, такие как scapy (Python-библиотека) или hping3. 


## lab 7 (кластер)

![image](https://github.com/user-attachments/assets/d5de62c4-5090-4ad7-a858-b29f8b34fbf4)

Вместо ВМ можно использовать контейнеры
https://vk.com/topic-64649419_36089444


## Система оценивания курса

Каждая лабораторная работа оценивается определённым количеством баллов:

- lab 0 - 1
- lab 1 - 2
- lab 2 - 2
- lab 3 - 2
- lab 4 - 2
- lab 5 - 2
- lab 6 - 3
- lab 7 - 3

К каждой лабораторной работе прилагается теоретический материал, который необходимо изучить и сдать. Для получения положительной оценки нужно:
1) Сдать всю теорию.
2) Набрать определённое количество баллов за лабораторные работы:
   - 9–11 баллов — оценка 3
   - 12–14 баллов — оценка 4
   - 15–17 баллов — оценка 5

Оценку можно повысить одним из двух способов
1) На экзамене можно взять билет и повысить оценку на 1 балл.
2) За активную работу на лекциях можно получить дополнительный балл.
