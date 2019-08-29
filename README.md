### Netflix OSS 

##### Used: Eureka Server, Config Server, Config Client, Zuul Api Gateway, Feign Client, RestTemplate, WebClient, Hystrix, Ribbon, Security (JWT), Spring WebFlux + MongoDB + Docker

_____

### Introduction

Мое знакомство со стеком началось больше полугода назад, и я нашел в нем определенные классные фичи, которые работают из коробки и которые, как мне кажется, достаточно интересные.
Я начал писать статьи в блоге и частично переводить документацию на русский язык, т.к. на русском довольно простой и понятной документации я не нашел, когда изучал данный материал.

В ходу статьи буду стараться давать ссылки на свои статьи. 
Надеюсь кто-то найдет из этого что-нибудь полезное.

В этом небольшом примере рассмотрим все из вышеуказанных топиков.

Я понимаю, что далеко до совершенства, но цель данного примера показать стандартные возможности Spring Cloud (Netflix OSS).

Если вы нашли какие-либо неточности или видите, что можно что-то улучшить, предложите свои изменения и я с радостью добавлю их. Давайте сделаем это вместе :)

____

### Cloud Computing
    
Облачные вычисления — это предоставление вычислительных служб (серверов, хранилища, баз данных, сетей, программного обеспечения, аналитики и т.д.) посредством интернета. 
Такие службы ускоряют внедрение каких-либо инноваций, повышают гибкость ресурсов и обеспечивают экономию благодаря высокой масштабируемости. 
Пользователь обычно платит только за облачные службы, которые он использет.
    
`Какие проблемы это решает ?`  
- Затраты

Облачные вычисления позволяют избежать капитальных затрат на приобретение оборудования и программного обеспечения, настройку и эксплуатацию.

- Скорость

Большинство облачных вычислительных служб предоставляются в режиме самообслуживания и по запросу.

- Глобальный масштаб

Преимущества служб облачных вычислений включают возможность эластичного масштабирования. 

- Производительность

Для локальных центров обработки данных обычно требуются много стоек и серверов, а также настройка оборудования. Облачные вычисления позволяют избежать многих из этих задач.
Самые большие облачные вычислительные службы работают в мировой сети безопасных центров обработки данных, которые регулярно обновляются до самого последнего поколения быстрого и эффективного вычислительного оборудования. 

- Надежность

Облачные вычисления делают резервное копирование данных, аварийное восстановление и непрерывность бизнес-процессов 

- Безопасность

Многие поставщики облачных служб предлагают широкий набор политик, технологий и средств контроля, которые в целом повышают уровень безопасности, помогая защитить данные, приложения и инфраструктуру от потенциальных угроз.
    
_____

### Зачем Spring Cloud если есть Kubernetes ?

Если вам нужны некоторые из ваших микросервисов на другом языке, то `Kubernetes` может это сделать, если не бояться потратить деньги на инвестиции в ваш технический стек, чтобы иметь более широкую и менее зависимую систему.

Если вам нужна быстрая разработка, хорошо интегрированная со стеком Spring без большого участия DevOps - то здесь не обойтись без `Spring Cloud`.


`Spring Cloud` имеет богатый набор хорошо интегрированных библиотек Java для решения всех проблем во время выполнений. 
В результате у самих микросервисов есть библиотеки для различных задач: 

- для обнаружения клиентов
- для балансировки нагрузки
- для обновления конфигурации
- для отслеживания показателей и т.д. 

`Kubernetes` предназначен не только для платформы Java, и решает проблемы распределенных вычислений в общем для всех языков. 
Он предоставляет услуги по управлению конфигурацией, обнаружению сервисов, балансировке нагрузки, трассировке, метрикам, запланированным заданиям и т.д. 

Некоторые библиотеки, такие как `Hystrix`, `Spring Boot`, одинаково полезны для обеих сред. Есть области, где обе платформы являются `взаимодополняющими` и могут быть объединены вместе для создания более мощного решения (такие примеры - `KubeFlix` и `Spring Cloud Kubernetes` например).

##### Spring Cloud Kubernetes:

    https://github.com/spring-cloud/spring-cloud-kubernetes
    http://www.ofbizian.com/2016/12/spring-cloud-compared-kubernetes.html

Он нужен чтобы облегчить интеграцию приложений Spring Cloud и Spring Boot, работающих в Kubernetes.

##### KubeFlix:

Kubernetes integration with Netflix

    https://blog.fabric8.io/kubeflix-kubernetes-integration-with-netflix-69f76d27ef91

____

### Netflix

##### Что такое Netflix ?

