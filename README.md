# новый новый интернет


<details>
  <summary>осторожно спойлеры к кремниевой долине</summary>
  <p>как вы помните(ну, если смотрели, конечно) ребята пытались созать новый интернет, но он оказался слишком крутым, да настолько, что научился решать NP задачу за полиномиальное время (ну они же туда пркирепили нейросеть, чему вы удивлятесь????)</p>
</details>

<details>
  <summary>более скучный текст, но без спойлеров </summary>
  <p> в этом семестре вам надо будет написать несколкьо программ, эмулирующих реальный интернет и принципы его работы </p>
</details>

## lab 0 (wireshark)

  ![image](https://github.com/user-attachments/assets/dffb848e-74b8-47c7-84fb-1fb6d54fe27d)


  1) установите wireshark
  2) посмотрите каиие интерфейсы вам доступны, поймите, что такое интерфейс и чем они отличаются
  3) начните захват трафика на активном сетевом интерфейсе
  4) Откройте веб-браузер и перейдите на любой HTTP-сайт (не HTTPS, чтобы трафик был незашифрованным). Например, [http://example.com](http://xcal1.vodafone.co.uk/)
  5) Примените фильтр http в Wireshark, чтобы отобразить только HTTP-запросы и ответы.
  6) Изучите содержимое пакетов


## lab 1 (маршрут построен)

![image](https://github.com/user-attachments/assets/8361564a-221e-4fa6-a052-5ec501d26d15)

теперь, когда вы знаете, что есть какие-то там протоколы и что-то там куда-то отправляется, было бы неплохо заняться этой отправкой 

1) овтетьте на вопросы
  - зачем нужен маршрутизатор
  - чем маршрутизатор отличвется от коммутатора, на каком уровне модели OSI они работают
  - может ли работать интернте или передача сообщений между компьюетарми без маршрутизатора
  - что такое mac и ip адреса
2) вам необходимо написать две программы
  - программа клиентский компьюетр: надо захардкодить mac и ip адрес, программа должна уметь пинговать другие ноды в сети
  - программа маргшрутизатор: принимает все запросы и маршрутизирует
3) условия для программ:
  - все ошибки должны обрабатываться
  - код стайл должен быть
  - система должна легко маштабироватьяс, то есть продолжать работать при добавлении новых нод или сохранять работоспособность при отключении старых (имеются в виду ноды клиенты)
  - маршрутизатор должен уметь обрабатывать ненсколкьо запросов одновременно
  - предполагается, что ip адрес маршрутизатора вы знаете, остальных нод нет, маршрутизатор не знает ни чей ip адрес (имеется в виду ip адрес не реальный, а тот, который вы захардкодили) 
4) посмотрите, что будет, если задать двум нодам одинаковые ip адреса, mac адреса  

## lab 2 (динамическая адресация)

![image](https://github.com/user-attachments/assets/8c09eee8-f2d3-4526-925d-bb97fef85b31)


как вы могли заметить на примере прошлой лабы, добавлять новые ноды тяжело и неудобно, а представьте, если ваш маршрутизатор стоял бы в каком-нибудь кафе, в таком случае выдвать ip вручную уже невозможно,
надо как-то автмоатизировать этот процесс

1) овтетьте на вопросы
- зачем нужен DHCP сервер
- что будет, если в сети будет несколкьо DHCP серверов
  
2) напишите свой DHCP сервер, уделите отделньое внимание тому, чтобы двум узлам не выдали одинаковые адреса
   - изначально вы не знаете адрес DHCP сервера, вам нужно как-то его обнаружить
3) модифицируйте прошлую своб программу, чтобы вы могли получать адреса автоматичсеки 

## lab 3 (днс)

![image](https://github.com/user-attachments/assets/58d26f55-3339-4f44-8a74-d279a2e7d9d1)


в реальной жизни нкито не пользуется ip  адресами, а пишут домейные имена, добавьте такой функционал
 1) напишите свой днс сервер  
 2) пусть теперь клиентские ноды будут хостами, на каждой из них должна быть уникальная html страничка, нода должна обратиться к днс, чтобы зарегистрировать там свой "сайт"
 3) с любой ноды надо уметь получать данные с любой другой ноды, обращаясь по домейному имени  
 4) поудмайте, как новому клиенту, при прсиоединении к сети, узнать про днс сервер
     
## lab 4 (цензура)

![image](https://github.com/user-attachments/assets/61e9fae3-0f3a-45b0-8c96-d28297672f84)

теперь у вас уже есть мини версия интернета, но кажется вы что-то забыли, в вашей сети нет никакого котроля за оптравляемой инфомрацией, что противоречит примерно всем законодательсвтам прмиерно всех стран! Ну в общем вы поняли, надо кое-что добавить

1) должны сохранятся данные о всех операциях в интернете, кто и кому какие данные отправил
2) все сообщения начинающиеся со слов SPAM, DDOS а также bittorrent протокол должны блокироваться
3) придумайте способ обойти эти ограничения) 
   
## lab 5 (кластер)