Немного биографии.

`Netflix` - это американская развлекательная компания, предоставляющая услуги видео онлайн (online Video streaming) и видео по запросу (Video on demand), основана в 1997 году, штаб-квартира находится в Лос Гатос, Калифорния. Изначально она являлась компанией по дистрибуции  DVD, модель продажи былла отправка  DVD по почте покупателям (DVD Emailing).

В 2006 году `Amazon` объявила о своем большом проекте и совсем не связано с индустрией их бизнеса, это "облачные вычисления" (Cloud computing). 

Сервис, который позже был назван как Amazon S3 (Amazon Simple Storage Service) позволяет пользователям сохранять свои данные в облачных серверах и иметь доступ всегда и везде.

`Netflix` понял что Amazon является нужным для них партнером. Вместо того, чтобы инвестировать много денег в сервера, можно использовать инфраструктуру у Amazon. Так и началось их сотрудничество.

На данный момент Netflix является самой большоей компанией в мире предоставляющей сервис онлайн фильмов и видео по запросу (video on demand).

Почти все ресурсы  Netflix развернуты на  Amazon Web Service (AWS). 

Ниже приведено изображение архитектуры их системы в качестве примера:

![alt text](http://mike.blogs.com/.a/6a00d83451c1bb69e2014e8948cca8970d-pi)

____

### Eureka Server

`Eureka Server` — это приложение, которое содержит информацию обо всех клиентских сервисных приложениях. 
Каждый микросервис регистрируется на сервере Eureka, и Eureka знает все клиентские приложения, работающие на каждом порту и IP-адресе. 
Eureka Server также известен как Discovery Server.

Его аналоги:
- Consul
- Zookeeper
- Cloud Foundry

Если простыми словами, то — это сервер имен или реестр сервисов. Обязанность — давать имена каждому микросервису.
Регистрирует микросервисы и отдает их ip другим микросервисам.

Таким образом, каждый сервис регистрируется в Eureka и отправляет эхо-запрос серверу Eureka, чтобы сообщить, что он активен.

Для этого сервис должен быть помечен как `@EnableEurekaClient`, а сервер `@EnableEurekaServer`.

При указании аннотаций `@EnableDiscoveryClient` тоже отработает, т.к. Eureka является Discovery сервисом, но вот в случае если использовать наоборот - юбой другой Dicovery сервис и использовать аннотацию `@EnableEurekaClient`, так уже не получится.

Eureka Client сбрасывает все HTTP-соединения, которые простаивали более 30 секунд, которые он создал для связи с сервером.

Клиент взаимодействует с сервером следующим образом:

1) Eureka Client регистрирует информацию о запущенном экземпляре на сервере Eureka.

2) Каждые 30 секунд Eureka Client отсылает запрос на сервер и информирует сервер о том, что он (экземпляр) еще жив.
Если сервер не видел обновления в течение 90 секунд, он удаляет экземпляр из своего реестра.

3) Eureka Client получает информацию реестра от сервера и кэширует ее у себя локально. 
Эта информация обновляется периодически (каждые 30 секунд), получая обновления между последним апдейтом и текущим. 
Клиент автоматически обрабатывает дублирующую информацию.

4) Получив обновления, клиент сверяет информацию с сервером, сравнивая количество экземпляров, возвращаемых сервером, и если информация по какой-либо причине не совпадает, вся информация реестра извлекается снова.
Клиент получает информацию в сжатом формате JSON, используя клиент jersey apache.

5) При завершении работы клиент отправляет запрос отмены на сервер. 
Таким образом экземпляр удаляется из реестра экземпляров сервера.
Eureka использует протокол, который требует, чтобы клиенты выполняли явное действие отмены регистрации.

Клиенты, которые использовали 3 неудачные попытки синхронизации с сервером с интервалом в 30 секунд будут удалены автоматически.

##### Взаимодействие серверов между собой:

Серверы Eureka взаимодействуют друг с другом, используя тот же механизм, который используется между клиентом и сервером.

Когда сервер запускается, он пытается получить всю информацию реестра экземпляра от соседнего узла. 

Если при получении информации от узла возникает проблема, сервер проверяет все равноправные узлы.

В случае проблем сервер пытается защитить уже имеющуюся у него информацию.

Более подробную информацию про Eureka вы можете прочитать в моей статье.
Надеюсь она будет полезна.

    https://medium.com/@kirill.sereda/spring-cloud-netflix-eureka-%D0%BF%D0%BE-%D1%80%D1%83%D1%81%D1%81%D0%BA%D0%B8-5b7829481717

Подсказки для настроек в файлах `application.property, application.yml`:

    https://cloud.spring.io/spring-cloud-static/Dalston.SR5/multi/multi__appendix_compendium_of_configuration_properties.html

Минимальные настройки eureka server - это порт и имя, а также `@EnableEurekaServer` над основным классом. Этого будет достаточно.

В нашем примере мы указали следующие настройки в файле `application.yml`

    spring:
      application:
        name: eureka-server
    
    server:
      port: ${PORT:8761}
    
    eureka:
      client:
        register-with-eureka: false  
        fetch-registry: false        
        instance-info-replication-interval-seconds: 10   
      server:
        eviction-interval-timer-in-ms: 50000
        wait-time-in-ms-when-sync-empty: 5

Наш сервер работает на порту 8761 с именем eureka-server.

Более детальное описание других настроек можно увидеть в коде на github.

Ссылка на Eureka Server:

    https://github.com/ksereda/Gallery-Service/tree/master/eureka-server
    
Некоторые настройки в `application.yml` закомментированы. Не обращайте на них внимание, к ним вернемся чуть позже.
    
Основной класс:

    @SpringBootApplication
    @EnableEurekaServer
    public class EurekaServerApplication {
    
    	public static void main(String[] args) {
    		SpringApplication.run(EurekaServerApplication.class, args);
    	}
    
    }
    
Запустите приложение и перейдите в браузере

    http://localhost:8761
    
Вы увидите дашборд для управления.

![alt text](https://www.baeldung.com/wp-content/uploads/2016/08/Screenshot_20160819_073151.png)

___

### Eureka Client

Для того, чтобы сервис стал клиентом Eureka, ему необходимо над основным классом указать `@EnableEurekaClient`

    @SpringBootApplication
    @EnableEurekaClient
    public class GalleryServiceApplication {
    
        public static void main(String[] args) {
            SpringApplication.run(GalleryServiceApplication.class, args);
        }
    
    }

В нашем примере все остальные сервисы будут по совместительству клиентами Eureka, не важно, каку функцию они выполняют.

___

### Gallery-Service

Рассмотрим `gallery-service`.

Он представляет обычный CRUD.

Мы будем использовать базу MongoDB, Spring WebFlux для реактивности и Lombok.

У нас есть Bucket модель с темами для изучения 

    @Data
    @Builder
    @AllArgsConstructor
    @Document(collection = "buckets")
    public class Bucket {
    
        @Id
        private String id;
    
        @NotBlank
        @Size(max = 10)
        private String title;
    
        private String description;
        private int personalNumber;
        private String imageLink;
    
    }
    
У нас есть контроллер `BucketController` , который обрабатывает запросы через реактивный репозиторий

    @Repository
    public interface BucketRepository extends ReactiveMongoRepository<Bucket, String> {
    }

Все достаточно просто.

Файл настроек также прост

    spring:
      application:
        name: gallery-service
      data:
        mongodb:
          uri: mongodb://localhost:27017/gallerydb
    
    server:
      port: 8081
    
    eureka:
      client:
        serviceUrl:
          defaultZone: ${EUREKA_URI:http://localhost:8761/eureka}
      instance:
        preferIpAddress: true

Используем MongoDB в докере на порту 27017 с именем базы gallerydb

Запустите Eureka Server вначале, а затем запустите наш сервис и перейдите на

    http://localhost:8081/
    
чтобы получить информацию что наш сервис работает.

Если вы перейдете в Eureka

    http://localhost:8761
    
Вы увидите что Eureka увидела наш сервис (имя и на каком порту он работает).
Сервер и клиент обменялись эхо запросами и поддерживают связь.

Также при старте gallery-service в консоли вы можете увидеть строки

    2019-08-29 15:53:41.923  INFO [gallery-service,,,] 1333 --- [  restartedMain] com.netflix.discovery.DiscoveryClient    : Getting all instance registry info from the eureka server
    2019-08-29 15:53:42.389  INFO [gallery-service,,,] 1333 --- [  restartedMain] com.netflix.discovery.DiscoveryClient    : The response status is 200
    
    2019-08-29 15:53:42.410  INFO [gallery-service,,,] 1333 --- [  restartedMain] o.s.c.n.e.s.EurekaServiceRegistry        : Registering application gallery-service with eureka with status UP
    
что означает, что сервис зарегистрировался в Eureka и получил подтверждение.

Непосредственно в консоли самой Eureka можно увидеть следующее

    2019-08-29 15:53:42.484  INFO 1053 --- [nio-8761-exec-1] c.n.e.registry.AbstractInstanceRegistry  : Registered instance GALLERY-SERVICE/192.168.97.121:gallery-service:8081 with status UP (replication=false)
    2019-08-29 15:53:43.056  INFO 1053 --- [nio-8761-exec-3] c.n.e.registry.AbstractInstanceRegistry  : Registered instance GALLERY-SERVICE/192.168.97.121:gallery-service:8081 with status UP (replication=true)
    
Eureka успешно зарегистрировала gallery-service.

Вы также можете запустить gallery-service не запуская перед ним Eureka, тогда вы увидите что сервис поднялся, но не смог зарегистрироваться в Eureka и получите сообщение об ошибке

    2019-08-29 15:58:42.529  WARN [gallery-service,,,] 1333 --- [freshExecutor-0] c.n.d.s.t.d.RetryableEurekaHttpClient    : Request execution failed with message: java.net.ConnectException: В соединении отказано (Connection refused)
    2019-08-29 15:58:42.529 ERROR [gallery-service,,,] 1333 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : DiscoveryClient_GALLERY-SERVICE/192.168.97.121:gallery-service:8081 - was unable to refresh its cache! status = Cannot execute request on any known server
    
    com.netflix.discovery.shared.transport.TransportException: Cannot execute request on any known server
    
Но вы сможете работать с ним.

Каждые 30 секунд сервис будет слать эхо запрос на Eureka и ждать что она ответит ему взаимностью.

Ссылка на gallery-service

    https://github.com/ksereda/Gallery-Service/tree/master/gallery-service
    
Некоторые настройки в `application.yml` закомментированы. Не обращайте на них внимание, к ним вернемся чуть позже.

В основном классе я указал

    	@Bean
    	CommandLineRunner run(BucketRepository bucketRepository) {
    		return args -> {
    			bucketRepository.deleteAll()
    					.thenMany(Flux.just(
    							new Bucket("1", "Java", "OOP", 280, "http://infopulse-univer.com.ua/images/trenings/java.png"),
    							new Bucket("2", "Java", "Steram API", 437, "https://www.hdwallpaperslife.com/wp-content/uploads/2018/09/JAVA14-480x270.png"),
    							new Bucket("3", "Java", "Collections", 14, "https://i.ytimg.com/vi/oOOESCvGGcI/hqdefault.jpg"),
    							new Bucket("4", ".NET", "Basic", 1213, "https://upload.wikimedia.org/wikipedia/commons/0/0e/Microsoft_.NET_logo.png"),
    							new Bucket("5", "C++", "Basic", 870, "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSmgIz9Ug-MVzBQJMcgXedOXTqHWGmbSu5pPDivz8hrfo_GE0HZEA"),
    							new Bucket("6", "JavaScript", "Angular 8", 155, "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTg41zepuyHbew8bIsTYeKWJ9RYOnnV922lNa85-fQTVrKDG19K2w")
    					)
    							.flatMap(bucketRepository::save))
    					.thenMany(bucketRepository.findAll())
    					.subscribe(System.out::println);
    
    		};
    	}

чтобы при старте приложения атвоматически создались данные, которые отобразятся в нашей MongoDB (чтобы не создавать вручную).

Как настроить MongoDB я опишу ниже.

Перейдите в браузере на 

    http://localhost:8081/getAll
    
чтобы получить все данные из базы.

Аналогично /create, /update, /delete

- если вы перейдете на

    
    http://localhost:8081/stream/buckets
    
вы получите все данне из базы стримом.

Здесь во всю используется прелесть реактивной системы с 
    
    MediaType.TEXT_EVENT_STREAM_VALUE

- перейдите на

    
    http://localhost:8081/stream/buckets/default

И будете получать каждую секунду новое деволтное значение

- перейдите на

    
    http://localhost:8081/stream/buckets/delay
    
При помощи Flux мы можем получить все обьекты из базы с интервалом в 2 секунды каждый. 
Здесь мы сэмулировали ситуацию, которая позволяет получить данные по мере их поступления. 
Это одна из основных идей реактивного программирования.

Мы подписываемся на поток и ждем данные. Spring сам уведомит нас о поступлении данных.

Основная концепция реактивного программирования базируется на неблокирующем вводе/выводе.

Напрмиер при старте приложения в нашей базе находится 4 записи а не 6. без использовании реактивности мы бы получили 4 записи. Потом кто-либо в этот промежуток времени добавил еще 2 записи и когда мы сделали второй запрос, мы бы получили 6 записей.

С использованием потоков `Mono/Flux` мы сэмулировали такую ситуацию и за один запрос сможем получить все данные с небольшим интервалом.

____






