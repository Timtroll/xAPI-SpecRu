# xAPI-SpecRu
## Расширенное распределенное обучение (ADL) Co-Laboratories
## Advanced Distributed Learning (ADL) Co-Laboratories
## (Вольный перевод от Timtroll https://github.com/adlnet/xAPI-Spec)

>#### Timtroll (вольный перевод спецификации)

>"Copyright 2013 Advanced Distributed Learning (ADL) Initiative, U.S. Department of Defense

>Licensed under the Apache License, Version 2.0 (the "License"). You may not use this file except 
>in compliance with the License. You may obtain a copy of the License at
>http://www.apache.org/licenses/LICENSE-2.0

> Если не предусмотрено действующим законодательством или согласования в письменной форме, программное обеспечение распространяется 
> "как есть" БЕЗ КАКИХ ЛИБО ГАРАНТИЙ И УСЛОВИЙ явных или подразумеваемых. Смотри Лицензию на родном языке которая регулирует права и
> ограничения по данной Лицензии.

> Данный документ составлен членами  xAPI Working Group (смотри список в [CONTRIBUTING.md](CONTRIBUTING.md#contributors))
> при поддержке Deputy Assistant Secretary of Defense (Readiness) Advanced Distributed Learning (ADL) Initiative. Все замечания 
> и отклики посылайте сюда helpdesk@adlnet.gov

## Содержание
*	Часть первая:	[Про xAPI](./xAPI-About.md#partone)
	*	1.0.	[Введение](./xAPI-About.md#introduction-partone) 
	*	2.0.	[Как использовать данный документ](./xAPI-About.md#readingguidelines)
		*	2.1.	[Обязано быть / Как есть / Возможно будет](./xAPI-About.md#def-must-should-may)
	 	*	2.2.	[Руководство для Interpreting Descriptive Text и Tables](./xAPI-About.md#interpret-text-table)
	*	3.0.	[Сериализация и JavaScript Object запись](./xAPI-About.md#json)
	*	4.0.	[Определения](./xAPI-About.md#definitions) 
	*	5.0.	[xAPI компоненты](./xAPI-About.md#xapi-components) 
	*	6.0.	[Расширения xAPI](./xAPI-About.md#extending-xapi) 
	*	7.0.	[Профили и Комьюнити на практике](./xAPI-About.md#COPs)
	*	[Приложения](./xAPI-About.md#append1)
		*	[Приложение A: регистрация изменений](./xAPI-About.md#Appendix1A)
		*	[Приложение B: cmi5 примеры](./xAPI-About.md#Appendix1B)
*	Часть вторая:	[Данные xAPI](./xAPI-Data.md#parttwo)
	*	1.0.	[Документация](./xAPI-Data.md#documents) 
	*	2.0.	[Формулировки](./xAPI-Data.md#statements)
		*	2.1.	[Общая цель](./xAPI-Data.md#statement-purpose)
	 	*	2.2.	[Требования к форматированию](./xAPI-Data.md#dataconstraints) 
	 		*	2.2.s1 [Подробности](./xAPI-Data.md#datadetail) 
	 		*	2.2.s2 [Требования](./xAPI-Data.md#datarequirements) 
		 	*	2.3.s3	[Требования к Learning Record Provider](./xAPI-Data.md#lrsarequirements)
	 	*	2.3.	[Директивы о жизненном цикле](./xAPI-Data.md#lifecycle) 
		 	*	2.3.1.	[Директивы неизменяемости](./xAPI-Data.md#statement-immutability-and-exceptions) 
		 	*	2.3.2.	[Аннулирование](./xAPI-Data.md#voided)
   		*	2.4.	[Директива свойствах](./xAPI-Data.md#statement-properties)
	        *	2.4.1.	[ID](./xAPI-Data.md#stmtid)
	        *	2.4.2.	[Actor](./xAPI-Data.md#actor)
	        *	2.4.3.	[Действия](./xAPI-Data.md#verb)
	        *	2.4.4.	[Object](./xAPI-Data.md#object)
	        *	2.4.5.	[Result](./xAPI-Data.md#result)
	        *	2.4.6.	[Context](./xAPI-Data.md#context)
	        *	2.4.7.	[Timestamp](./xAPI-Data.md#timestamp)
	        *	2.4.8.	[Stored](./xAPI-Data.md#stored)
	        *	2.4.9.	[Authority](./xAPI-Data.md#authority)
	        *	2.4.10.	[Version](./xAPI-Data.md#version)
	        *	2.4.11.	[Attachments](./xAPI-Data.md#attachments)
    	*	2.5.	[Исправления(Восстановления)](./xAPI-Data.md#retrieval) 
    	*	2.6.	[Подписи](./xAPI-Data.md#signature)
	*	3.0.	[Metadata](./xAPI-Data.md#metadata)
		*	3.1.	[IRI Requirements](./xAPI-Data.md#iri-requirements)
		*	3.2.	[Hosted Metadata](./xAPI-Data.md#miscmeta)
    *	4.0.	[Спациальные типы данных и правила](./xAPI-Data.md#special-data)
		*	4.1.	[Расширения](./xAPI-Data.md#miscext) 
		*	4.2.	[Карта языков (Language Maps)](./xAPI-Data.md#lang-maps)
		*	4.3.	[IRIs](./xAPI-Data.md#iris)
		*	4.4.	[UUIDs](./xAPI-Data.md#uuids)
		*	4.5.	[ISO 8601 Timestamps](./xAPI-Data.md#timestamps)
		*	4.6.	[ISO 8601 Durations](./xAPI-Data.md#durations)
	*	[Приложения](./xAPI-Data.md#append2)
		*	[Приложение A: Примеры директив](./xAPI-Data.md#Appendix2A)
		*	[Приложение B: Примеры директив различных типов](./xAPI-Data.md#Appendix2B)
		*	[Приложение C: Примеры определений активностей для типа "cmi.interaction"](./xAPI-Data.md#Appendix2C)  	
		*	[Приложение D: Примеры подписанных директив](./xAPI-Data.md#Appendix2D)
*	Часть третья:	[Обработка данных, Валидация и Безопасность](./xAPI-Communication.md#partthree)
	*	1.0.	[Запросы](./xAPI-Communication.md#requests)
		*	1.1.	[Реализация HEAD Request](./xAPI-Communication.md#httphead)
	 	*	1.2.	[Headers](./xAPI-Communication.md#headers) 
	 	*	1.3.	[Альтернативный синтаксис запроса](./xAPI-Communication.md#alt-request-syntax) 
	 	*	1.4.	[Encoding](./xAPI-Communication.md#encoding) 
	 	*	1.5.	[Content Types](./xAPI-Communication.md#content-types) 
	        *	1.5.1.	[Application/JSON](./xAPI-Communication.md#applicationjson) 
	        *	1.5.1.	[Multipart/Mixed](./xAPI-Communication.md#multipartmixed)
	*	2.0.	[Ресурсы](./xAPI-Communication.md#datatransfer) 
	 	*	2.1.	[Объявление Resource](./xAPI-Communication.md#stmtres) 
	 	*	2.2.	[Документы Resources](./xAPI-Communication.md#doctransfer) 
	 	*	2.3.	[Государственный Resource](./xAPI-Communication.md#stateres) 
	 	*	2.4.	[Агентский Resource](./xAPI-Communication.md#agentsres) 
	 	*	2.5.	[Активности Resource](./xAPI-Communication.md#activitiesres) 
	 	*	2.6.	[Профиль агента Resource](./xAPI-Communication.md#agentprofres) 
	 	*	2.7.	[Активности профиля Resource](./xAPI-Communication.md#actprofres) 
	 	*	2.8.	[Описание Resource](./xAPI-Communication.md#aboutresource) 
   	*	3.0.	[Валидация данных](./xAPI-Communication.md#validation)
    	*	3.1.	[Совпадения](./xAPI-Communication.md#concurrency)
    	*	3.2.	[Коды ошибок](./xAPI-Communication.md#errorcodes)
    	*	3.3     [Версионность](./xAPI-Communication.md#versioning)
    *	4.0.	[Аутентификация](./xAPI-Communication.md#authentication)
		*	4.1.	[OAuth 1.0 сценарии и методы](./xAPI-Communication.md#authdefs) 
		*	4.2.	[OAuth 1.0 объемы авторизации](./xAPI-Communication.md#oauthscope)
    *	5.0	[Безопасность](./xAPI-Communication.md#security)
	*	[Приложения](./xAPI-Communication.md#append3)
		*	[Приложение A: Преобразование отчетности в 1.0.0](./xAPI-Communication.md#Appendix3A)
		*	[Приложение B: Таблица всех ресурсов](./xAPI-Communication.md#Appendix3B)
		*	[Приложение C: Примеры кроссдоменныъ запросов](./xAPI-Communication.md#Appendix3C)


<a name="partthree" />
# Часть третья: Обработка данных, Валидация и Безопасность

Это третья часть c более детальной технической стороной xAPI, описывающия как Директивы передаются между Learning Record Provider и LRS. Ряд библиотек доступны для использования с целым рядом технологий (в том числе JavaScript), которые могут обрабатывать эту часть спецификации. Поэтому такое описание не может быть необходимым для Learning Record Providers.

<a name="requests"/>

## <a name="1.0">1.0</a> Запросы (Requests)

Отслеживание в xAPI осуществляется с помощью HTTP-запросов от Learning Record Provider (client) к LRS (server). Эта спецификация предлагает руководство в построении некоторых аспектов этой связи. Там, где нет прямых указаний, рекомендуется, чтобы эти реализаторы xAPI использовали существующие лучшие методы.

<a name="httphead"/>

### <a name="1.1">1.1</a> Реализация HEAD Request

###### <a name="1.1.s1"></a>Описание

Поведение LRS в ответ на PUT, POST, GET и DELETE запрос описана в [Ресурсы](#resources) ниже.
Все ресурсы, которые поддерживают GET также поддерживают HEAD.
LRS будет отвечать на запросы в HEAD, возвращая метаинформацию только используя заголовки HTTP, а не BODY.

###### <a name="1.1.s2"></a>Обоснование

Подключение клиентов к LRS, возможно потребует проверить, существует ли конкретная Директива, или попытается определить дату изменения документов, таких, как в State, Activity Profile или Agent Profile Resources. В частности, для больших документов, это является более эффективным, чтобы не получать весь документ только для получения его даты изменения.

###### <a name="1.1.s3"></a>Требования к LRS

* <a name="1.1.s3.b1"></a>LRS ДОЛЖЕН ответить на любой HTTP HEAD запрос, как если бы он отвечал на запрос HTTP GET, с такими ограничениями:
    * <a name="1.1.s3.b1.b1"></a>Тело сообщения ДОЛЖНО быть опущено.
    * <a name="1.1.s3.b1.b2"></a>Заголовок Content-Length, МОЖЕТ быть опущен, для экономии ресурсов LRS.

<a name="headers"/> 

### <a name="1.2">1.2</a> Headers

##### <a name="1.2.s1"></a>Header Parameters

Некоторые параметры Header, используемые xAPI в передаче данных - [Стандартные заголовки HTTP](http://en.wikipedia.org/wiki/List_of_HTTP_header_fields). Следующие заголовки запроса, как ожидается, будут использоватьсяLearning Record Providers в некоторых или всех типах запросов и ситуаций, описанных в данной спецификации:

* <a name="1.2.s1.b1"></a>Accept
* <a name="1.2.s1.b2"></a>Accept-Encoding
* <a name="1.2.s1.b3"></a>Accept-Language
* <a name="1.2.s1.b4"></a>Authorization
* <a name="1.2.s1.b5"></a>Content-Type
* <a name="1.2.s1.b6"></a>Content-Length
* <a name="1.2.s1.b7"></a>Content-Transfer-Encoding
* <a name="1.2.s1.b8"></a>If-Match
* <a name="1.2.s1.b9"></a>If-None-Match
* <a name="1.2.s1.b10"></a>X-Experience-API-Version 

Ожидается, что следующие заголовки будут использоваться LRS. Опять же, не все из них относятся к любому типу запроса и/или ситуации:

* <a name="1.2.s1.b11"></a>Content-Type
* <a name="1.2.s1.b12"></a>Content-Length
* <a name="1.2.s1.b13"></a>Last-Modified
* <a name="1.2.s1.b14"></a>ETag
* <a name="1.2.s1.b15"></a>Status
* <a name="1.2.s1.b16"></a>X-Experience-API-Version
* <a name="1.2.s1.b17"></a>X-Experience-API-Consistent-Through

Этот перечень не являюеся исчерпывающими. Смотри требования, представленные в данном документе для получения более подробной информации.

<a name="alt-request-syntax"/>

### <a name="1.3">1.3</a>Альтернативный синтаксис запроса


###### <a name="1.3.s1"></a>Описание

Одна из целей xAPI, чтобы позволить кросс-доменного отслеживание, и даже если XAPI стремится включить отслеживание из небраузерных приложений приложений, браузеры по-прежнему нуждаются в поддержке. Например, Internet Explorer 8 и 9 не в состоянии реализовать  Cross Origin Resource Sharing, а использует  свой собственный Cross Domain Request API, который не могут использовать все чAPI, как описано выше в связи с только поддержкой "GET" и "POST" и не позволяя устанавливать заголовки HTTP.

###### <a name="1.3.s2"></a>Подробности/Требования

Ниже описывается альтернативный синтаксис для использования в случаях, когда невозможно использовать обычный синтаксис для конкретных вызовов из-за ограничений, упомянутых выше. Этот альтернативный синтаксис может быть использован для получения Директив из-за ограничений по длине строки запроса GET.

Смотри примеры в [Приложение C: Cross Domain Request Example](#Appendix3C). 

###### <a name="1.3.s3"></a>Требования

__Method__:
* <a name="1.3.s3.b1"></a>Все xAPI запросы ДОЛЖНЫ быть POST. 
* <a name="1.3.s3.b2"></a>Предполагаемый метод xAPI ДОЛЖЕН быть включен в качестве значения "method" параметр строки запроса query.
* <a name="1.3.s3.b3"></a>Learning Record Provider НЕ ДОЛЖЕН включать в запрос любые другие параметры строки query.

Пример: http://example.com/xAPI/statements?method=PUT

__Content__:
* <a name="1.3.s3.b4"></a>Если вызов xAPI участвует передаче контента, Learning Record Provider ДОЛЖЕН закодировать URL, чтобы включить содержание в качестве параметра формы под названием "content".
* <a name="1.3.s3.b5"></a>LRS ДОЛЖЕН интерпретировать этот "content" в виде строки UTF-8. Передача/Хранение двоичных данных не поддерживается.

__Headers__:
* <a name="1.3.s3.b6"></a>Learning Record Provider МОЖЕТ включать в себя любые параметры заголовка, необходимые по данной спецификации, которые, как ожидается, появится в HTTP-заголовке в качестве параметров формы с одинаковыми именами. Это относится к следующим параметрам: Authorization, X-Experience-API-Version, Content-Type, Content-Length,
If-Match and If-None-Match.
Это не относится к параметру Content-Transfer-Encoding.
* <a name="1.3.s3.b7"></a>Параметры, перечисленные выше в качестве параметров заголовка LRS ДОЛЖЕН воспринимать как параметры формы.
* <a name="1.3.s3.b8"></a>Learning Record Provider ДОЛЖЕН содержать другие параметры заголовка, не только передаваемые в заголовке HTTP в обычном режиме.
* <a name="1.3.s3.b9"></a>РЕКОМЕНДУЕТСЯ чтобы Learning Record Provider включал в HEADER заголовок Content-Type и посылал запросы со значением 'application/x-www-form-urlencoded'.
* <a name="1.3.s3.b10"></a>РЕКОМЕНДУЕТСЯ использовать параметр Content-Type чтобы указывать тип содержимого содержания в параметре формы.
* <a name="1.3.s3.b11"></a>Learning Record провайдеру РЕКОМЕНДУЕТСЯ включать в заголовок Content-Length с указанием общей длинызапроса. 
* <a name="1.3.s3.b12"></a>В параметре формы Content-Length РЕКОМЕНДУЕТСЯ указать именно длину содержимого внутри
 формы и поэтому длина будет меньше, чем обычная длина указываемая в Content-Length.
 
__Query string parameters__:
* <a name="1.3.s3.b13"></a>Любые параметры строки запроса отличные от "method" ДОЛЖНЫ быть включены в качестве параметров формы с теми же названиями.
* <a name="1.3.s3.b14"></a>LRS ДОЛЖЕН рассматривать ВСЕ параметры заголовка отличные от "content" в качестве параметров строки запроса параметров формы.

__Attachments__: Следует отметить, что не представляется возможным отправлять бинарные вложения данных, используя текущий синтаксис. Смотри [Приложения](./xAPI-Data.md#attachments) 

* <a name="1.3.s3.b15"></a>LRS ДОЛЖНА подделжывать синтаксис описанный выше.

Иногда для Learning Record Provider есть требования поддержки приложений или браузеров, где код xAPI Client размещен на другом протоколе (HTTP или HTTPS) отличном от LRS. Прокси-сервер необходим, только ЕСЛИ вы хотите поддерживать HTTP для xAPI HTTPS запросы от IE 9 или ниже. Вы можете сделать HTTP к HTTPS (или HTTPS к HTTP!) без прокси-сервера, если вы используете современный браузер. Есть два простых решения: 1) установить прокси, который приведет протоколы к одной схеме или 2) разместить настороне сервера LRS посредника маршрутизации Директив к LRS.

Настоятельно рекомендуем рассмотреть все риски в области безопасности, прежде чем принимать решение об использовании реализаций на основе HTTP.

<a name="encoding"/> 

### <a name="1.4">1.4</a> Encoding

###### <a name="1.4.s1"></a>Требования

* <a name="1.4.s1.b1"></a>Все строки ДОЛЖНЫ быть в кодировке UTF-8. 

<a name="content-types"/> 
### <a name="1.5">1.5</a> Content Types

В этой спецификации запросы и ответы используют `application/json` content type. Исключениями из этого правила являются:

* <a name="1.5.b1"></a>Документы могут иметь любой content type. 
* <a name="1.5.b2"></a>Запросы Директив, которые включают в себя вложения используют `multipart/mixed` content type. 

<a name="applicationjson"/> 
#### <a name="1.5.1">1.5.1</a> Application/JSON

Запросы в этой спецификации обычно используют `application/json` content type. 

###### <a name="1.5.1.s1"></a>LRS Тебования
* <a name="1.5.1.s1.b1"></a>При получении запроса PUT или POST с документом типа `application/json` LRS ДОЛЖНА принять  запрос и обработать те из них, которые не содержат привязки к объектам.
* <a name="1.5.1.s1.b2"></a>При получении запроса PUT или POST с документом типа `application/json` LRS ДОЛЖНА принять и обработать те которые содержат только объекты вложения с Url файла.

<a name="multipartmixed"/> 
#### <a name="1.5.2">1.5.2</a> Multipart/Mixed

The `multipart/mixed` content type is used for requests that *could* include Attachments. This does not mean that all 
"multipart/mixed" requests necessarily do include Attachments.

##### <a name="1.5.2.s1"></a>Procedure For The Exchange Of Attachments

* <a name="1.5.2.s1.b1"></a>A Statement request including zero or more Attachments is construed as described below.

* <a name="1.5.2.s1.b2"></a>The Statement is sent using a Content-Type of `multipart/mixed`. Any Attachments are placed 
at the end of such transmissions.

* <a name="1.5.2.s1.b3"></a>The LRS decides whether to accept or reject the Statement based on the information in the first part.

* <a name="1.5.2.s1.b4"></a>If it accepts the request, it can match the raw data of an Attachment(s) with the 
Attachment header by comparing the SHA-2 of the raw data to the SHA-2 declared in the header. It MUST not do so any other way.

###### <a name="1.5.2.s2"></a>Requirements for Attachment Statement Batches

A request transmitting a Statement batch, Statement results, or single Statement that includes Attachments MUST satisfy one of the 
following criteria:

* <a name="1.5.2.s2.b1"></a>It MUST be of type `application/json` and include a fileUrl for every Attachment EXCEPT for Statement 
results when the "attachments" filter is `false`.
* <a name="1.5.2.s2.b2"></a>It MUST conform to the definition of "multipart/mixed" in [RFC 2046](https://www.ietf.org/rfc/rfc2046.txt) and:
    * <a name="1.5.2.s2.b2.b1"></a>The first part of the multipart document MUST contain the Statements themselves, 
    with type `application/json`.
    * <a name="1.5.2.s2.b2.b2"></a>Each additional part contains the raw data for an Attachment and forms a logical 
    part of the Statement. This capability will be available when issuing PUT or POST requests against the Statement Resource.
    * <a name="1.5.2.s2.b2.b3"></a>MUST include an X-Experience-API-Hash parameter in each part's header after the 
    first (Statements) part.
    * <a name="1.5.2.s2.b2.b4"></a>MUST include a Content-Transfer-Encoding parameter with a value of `binary` in each 
    part's header after the first (Statements) part.
    * <a name="1.5.2.s2.b2.b5"></a>SHOULD only include one copy of an Attachment's data when the same Attachment is used 
    in multiple Statements that are sent together.
    * <a name="1.5.2.s2.b2.b6"></a>SHOULD include a Content-Type parameter in each part's header. For the first part 
    (containing the Statement) this MUST be `application/json`.
   	* <a name="1.5.2.s2.b2.b7"></a>Where parameters have a corresponding property within the attachment Object 
   	(outlined in the table above), and both the parameter and property are specified for a given Attachment, 
	the value of these parameters and properties MUST match. 

###### <a name="1.5.2.s3"></a>LRS Requirements

* <a name="1.5.2.s3.b1"></a>An LRS MUST include Attachments in the Transmission Format described above
when requested by the Client (see [Statement Resource](#stmtres)).
* <a name="1.5.2.s3.b2"></a>An LRS MUST NOT pull Statements from another LRS without requesting Attachments.
* <a name="1.5.2.s3.b3"></a>An LRS MUST NOT push Statements into another LRS without including Attachment data
received, if any, for those Attachments.
* <a name="1.5.2.s3.b4"></a>When receiving a PUT or POST with a document type of `multipart/mixed`, an LRS MUST accept batches of 
Statements that contain Attachments in the Transmission Format described above.
* <a name="1.5.2.s3.b5"></a>When receiving a PUT or POST with a document type of `multipart/mixed`, an LRS MUST reject batches of 
Statements having Attachments that neither contain a fileUrl nor match a received Attachment part based on their hash.
* <a name="1.5.2.s3.b6"></a>When receiving a PUT or POST with a document type of `multipart/mixed`, an LRS SHOULD assume a 
Content-Transfer-Encoding of binary for Attachment parts.
* <a name="1.5.2.s3.b7"></a>An LRS MAY reject (batches of) Statements that are larger than the LRS is configured to allow.
* <a name="1.5.2.s3.b8"></a>When receiving a PUT or POST with a document type of `multipart/mixed`, an LRS SHOULD* accept batches 
of Statements which contain no Attachment Objects.
* <a name="1.5.2.s3.b9"></a>When receiving a PUT or POST with a document type of `multipart/mixed`, an LRS SHOULD* accept batches 
of Statements which contain only Attachment Objects with a populated fileUrl.

__Note:__ There is no requirement that Statement batches using the "mime/multipart" format contain Attachments.

###### <a name="1.5.2.s4"></a>Learning Record Provider Requirements

* <a name="1.5.2.s4.b1"></a>A Learning Record Provider MAY send Statements with Attachments as described above.
* <a name="1.5.2.s4.b2"></a>A Learning Record Provider MAY send multiple Statements where some or all have 
Attachments if using POST.
* <a name="1.5.2.s4.b3"></a>A Learning Record Provider MAY send batches of type `application/json` where every attachment
Object has a fileUrl, ignoring all requirements based on the "multipart/mixed" format.
* <a name="1.5.2.s4.b4"></a>A Learning Record Provider SHOULD use SHA-256, SHA-384, or SHA-512 to populate the "sha2" property.

###### <a name="1.5.2.s5"></a>File URL
The File URL is intended to provide a location from which the Attachment can be received.
There are, however, no requirements for the owner of the Attachment to make the 
Attachment data available at the location indefinitely or to make the Attachment publically
available without security restrictions. When determining Attachment hosting arrangements, 
those creating Statements using the "fileUrl" property are encouraged to consider the needs of end recipient(s) 
of the Statement, especially if the Attachment content is not included with the Statement.

* <a name="1.5.2.s5.b1"></a>The Attachment data SHOULD be retrievable at the URL indicated by the fileUrl.
* <a name="1.5.2.s5.b2"></a>The owner of the attachment MAY stop providing the attachment data at this IRL at any time. 
* <a name="1.5.2.s5.b3"></a>Security restrictions MAY be applied to those attempting to access the Attachment data at this IRL. 

The period of time an Attachment is made available for, and the security restrictions applied to
hosted attachments, are out of scope of this specification. 

###### <a name="1.5.2.s6"></a>Example

Below is an example of a very simple Statement with an Attachment. Please note the following:

* <a name="1.5.2.s6.b1"></a>The boundary in the sample was chosen to demonstrate valid character classes;
* <a name="1.5.2.s6.b2"></a>The selected boundary does not appear in any of the parts;
* <a name="1.5.2.s6.b3"></a>For readability the sample attachment is of type "text/plain". Even if it had been 
a binary type like "image/jpeg", no encoding would be done, the raw octets would be included;
* <a name="1.5.2.s6.b4"></a>Per RFC 2046, the boundary is `<CRLF>` followed by -- followed by the boundary string 
declared in the header.

__Note:__ Don't forget the ```<CRLF>```  when building or parsing these messages.

Headers:

``` 
Content-Type: multipart/mixed; boundary="abcABC0123'()+_,-./:=?"
X-Experience-API-Version:1.0.0
```
Content:
```

--abcABC0123'()+_,-./:=?
Content-Type:application/json

{
    "actor": {
        "mbox": "mailto:sample.agent@example.com",
        "name": "Sample Agent",
        "objectType": "Agent"
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/answered",
        "display": {
            "en-US": "answered"
        }
    },
    "object": {
        "id": "http://www.example.com/tincan/activities/multipart",
        "objectType": "Activity",
        "definition": {
            "name": {
                "en-US": "Multi Part Activity"
            },
            "description": {
                "en-US": "Multi Part Activity Description"
            }
        }
    },
    "attachments": [
        {
            "usageType": "http://example.com/attachment-usage/test",
            "display": { "en-US": "A test attachment" },
            "description": { "en-US": "A test attachment (description)" },
            "contentType": "text/plain; charset=ascii",
            "length": 27,
            "sha2": "495395e777cd98da653df9615d09c0fd6bb2f8d4788394cd53c56a3bfdcd848a"
        }
    ]
}
--abcABC0123'()+_,-./:=?
Content-Type:text/plain
Content-Transfer-Encoding:binary
X-Experience-API-Hash:495395e777cd98da653df9615d09c0fd6bb2f8d4788394cd53c56a3bfdcd848a

here is a simple attachment
--abcABC0123'()+_,-./:=?--
```

<a name="datatransfer"/> <a name="resources"/>
## <a name="2.0">2.0</a> Resources

The LRS is interacted with via RESTful HTTP methods to the resources outlined in this section.
The Statement Resource can be used by itself to track learning records. Other resources provide
additional functionality. 

An LRS will support all of the resources described in this section. It's also possible
for a tool which is not an LRS to choose to follow the LRS requirements of one or 
more of the resources and methods described in this section. For example a tool might
implement POST Statements for the purposes of receiving incoming Statements forwarded by an LRS.
Such a system is not considered to be an LRS or 'partial LRS'; it is simply not an LRS. 

__Note:__ In all of the example endpoints where xAPI resources are located given in the specification, `http://example.com/xAPI/` 
is the example base endpoint of the LRS. All other IRI syntax after this represents the particular resource used. 
A full list of the endpoints is included in [Appendix B: Table of All Resources](#Appendix3B).

###### <a name="2.0.s1"></a>Requirements

* <a name="2.0.s1.b1"></a>The LRS MUST support all of the resources described in this section. 
* <a name="2.0.s1.b2"></a>If the LRS implements OAuth 1.0, the LRS MUST also support all of the OAuth resources 
described in [OAuth Authorization Scope](#oauthscope).
* <a name="2.0.s1.b3"></a>The LRS MAY support additional resources not described in this specification. 
* <a name="2.0.s1.b4"></a>Past, current and future versions of this specification do not and will not define endpoints 
with path segments starting with `extensions/`. LRSs supporting additional resources not defined in this specification SHOULD 
define their endpoints with path segments starting with `extensions/`.

<a name="stmtres"/> 

#### <a name="2.1">2.1</a> Statement Resource

###### <a name="2.1.s1"></a>Description

The basic communication mechanism of the  xAPI.

<a name="stmtresput"/>

#### <a name="2.1.1">2.1.1</a> PUT Statements

###### <a name="2.1.1.s1"></a>Details

Example endpoint: `http://example.com/xAPI/statements`

Stores a single Statement with the given id. POST can also be used to store single Statements.

**Content:** The Statement object to be stored. 

**Returns:** `204 No Content`

<table>
	<tr><th>Parameter</th><th>Type</th><th>Default</th><th>Description</th><th>Required</th></tr>
	<tr id="2.1.1.s1.table1.row1"><td>statementId</td><td>String</td><td> 
	<td>Id of Statement to record</td></td><td>Required</td></tr>
</table>

###### <a name="2.1.1.s2"></a>LRS Requirements

* <a name="2.1.1.s2.b1"></a>The LRS MAY respond before Statements that have been stored are available for retrieval.

* <a name="2.1.1.s2.b2"></a>An LRS MUST NOT make any modifications to its state based on receiving a Statement
with a statementId that it already has a Statement for. Whether it responds with `409 Conflict` or `204 No Content`, 
it MUST NOT modify the Statement or any other Object.

* <a name="2.1.1.s2.b3"></a>If the LRS receives a Statement with an id it already has a Statement for, it SHOULD
verify the received Statement matches the existing one and SHOULD return `409 Conflict` if they
do not match. See [Statement comparison requirements](./xAPI-Data.md#statement-comparison-requirements).

* <a name="2.1.1.s2.b4"></a>If the LRS receives a batch of Statements containing two or more Statements with the same id, 
it SHOULD* reject the batch and return `400 Bad Request`.



###### <a name="2.1.1.s3"></a>Learning Record Provider Requirements

* <a name="2.1.1.s3.b1"></a>Learning Record Providers SHOULD POST Statements including the Statement "id" property 
instead of using PUT. 
* <a name="2.1.1.s3.b2"></a>When PUTing Statements, the "id" property of the Statement SHOULD be used. 
* <a name="2.1.1.s3.b3"></a>Where provided, the "id" property of the Statement MUST match the "statementId" parameter of the request. 

<a name="stmtrespost"/>

#### <a name="2.1.2">2.1.2</a> POST Statements

###### <a name="2.1.2.s1"></a>Details

Example endpoint: `http://example.com/xAPI/statements`

Stores a Statement, or a set of Statements.

**Content:** An array of Statements or a single Statement to be stored. 

**Returns:** `200 OK`, Array of Statement id(s) (UUID) in the same order as the corresponding stored Statements.

###### <a name="2.1.2.s2"></a>Requirements

* <a name="2.1.2.s2.b1"></a>The LRS MAY respond before Statements that have been stored are available for retrieval.
* <a name="2.1.2.s2.b2"></a>GET Statements MAY be called using POST and form parameters if necessary as query strings 
have limits. See [Alternate Request Syntax](#alt-request-syntax) for more details.
* <a name="2.1.2.s2.b3"></a>The LRS MUST differentiate a POST to add a Statement or to list Statements based on the 
parameters passed. See [Alternate Request Syntax](#alt-request-syntax) for more details.
* <a name="2.1.2.s2.b4"></a>An LRS MUST NOT make any modifications to its state based on receiving a Statement
with an id that it already has a Statement for. Whether it responds with `409 Conflict` or `204 No Content`, 
it MUST NOT modify the Statement or any other Object.
* <a name="2.1.2.s2.b5"></a>If the LRS receives a Statement with an id it already has a Statement for, it SHOULD
verify the received Statement matches the existing one and SHOULD return `409 Conflict` if they
do not match. See [Statement comparison requirements](./xAPI-Data.md#statement-comparison-requirements).
* <a name="2.1.2.s2.b6"></a>If the LRS receives a batch of Statements containing two or more Statements with the same id, 
it SHOULD* reject the batch and return `400 Bad Request`.

<a name="stmtresget"/>

#### <a name="2.1.3">2.1.3</a> GET Statements

###### <a name="2.1.3.s1"></a>Details

Example endpoint: `http://example.com/xAPI/statements`

This method is called to fetch a single Statement or multiple Statements. If the statementId or voidedStatementId parameter 
is specified a single Statement is returned.

Otherwise returns: A [StatementResult](./xAPI-Data.md#retrieval) Object, a list of Statements in reverse chronological order based 
on "stored" time, subject to permissions and maximum list length. If additional results are available, an IRL to 
retrieve them will be included in the StatementResult Object.

**Content:** None.

**Returns:** `200 OK`, Statement or [Statement Result](./xAPI-Data.md#retrieval)

<table>
	<tr><th>Parameter</th><th>Type</th><th>Default</th><th>Description</th><th>Required</th></tr>
	<tr id="2.1.3.s1.table1.row1">
		<td>statementId</td>
		<td>String</td>
		<td> </td>
		<td>Id of Statement to fetch</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row2">
		<td>voidedStatementId</td>
		<td>String</td>
		<td> </td>
		<td>Id of voided Statement to fetch. see <a href="./xAPI-Data.md#voided">Voided
		Statements</a></td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row3">
		<td>agent</td>
		<td>Agent or Identified Group Object (JSON)</td>
		<td> </td>
		<td>Filter, only return Statements for which the specified Agent or Group is 
		the Actor or Object of the Statement.
			<ul>
				<li> 
					Agents or Identified Groups are equal when the same 
					Inverse Functional Identifier is used in each Object compared and 
					those Inverse Functional Identifiers have equal values.
				</li><li>
					For the purposes of this filter, Groups that have members 
					which match the specified Agent	based on their Inverse Functional
					Identifier as described above are considered a match
				</li>
			</ul>
			<br><br>See <a href="./xAPI-Data.md#actor">agent/group</a> Object definition
			for details.
		</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row4">
		<td>verb</td>
		<td>Verb id (IRI)</td>
		<td> </td>
		<td>Filter, only return Statements matching the specified Verb id.</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row5">
		<td>activity</td>
		<td>Activity id (IRI)</td>
		<td> </td>
		<td>
			Filter, only return Statements for which the Object of the Statement is 
			an Activity with the specified id.
		</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row6">
		<td>registration</td>
		<td>UUID</td>
		<td> </td>
		<td>
			Filter, only return Statements matching the specified registration 
			id. Note that although frequently a unique registration will be used 
			for one Actor assigned to one Activity, this cannot be assumed. 
			If only Statements for a certain Actor or Activity are required, 
			those parameters also need to be specified.
		</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row7">
	<td>related_activities</td>
		<td>Boolean</td>
		<td>false</td>
		<td>
			Apply the Activity filter broadly. Include Statements for which the Object,
			any of the  context Activities, or any of those properties in a contained
			SubStatement match the Activity parameter, instead of that parameter's 
			normal behavior. Matching is defined in the same way it is for the 
			"activity" parameter.
		</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row8">
		<td>related_agents</td>
		<td>Boolean</td>
		<td>false</td>
		<td>
			Apply the Agent filter broadly. Include Statements for which 
			the Actor, Object, Authority, Instructor, Team,
			or any of these properties in a contained SubStatement match the Agent parameter,
			instead of that parameter's normal behavior. Matching is defined in the same way
			it is for the "agent" parameter.
		</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row9">
		<td>since</td>
		<td>Timestamp</td>
		<td> </td>
		<td>Only Statements stored since the specified Timestamp (exclusive) are returned.</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row10">
		<td>until</td>
		<td>Timestamp</td>
		<td> </td>
		<td>Only Statements stored at or before the specified Timestamp are returned.</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row11">
		<td>limit</td>
		<td>Nonnegative Integer</td>
		<td>0</td>
		<td>
			Maximum number of Statements to return. 0 indicates return the 
			maximum the server will allow.
		</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row12">
		<td>format</td>
		<td>String: (<code>ids</code>, <code>exact</code>, or <code>canonical</code>)</td>
		<td>exact</td>
		<td>If <code>ids</code>, only include minimum information necessary in Agent, Activity, Verb 
			and Group Objects to identify them. For Anonymous Groups this means including 
			the minimum information needed to identify each member. 
			<br/><br/>
			If <code>exact</code>, return Agent, Activity, Verb and Group Objects populated exactly as they 
			were when the Statement was received. An LRS requesting Statements for the purpose 
			of importing them would use a format of "exact" in order to maintain 
			<a href="./xAPI-Data.md#statement-immutability-and-exceptions">Statement Immutability</a>.
			<br/><br/>
			If <code>canonical</code>, return Activity Objects and Verbs populated with the canonical
			definition of the Activity Objects and Display of the Verbs as determined by the LRS, after
			applying the <a href="#queryLangFiltering">language filtering process defined below</a>,
			and return the original Agent and Group Objects as in "exact" mode.
		</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row13">
		<td>attachments</td><td>Boolean</td><td>false</td>
		<td>If <code>true</code>, the LRS uses the multipart response format and includes all attachments as 
		described previously.  If <code>false</code>, the LRS sends the prescribed response with Content-Type 
		application/json and does not send attachment data.</td>
		<td>Optional</td>
	</tr>
	<tr id="2.1.3.s1.table1.row14">
		<td>ascending</td>
		<td>Boolean</td>
		<td>false</td>
		<td>If <code>true</code>, return results in ascending order of stored time</td>
		<td>Optional</td>
	</tr>
</table>

__Note:__ The values of Boolean parameters are represented as `true` or `false` as in JSON.
###### <a name="2.1.3.s2"></a>Requirements

* <a name="2.1.3.s2.b1"></a>The LRS MUST reject with a `400 Bad Request` error any requests to this resource 
which contain both statementId and voidedStatementId parameters

* <a name="2.1.3.s2.b2"></a>The LRS MUST reject with an `400 Bad Request` error any requests to this resource which 
contain statementId or voidedStatementId parameters, and also contain any other parameter besides "attachments" or "format".

* <a name="2.1.3.s2.b3"></a>The LRS MAY apply additional query filter criteria based on permissions associated
with the credentials used. 

* <a name="2.1.3.s2.b4"></a>In the event that no Statements are found matching the query filter criteria, the LRS MUST still return 
`200 OK` and a [StatementResult](./xAPI-Data.md#retrieval) Object. In this case, the "statements" property will contain an empty array.

* <a name="2.1.3.s2.b5"></a>The LRS MUST include the header "X-Experience-API-Consistent-Through", in 
[ISO 8601 combined date and time](https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations) format, 
on all responses to Statements Resource requests, with a value of the timestamp for which all Statements that have or will have a 
"stored" property before that time are known with reasonable certainty to be available for retrieval. This time SHOULD take 
into account any temporary condition, such as excessive load, which might cause a delay in Statements becoming available 
for retrieval. It is expected that this will be a recent timestamp, even if there are no recently received Statements. 

* <a name="2.1.3.s2.b6"></a>If the "attachment" property of a GET Statement is used and is set to `true`, the LRS MUST 
use the multipart response format and include all Attachments as described in [Part Two](./xAPI-Data.md#attachments).

* <a name="2.1.3.s2.b7"></a>If the "attachment" property of a GET statement is used and is set to `false`, the LRS MUST NOT
include Attachment raw data and MUST report `application/json`.

* <a name="2.1.3.s2.b8"></a>The LRS SHOULD* include a "Last-Modified" header which matches the "stored" Timestamp 
of the Statement. 

<a name="queryStatementRef" />

###### <a name="2.1.3.s3"></a>Filter Conditions for StatementRefs

This section outlines rules by which Statements targeting other Statements can sometimes be considered to 
meet the filter conditions of a query even if they do not match the original query's filter parameters. 
These rules **do not** apply when retrieving a single Statement using "statementId" or "voidedStatementId" query 
parameters.

'Targeting Statements' means that one Statement (the targeting Statement) includes the Statement id of another
Statement (the targeted Statement) as a Statement Reference as the Object of the Statement. 

For filter parameters which are not time or sequence based (that is, other than "since", "until", or "limit"), 
Statements which target another Statement (by using a StatementRef as the Object of the Statement) will meet the 
filter condition if the targeted Statement meets the filter condition.

The time and sequence based parameters MUST still be applied to the Statement making the StatementRef in this manner. 
This rule applies recursively, so that "Statement a" is a match when a targets b which targets c and the filter 
conditions described above match for "Statement c".

For example, consider the Statement 'Ben passed explosives training', and a follow up
Statement: "Andrew confirmed <StatementRef to original Statement\>". The follow up
Statement will not mention 'Ben' or 'explosives training', but when fetching Statements
with an Actor filter of 'Ben' or an Activity filter of 'explosives training', both
Statements match and will be returned so long as they fall into the time or sequence
being fetched.

__Note:__ StatementRefs used as a value of the "Statement" property within Context do not affect how
Statements are filtered.

<a name="queryLangFiltering" />

###### <a name="2.1.3.s4"></a>Language Filtering Requirements for Canonical Format Statements

* <a name="2.1.3.s4.b1"></a>Activity Objects contain Language Map Objects within their "name", "description" and various 
interaction components. The LRS MUST return only one language in each of these maps. 

* <a name="2.1.3.s4.b2"></a>The LRS MAY maintain canonical versions of language maps against any IRI identifying an object containing
language maps. This includes the language map stored in the Verb's "display" property and potentially some 
language maps used within extensions. 

* <a name="2.1.3.s4.b3"></a>If the LRS maintains a canonical version of a language map, it SHOULD* return this canonical language map
 when canonical format is used to retrieve Statements. 

* <a name="2.1.3.s4.b4"></a>The LRS SHOULD* return only one language within each language map for which it returns a canonical map. 

* <a name="2.1.3.s4.b5"></a>In order to choose the most relevant language, the LRS MUST apply the "Accept-Language" header as 
described in [RFC 2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html) 
(HTTP 1.1), except that this logic MUST be applied to each language map individually to select 
which language entry to include, rather than to the resource (list of Statements) as a whole.

<a name="voidedStatements" />

##### <a name="2.1.4">2.1.4</a> Voided Statements
[Part Two](./xAPI-Data.md#voided) describes the process by which Statements can be voided. This section
describes how voided Statements are handled by the LRS when queried. 

Clients can identify the presence and Statement id of any voided Statements by the target of the voiding Statement. 
Aside from debugging tools, many Learning Record Consumers will not want to display voiding Statements to their users 
and will not display these as part of activity streams and other reports. 

###### <a name="2.1.4.s1"></a>Requirements

* <a name="2.1.4.s1.b1"></a>The LRS MUST not return any Statement which has been voided, unless that Statement has been 
requested by voidedStatementId. The process described in [the section on filter conditions for StatementRefs](#queryStatementRef) 
is no exception to this requirement. The process of retrieving voiding Statements is to request each 
individually by voidedStatementId.

* <a name="2.1.4.s1.b2"></a>The LRS MUST still return any Statements targeting the voided Statement, following the process 
and conditions described in [the section on filter conditions for StatementRefs](#queryStatementRef). This includes the 
voiding Statement, which cannot be voided. 

<a name="doctransfer"/>

### <a name="2.2">2.2</a> Document Resources 

##### <a name="2.2.s1"></a>Description
The  xAPI provides a facility for Learning Record Providers to save arbitrary data in 
the form of documents, perhaps related to an Activity, Agent, or combination of both.

##### <a name="2.2.s2"></a>Details
Note that the following table shows generic properties, not a JSON Object as many other tables 
in this specification do. The id is stored in the IRL, "updated" is HTTP header information, and 
"contents" is the HTTP document itself (as opposed to an Object).
<table>
	<tr><th>Property</th><th>Type</th><th>Description</th></tr>
	<tr id="2.2.s2.table1.row1"><td>id</td><td>String</td><td>Set by Learning Record Provider, unique within the scope 
	of the Agent or Activity.</td></tr>
	<tr id="2.2.s2.table1.row2"><td>updated</td><td>Timestamp</td><td>When the document was most recently modified.</td></tr>
	<tr id="2.2.s2.table1.row3"><td>contents</td><td>Arbitrary binary data</td><td>The contents of the document</td></tr>
</table>

The three Document Resources provide [document](./xAPI-Data.md#documents) storage.  The details of each resource are found in 
the following sections, and the information in this section applies to all three resources.

###### <a name="2.2.s3"></a>Details

<table>
	<tr>
		<th>Resource</th>
		<th>Method</th>
		<th>Endpoint</th>
		<th>Example</th>
	</tr>
	<tr id="2.2.s3.table1.row1">
		<td>State Resource</td>
		<td>POST</td>
		<td>activities/state</td>
		<td>http://example.com/xAPI/activities/state</td>
	</tr>
	<tr id="2.2.s3.table1.row2">
		<td>Activity Profile Resource</td>
		<td>POST</td>
		<td>activities/profile</td>
		<td>http://example.com/xAPI/activities/profile</td>
	</tr>
	<tr id="2.2.s3.table1.row3">
		<td>Agent Profile Resource</td>
		<td>POST</td>
		<td>agents/profile</td>
		<td>http://example.com/xAPI/agents/profile</td>
	</tr>
</table>

###### <a name="2.2.s4"></a>Requirements

* <a name="2.2.s4.b1"></a>A Learning Record Provider MAY send documents to any of the Document Resources for Activities and 
Agents that the LRS does not have prior knowledge of. 

* <a name="2.2.s4.b2"></a>The LRS MUST NOT reject documents on the basis of not having prior knowledge of the Activity and/or Agent.

##### <a name="2.2.s5"></a>Last Modified
The "Last Modified" header is set by the LRS when returning single or multiple documents in response to a GET request. 

###### <a name="2.2.s6"></a>Requirements
* <a name="2.2.s6.b1"></a>When returning a single document, the LRS SHOULD* include a "Last-Modified" header indicating when
the document was last modified. 
* <a name="2.2.s6.b2"></a>When returning multiple documents, the LRS SHOULD* include a "Last-Modified" header indicating when
the most recently modified document was last modified. 

###### <a name="2.2.s7"></a>JSON Procedure with Requirements

If a Learning Record Provider stores variables as JSON Objects in a document with content type `application/json`, 
they can manipulate them as sets of variables using POST.

The following process walks through that process and the process requirements.
For example, a document contains: 

```
{
	"x" : "foo",
	"y" : "bar"
}
```
When an LRS receives a POST request with content type `application/json` for an existing document also of
content type `application/json`, it MUST merge the posted document with the existing document. 
In this context, merge is defined as:
* <a name="2.2.s7.b1"></a>de-serialize the Objects represented by each document.
* <a name="2.2.s7.b2"></a>for each property directly defined on the Object being posted, set the corresponding
property on the existing Object equal to the value from the posted Object.  
* <a name="2.2.s7.b3"></a>store any valid json serialization of the existing Object as the document referenced in the request.

Note that only top-level properties are merged, even if a top-level property is an Object. The entire contents of each 
original property are replaced with the entire contents of each new property.

For example, this document is POSTed with the same id as the existing document above:

```
{
	"x" : "bash",
	"z" : "faz"
}
```
the resulting document stored in the LRS is:
```
{
	"x" : "bash",
	"y" : "bar",
	"z" : "faz"
}
```

###### <a name="2.2.s8"></a>Requirements

* <a name="2.2.s8.b1"></a>If the document being posted or any existing document does not have a Content-Type
of `application/json`, or if either document cannot be parsed as a JSON Object, the LRS MUST
respond with HTTP status code `400 Bad Request`, and MUST NOT update the target document
as a result of the request.

* <a name="2.2.s8.b2"></a>If the merge is successful, the LRS MUST respond with HTTP status code `204 No Content`.

* <a name="2.2.s8.b3"></a>If a Learning Record Provider needs to delete a property, it SHOULD use a PUT request to replace 
the whole document as described below. 

<a name="stateres"/> 

### <a name="2.3">2.3</a> State Resource

##### <a name="2.3.s1"></a>Description

Generally, this is a scratch area for Learning Record Providers that do not have their own internal storage, 
or need to persist state across devices. 

##### <a name="2.3.s2"></a>Details

The semantics of the call are driven by the "stateId" parameter. If it is included, the GET and DELETE methods will 
act upon a single defined state document identified by "stateId". Otherwise, GET will return the available ids, 
and DELETE will delete all state in the context given through the other parameters. This resource has
[Concurrency](#concurrency) controls associated with it.

###### <a name="2.3.s3"></a>Single Document (PUT | POST | GET | DELETE)

Example endpoint: http://example.com/xAPI/activities/state

Stores, changes, fetches, or deletes the document specified by the given "stateId" that 
exists in the context of the specified Activity, Agent, and registration (if specified).

**Content (PUT | POST):** The document to be stored or updated.
**Content (GET | DELETE):** None.

**Returns (PUT | POST | DELETE):** `204 No Content`
**Returns (GET):** `200 OK`, the State document 
<table>
	<tr><th>Parameter</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.3.s3.table1.row1">
		<td>activityId</td>
		<td>Activity id (IRI)</td>
		<td>The Activity id associated with this state.</td>
		<td>Required</td>
	</tr>
	<tr id="2.3.s3.table1.row2">
		<td>agent</td>
		<td>Agent Object (JSON)</td>
		<td>The Agent associated with this state.</td>
		<td>Required</td>
	</tr>
	<tr id="2.3.s3.table1.row3">
		<td>registration</td>
		<td>UUID</td>
		<td>The registration associated with this state.</td>
		<td>Optional</td>
	</tr>
	<tr id="2.3.s3.table1.row4">
		<td>stateId</td>
		<td>String</td>
		<td>The id for this state, within the given context.</td>
		<td>Required</td>
	</tr>
</table>

###### <a name="2.3.s4"></a>Multiple Document GET

Example endpoint: http://example.com/xAPI/activities/state

Fetches State ids of all state data for this context (Activity + Agent \[ + registration if specified\]). 
If "since" parameter is specified, this is limited to entries that have been stored or updated since the specified 
timestamp (exclusive). 

**Content:** None.

**Returns:** `200 OK`, Array of State id(s)

<table>
	<tr><th>Parameter</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.3.s4.table1.row1">
		<td>activityId</td>
		<td>Activity id (IRI)</td>
		<td>The Activity id associated with these states.</td>
		<td>Required</td>
	</tr>
	<tr id="2.3.s4.table1.row2">
		<td>agent</td>
		<td>Agent object (JSON)</td>
		<td>The Agent associated with these states.</td>
		<td>Required</td>
	</tr>
	<tr id="2.3.s4.table1.row3">
		<td>registration</td>
		<td>UUID</td>
		<td>The Registration associated with these states.</td>
		<td>Optional</td>
	</tr>
	<tr id="2.3.s4.table1.row4">
		<td>since</td>
		<td>Timestamp</td>
		<td>Only ids of states stored since the specified Timestamp (exclusive) are returned.</td>
		<td>Optional</td>
	</tr>
</table>

###### <a name="2.3.s5"></a>Multiple Document DELETE

Example endpoint: http://example.com/xAPI/activities/state

Deletes all state data for this context (Activity + Agent \[+ registration if specified\]).

**Content:** None.

**Returns**: `204 No Content`
<table>
	<tr><th>Parameter</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.3.s5.table1.row1">
		<td>activityId</td>
		<td>Activity id (IRI)</td>
		<td>The Activity id associated with this state.</td>
		<td>Required</td>
	</tr>
	<tr id="2.3.s5.table1.row2">
		<td>agent</td>
		<td>Agent object (JSON)</td>
		<td>The Agent associated with this state.</td>
		<td>Required</td>
	</tr>
	<tr id="2.3.s5.table1.row3">
		<td>registration</td>
		<td>UUID</td>
		<td>The Registration associated with this state.</td>
		<td>Optional</td>
	</tr>
</table>

<a name="agentsres"/>

### <a name="2.4">2.4</a> Agents Resource

The Agents Resource provides a method to retrieve a special Object with combined information about an Agent derived from 
an outside service, such as a directory service. This resource has [Concurrency](#concurrency) controls associated with it.

###### <a name="2.4.s1"></a>Combined Information GET

###### <a name="2.4.s2"></a>Details

Example endpoint: http://example.com/xAPI/agents

Return a special, Person Object for a specified Agent. The Person Object is very similar to an Agent Object, 
but instead of each attribute having a single value, each attribute has an array value, and it is legal to 
include multiple identifying properties. This is different from the FOAF concept of person, person is being 
used here to indicate a person-centric view of the LRS Agent data, but Agents just refer to one 
persona (a person in one context).

The "agent" parameter is a normal Agent Object with a single identifier and no arrays. 
It is not a Person Object, nor is it a Group. 

**Content:** None.

**Returns:** `200 OK`, Person Object

<table>
	<tr><th>Parameter</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.4.s2.table1.row1">
		<td>agent</td>
		<td>Agent object (JSON)</td>
		<td>The Agent representation to use in fetching expanded Agent information.</td>
		<td>Required</td>
	</tr>
</table>

###### <a name="2.4.s3"></a>Requirements
* <a name="2.4.s3.b1"></a>An LRS capable of returning multiple identifying properties for a Person 
Object SHOULD require the connecting credentials have increased, explicitly 
given permissions. 
* <a name="2.4.s3.b2"></a>An LRS SHOULD reject insufficiently privileged requests with `403 Forbidden`.
* <a name="2.4.s3.b3"></a>If an LRS does not have any additional information about an Agent to return, 
the LRS MUST still return a Person Object when queried, but that Person Object will only 
include the information associated with the requested Agent. 

__Note:__ This means that if a request is made for an Agent which the LRS has no 
prior knowledge of, it will still return a Person object containing the information 
about the Agent it received in the request. 

###### <a name="2.4.s4"></a>Person Properties

###### <a name="2.4.s5"></a>Details

<table>
	<tr><th>Property</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.4.s5.table1.row1">
		<td>objectType</td>
		<td>String</td>
		<td><code>Person</code></td>
		<td>Required</td>
	</tr>
	<tr id="2.4.s5.table1.row2">
		<td>name</td>
		<td>Array of strings.</td>
		<td>List of names of Agents retrieved.</td>
		<td>Optional</td>
	</tr>
	<tr id="2.4.s5.table1.row3">
		<td><a href="http://xmlns.com/foaf/spec/#term_mbox">mbox</a></td>
		<td>Array of IRIs in the form "mailto:email address".</td>
		<td>List of e-mail addresses of Agents retrieved.</td>
		<td>Optional</td>
	</tr>
	<tr id="2.4.s5.table1.row4">
		<td><a href="http://xmlns.com/foaf/spec/#term_mbox_sha1sum">mbox_sha1sum</a></td>
		<td>Array of strings.</td>
		<td>List of the SHA1 hashes of mailto IRIs (such as go in an mbox property).</td>
		<td>Optional</td>
	</tr>
	<tr id="2.4.s5.table1.row5">
		<td>openid*</td>
		<td>Array of strings.</td>
		<td>List of openids that uniquely identify the Agents retrieved.</td>
		<td>Optional</td>
	</tr>
	<tr id="2.4.s5.table1.row6">
		<td>account*</td>
		<td>Array of account objects.</td>
		<td>List of accounts to match. Complete account Objects (homePage and name) 
		MUST be provided.</td>
		<td>Optional</td>
	</tr>
</table>

See also: [Agent](./xAPI-Data.md#agent).

###### <a name="2.4.s6"></a>Requirements

* <a name="2.4.s6.b1"></a>All array properties MUST be populated with members with the same definition as the 
similarly named property from Agent Objects.

* <a name="2.4.s6.b2"></a>Additional properties not listed here SHOULD* NOT be added to this object and each 
property MUST occur only once. 

<a name="activitiesres"/> 

### <a name="2.5">2.5</a> Activities Resource

The Activities Resource provides a method to retrieve a full description of an Activity from the LRS. 
This resource has [Concurrency](#concurrency) controls associated with it.

###### <a name="2.5.s1"></a>Full Activity Object GET

Example endpoint: http://example.com/xAPI/activities

Loads the complete Activity Object specified.

**Content:** None.

**Returns:** `200 OK`, Content 
<table>
	<tr><th>Parameter</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.5.s1.table1.row1">
		<td>activityId</td>
		<td>Activity id (IRI)</td>
		<td>The id associated with the Activities to load.</td>
		<td>Required</td>
	</tr>
</table>

###### <a name="2.5.s2"></a>Requirements

* <a name="2.5.s2.b1"></a>If an LRS does not have a canonical definition of the Activity to return, the LRS SHOULD* 
still return an Activity Object when queried.

<a name="agentprofres"/>

### <a name="2.6">2.6</a> Agent Profile Resource

###### <a name="2.6.s1"></a>Description

The Agent Profile Resource is much like the State Resource, allowing for arbitrary key / document pairs to be saved 
which are related to an Agent. 

###### <a name="2.6.s2"></a>Details

The semantics of the request are driven by the "profileId" parameter. If it is included, the GET method will act upon 
a single defined document identified by "profileId". Otherwise, GET will return the available ids.

###### <a name="2.6.s3"></a>Single Agent or Profile Document (PUT | POST | GET | DELETE)

Example endpoint: http://example.com/xAPI/agents/profile

Stores, changes, fetches, or deletes the specified Profile document in the context of the specified Agent.

**Content (PUT | POST):** The document to be stored or updated.
**Content (GET | DELETE):** None.

**Returns (PUT | POST | DELETE):** `204 No Content`
**Returns (GET):** `200 OK`, the Profile document

<table>
	<tr><th>Parameter</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.6.s3.table1.row1">
		<td>agent</td>
		<td>Agent object (JSON)</td>
		<td>The Agent associated with this Profile document.</td>
		<td>Required</td>
	</tr>
	<tr id="2.6.s3.table1.row2">
		<td>profileId</td>
		<td>String</td>
		<td>The profile id associated with this Profile document.</td>
		<td>Required</td>
	</tr>
</table>

__Note:__ The "agent" parameter is an Agent Object and not a Group. Learning Record Providers wishing to store data
against an Identified Group can use the Identified Group's identifier within an Agent Object. 

###### <a name="2.6.s4"></a>Multiple Document GET

Example endpoint: http://example.com/xAPI/agents/profile

Fetches Profile ids of all Profile documents for an Agent. If "since" parameter is specified, this is limited to entries 
that have been stored or updated since the specified Timestamp (exclusive).

**Content:** None.

**Returns:** `200 OK`, Array of Profile id(s)

<table>
	<tr><th>Parameter</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.6.s4.table1.row1">
		<td>agent</td>
		<td>Agent object (JSON)</td>
		<td>The Agent associated with this Profile document.</td>
		<td>Required</td>
	</tr>
	<tr id="2.6.s4.table1.row2">
		<td>since</td>
		<td>Timestamp</td>
		<td>Only ids of Profiles stored since the specified Timestamp 
			(exclusive) are returned.</td>
		<td>Optional</td>
	</tr>
</table>

<a name="actprofres"/> 

### <a name="2.7">2.7</a> Activity Profile Resource

###### <a name="2.7.s1"></a>Description

The Activity Profile Resource is much like the State Resource, allowing for arbitrary key / document pairs to be saved 
which are related to an Activity. 

###### <a name="2.7.s2"></a>Details

The semantics of the request are driven by the "profileId" parameter. If it is included, 
the GET method will act upon a single defined document identified by "profileId". 
Otherwise, GET will return the available ids.

###### <a name="2.7.s3"></a>Single Document (PUT | POST | GET | DELETE)

Example endpoint: http://example.com/xAPI/activities/profile

Stores, changes, fetches, or deletes the specified Profile document in the context of the specified Activity.

**Content (PUT | POST):** The document to be stored or updated.
**Content (GET | DELETE):** None.

**Returns (PUT | POST | DELETE)** `204 No Content`
**Returns (GET):** `200 OK`, the Profile document
<table>
	<tr><th>Parameter</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.7.s3.table1.row1">
		<td>activityId</td>
		<td>Activity id (IRI)</td>
		<td>The Activity id associated with this Profile document.</td>
		<td>Required</td>
	</tr>
	<tr id="2.7.s3.table1.row2">
		<td>profileId</td>
		<td>String</td>
		<td>The profile id associated with this Profile document.</td>
		<td>Required</td>
	</tr>
</table>

###### <a name="2.7.s4"></a>Multiple Document GET

Example endpoint: http://example.com/xAPI/activities/profile

Fetches Profile ids of all Profile documents for an Activity. If "since" parameter is specified, this is limited to 
entries that have been stored or updated since the specified Timestamp (exclusive).

**Content:** None.

**Returns:** `200 OK`, Array of Profile id(s)

<table>
	<tr id="2.7.s4.table1.row1"><th>Parameter</th><th>Type</th><th>Description</th><th>Required</th><tr>
	<tr>
		<td>activityId</td>
		<td>Activity id (IRI)</td>
		<td>The Activity id associated with these Profile documents.</td>
		<td>Required</td>
	</tr>
	<tr id="2.7.s4.table1.row2">
		<td>since</td>
		<td>Timestamp</td>
		<td>Only ids of Profile documents stored since the specified Timestamp (exclusive) 
		are returned.</td>
		<td>Optional</td>
	</tr>
</table>


<a name="aboutresource"/> 

### <a name="2.8">2.8</a> About Resource

###### <a name="2.8.s1"></a>Description

Returns JSON Object containing information about this LRS, including the xAPI version supported.

###### <a name="2.8.s2"></a>Rationale

Primarily this resource exists to allow Clients that support multiple xAPI versions to decide which version to 
use when communicating with the LRS. Extensions are included to allow other uses to emerge.

###### <a name="2.8.s3"></a>Details

###### <a name="2.8.s4"></a>Information GET

Example endpoint: http://example.com/xAPI/about

**Content:** None.

**Returns:** `200 OK`, JSON object containing basic metadata about this LRS
<table border="1">
	<tr><th>Property</th><th>Type</th><th>Description</th><th>Required</th></tr>
	<tr id="2.8.s4.table1.row1">
		<td>version</td>
		<td>Array of version strings</td>
		<td>xAPI versions this LRS supports</td>
		<td>Required</td>
	</tr>
	<tr id="2.8.s4.table1.row2">
		<td>extensions</td>
		<td><a href="./xAPI-Data.md#miscext">Object</a></td>
		<td>A map of other properties as needed</td>
		<td>Optional</td>
	</tr>

</table>

###### <a name="2.8.s5"></a>Requirements

* <a name="2.8.s5.b1"></a>An LRS MUST return the JSON document described above, with a "version" property that includes
the latest minor and patch version the LRS conforms to, for each major version.
    * <a name="2.8.s5.b1.b1"></a>For version 1.0.0 of this specification, this means that `1.0.0` MUST be included;
    `0.9` and `0.95` MAY be included. (For the purposes of this requirement, `0.9` and `0.95`
    are considered major versions.)
* <a name="2.8.s5.b2"></a>Additional properties MUST NOT be added to this object outside of extensions and each 
property MUST occur only once.
* <a name="2.8.s5.b3"></a>An LRS SHOULD allow unauthenticated access to this resource.
* <a name="2.8.s5.b4"></a>An LRS MUST NOT reject requests based on their version header as would otherwise be 
required by [Versioning](#versioning).

<a name="validation"/> 

## <a name="3.0">3.0</a> Data Validation

###### <a name="3.0.s1"></a>Description

The function of the LRS within the xAPI is to store and retrieve Statements. As long as it has sufficient information 
to perform these tasks, it is expected that it does them. Validation of Statements in the  xAPI is focused 
solely on syntax, not semantics. Enforcing the rules that ensure valid meaning among Verb definitions, Activity types, 
and extensions is the responsibility of the Learning Record Provider sending the Statement. 

###### <a name="3.0.s2"></a>Requirements

* <a name="3.0.s2.b1"></a>The LRS SHOULD enforce rules regarding structure. 
* <a name="3.0.s2.b2"></a>The LRS SHOULD NOT enforce rules regarding meaning.

<a name="concurrency"/>

### <a name="3.1">3.1</a> Concurrency

##### <a name="3.1.s1"></a>Description
Concurrency control makes certain that a client does not PUT, POST or DELETE documents based on old
data into an LRS.

##### <a name="3.1.s2"></a>Details
xAPI will use HTTP 1.1 entity tags ([ETags](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.19))
to implement optimistic concurrency control in the portions of the API where PUT, POST or DELETE might
overwrite or remove existing data, being:

* <a name="3.1.s2.b1"></a>State Resource
* <a name="3.1.s2.b2"></a>Agent Profile Resource 
* <a name="3.1.s2.b3"></a>Activity Profile Resource

##### <a name="3.1.s3"></a>Client Requirements
The State Resource will permit PUT, POST and DELETE requests without concurrency headers, since state conflicts
are unlikely. The requirements below only apply to Agent Profile Resource and Activity Profile Resource.

* <a name="3.1.s3.b1"></a>A Client making a PUT request to either the Agent Profile Resource or Activity Profile 
Resource MUST include the "[If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24)" header or the 
[If-None-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.26) header.

* <a name="3.1.s3.b2"></a>A Client making a POST request to either the Agent Profile Resource or Activity Profile 
Resource SHOULD* include the "[If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24)" header or the 
[If-None-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.26) header.

* <a name="3.1.s3.b3"></a>A Client making a DELETE request to either the Agent Profile Resource or Activity Profile 
Resource SHOULD* include the "[If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24)" header.

* <a name="3.1.s3.b4"></a>Clients SHOULD* use the ETag value provided by the LRS rather than calculating it themselves. 

##### <a name="3.1.s4"></a>LRS Requirements

* <a name="3.1.s4.b1"></a>An LRS responding to a GET request MUST add an ETag HTTP header to the response.
* <a name="3.1.s4.b2"></a>An LRS responding to a GET request without using a transfer encoding or using the identity 
transfer encoding MUST calculate the value of the ETag header to be a hexadecimal string of the SHA-1 digest of the contents. 
This hexadecimal string SHOULD be rendered using numbers and lowercase characters only; uppercase characters SHOULD NOT be used. 
The requirement to calculate the ETag this way will be removed in a future version of the specification.
* <a name="3.1.s4.b3"></a>An LRS responding to a GET request using any non-identity transfer encoding MUST NOT calculate 
the included ETag as above, due to the interpretation of ETags by existing web infrastructure.
* <a name="3.1.s4.b4"></a>As defined in [RFC 2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.19), 
an LRS responding to a GET request MUST enclose the header in quotes.
* <a name="3.1.s4.b5"></a>An LRS responding to a PUT request MUST handle the "[If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24)" header as described in RFC2616, HTTP 1.1 if 
it contains an ETag, in order to detect modifications made after the Client last fetched the document.
* <a name="3.1.s4.b6"></a>An LRS responding to a PUT request MUST handle the "[If-None-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.26)" header as described in 
RFC2616, HTTP 1.1 if it contains "*", in order to to detect when there is a resource present that the Client is not aware of.
* <a name="3.1.s4.b7"></a>An LRS responding to a POST or DELETE request SHOULD* handle the "[If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24)" header as described in RFC2616, HTTP 1.1 
if it contains an ETag, in order to detect modifications made after the Client last fetched the document.
* <a name="3.1.s4.b8"></a>An LRS responding to a POST request SHOULD* handle the 
"[If-None-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.26)" header as described in RFC2616, HTTP 1.1 if it 
contains "*", in order to to detect when there is a resource present that the Client is not aware of.

If the header precondition in either of the PUT request cases above fails, the LRS:

* <a name="3.1.s4.b9"></a>MUST return HTTP status `412 Precondition Failed`.
* <a name="3.1.s4.b10"></a>MUST NOT make a modification to the resource. 

If the header precondition in any of the POST or DELETE request cases above fails, the LRS:

* <a name="3.1.s4.b11"></a>SHOULD* return HTTP status `412 Precondition Failed`.
* <a name="3.1.s4.b12"></a>SHOULD* NOT make a modification to the resource. 

If a PUT request is received without either header for a resource that already exists, the LRS:

* <a name="3.1.s4.b13"></a>MUST return HTTP status `409 Conflict`.
* <a name="3.1.s4.b14"></a>MUST return a response explaining that the Learning Record Provider SHOULD
	* <a name="3.1.s4.b14.b1"></a>check the current state of the resource.
	* <a name="3.1.s4.b14.b2"></a>set the "If-Match" header with the current ETag to resolve the conflict.
* <a name="3.1.s4.b15"></a>MUST NOT make a modification to the resource.

<a name="errorcodes" /> 

### <a name="3.2">3.2</a> Error Codes

##### <a name="3.2.s1"></a>Description

This specification defines requirements, some of which are imposed on the LRS to accept or reject requests,
return responses and perform other behaviors in certain conditions. In cases where an LRS is required 
to reject a request, the appropriate error code is listed as part of the requirement. 

None of these requirements contradict the idea that the LRS is also allowed to be configurable to reject requests 
and respond or behave differently on the basis of conditions that are out of scope this specification. 

One of these conditions is permission. For example, the LRS might assign permissions to a particular set of 
credentials such that those credentials can only issue Statements relating to a particular agent. It could then 
reject any statements using those credentials not relating to that agent. The permissions that can be assigned 
by an LRS are out of scope of this specification, aside from the list of recommended OAuth Authorization scope 
values in section [4.2](#oauthscope). 

Permissions can also affect the response returned by an LRS to GET requests. For example, 
a set of credentials might have permission only to view Statements about a particular Actor, in which case
the LRS will filter any returned Statements to exclude any Statements not relating to that Actor. See 
[GET Statements](#stmtresget) for details. 

In cases explicitly allowed by this specification, the credentials used can also affect the LRS behavior in 
handling a request, for example the LRS will normally overwrite the "authority" property of a Statement, but can 
sometimes accept a submitted authority if it has a strong trust relationship associated with the credentials 
used to submit the Statement. See [Authority](./xAPI-Data.md#authority) for details. 

Permissions set by an LRS could cause a technically conformant LRS to fail conformance testing. 
This could occur where requests made by the testing software are rejected on the basis of permissions. For this reason
the LRS needs to be configurable, or credentials used for testing need to have sufficient permissions granted,
such that permission restrictions do not affect the result of conformance testing. 

Another condition is where the request sent is beyond the size limits set by the LRS. It would be unreasonable
to expect the LRS to always accept requests of any size. The LRS can choose any size limit it sees fit, but
needs to be configurable so as not to apply size limits during conformance testing. Of course, some size limits
will still exist during conformance testing due to limitations of hardware, etc. but it is expected that these limits
are sufficiently high so as not to affect the running of tests. 

The LRS can also reject requests or revoke credentials in case of suspected malicious intent, for example
an unexpected large number of requests made in a short period of time. It is expected that that limits 
will be sufficiently high such that the rate of requests made during conformance testing will not trigger any rate limits.

##### <a name="3.2.s2"></a>Details
The list below offers some general guidance on HTTP error codes that could be returned from various methods in the API. 

* <a name="3.2.s2.b1"></a>`400 Bad Request` - Indicates
an error condition caused by an invalid or missing argument. The term 
"invalid arguments" includes malformed JSON or invalid Object structures.

* <a name="3.2.s2.b2"></a>`401 Unauthorized` - Indicates that authentication is required, or in the 
case authentication has been posted in the request, that the given credentials have been refused.

* <a name="3.2.s2.b3"></a>`403 Forbidden` - Indicates that the request is unauthorized for the given 
credentials. Note this is different than refusing the credentials given. In this case, the credentials 
have been validated, but the authenticated Client is not allowed to perform the given action.

* <a name="3.2.s2.b4"></a>`404 Not Found` - Indicates the requested resource was not found. May be 
returned by any method that returns a uniquely identified resource, for instance, any State, Agent Profile, 
or Activity Profile Resource request targeting a specific document, or the method to retrieve a single Statement.

* <a name="3.2.s2.b5"></a>`409 Conflict` - Indicates an error condition due to a conflict with the 
current state of a resource, in the case of State Resource, Agent Profile Resource or Activity Profile Resource
requests, or in the Statement Resource PUT or POST calls. See Section [3.1 Concurrency](#concurrency) for more details.

* <a name="3.2.s2.b6"></a>`412 Precondition Failed` - Indicates an error condition due to a failure of 
a precondition posted with the request, in the case of State or Agent Profile or Activity Profile 
API requests. See Section [6.3 Concurrency](#concurrency) for more details.

* <a name="3.2.s2.b7"></a>`413 Request Entity Too Large` - Indicates that the LRS has rejected the Statement or 
document because its size (or the size of an Attachment included in the request) is larger than 
the maximum allowed by the LRS. 

* <a name="3.2.s2.b8"></a>`429 Too Many Requests` - Indicates that the LRS has rejected the request because it 
has received too many requests from the Client or set of credentials in a given amount of time. 

* <a name="3.2.s2.b9"></a>`500 Internal Server Error` - Indicates a general error condition, typically an 
unexpected exception in processing on the server.

##### <a name="3.2.s3"></a>Requirements

* <a name="3.2.s3.b1"></a>An LRS MUST return the error code most appropriate to the error condition from the list above.

* <a name="3.2.s3.b2"></a>An LRS SHOULD return a message in the response explaining the cause of the error.

* <a name="3.2.s3.b3"></a>An LRS SHOULD use content negotiation as described in [RFC 7231](http://tools.ietf.org/html/rfc7231#section-5.3) to decide the format of the error.

* <a name="3.2.s3.b4"></a>An LRS SHOULD allow for plain text, HTML, and JSON responses for errors (using content negotiation).

* <a name="3.2.s3.b5"></a>A Learning Record Provider SHOULD send an "Accept" header with requests to enable content negotiation.

* <a name="3.2.s3.b6"></a>The LRS SHOULD* reject any request with `400 Bad Request` status where the content type header 
does not match the content included in the request or where the structure of the request does not match the structure 
outlined in this specification for a particular content type. For example, if the content of the request is formatted as JSON, 
the content type is expected to be `application/json`. If the content type is application/x-www-form-urlencoded it is expected 
that the request will include a method parameter as outlined in [Alternate Request Syntax](#alt-request-syntax).

* <a name="3.2.s3.b7"></a>The LRS MUST reject with `400 Bad Request` status any requests that use any parameters which the LRS 
does not recognize in their intended context in this specification. 
( __Note:__ LRSs MAY recognize and act on parameters not in this specification).

* <a name="3.2.s3.b8"></a>The LRS MUST reject with `400 Bad Request` status any requests that use any parameters 
matching parameters described in this specification in all but case.

* <a name="3.2.s3.b9"></a>The LRS MUST reject a batch of statements if any Statement within that batch is rejected.

* <a name="3.2.s3.b10"></a>The LRS MUST reject with `403 Forbidden` status any request rejected by the LRS where the 
credentials associated with the request do not have permission to make that request. 

* <a name="3.2.s3.b11"></a>The LRS MUST reject with `413 Request Entity Too Large` status any request rejected by the LRS 
where the size of the Attachment, Statement or document is larger than the maximum allowed by the LRS.

* <a name="3.2.s3.b12"></a>The LRS MAY choose any Attachment, Statement and document size limits and MAY vary this limit 
on any basis, e.g., per authority.

* <a name="3.2.s3.b13"></a>The LRS MUST reject with `429 Too Many Requests` status any request rejected by the LRS where 
the request is rejected due to too many requests being received by a particular Client or set of credentials in a given 
amount of time. 

* <a name="3.2.s3.b14"></a>The LRS MAY choose any rate limit and MAY vary this limit on any basis, e.g., per authority.

The following requirements exist for the purposes of conformance testing, to ensure that any limitations or permissions 
implemented by the LRS do not affect the running of conformance testing software. 

* <a name="3.2.s3.b15"></a>The LRS SHOULD* be configurable not to reject any requests from a particular set of credentials 
on the basis of permissions. This set of credentials SHOULD* be used for conformance testing but MAY be deleted/deactivated 
on live systems. 

* <a name="3.2.s3.b16"></a>The LRS MUST be configurable to accept Attachments, Statements or documents of any reasonable 
size (see above).

* <a name="3.2.s3.b17"></a>The LRS MUST be configurable to accept requests at any reasonable rate. 

<a name="versioning"/> 

### <a name="3.3">3.3</a> Versioning

###### <a name="3.3.s1"></a>Rationale

Future revisions of the specification might introduce changes such as properties added to Statements. Using Semantic 
Versioning will allow Clients and LRSs to remain interoperable as the specification changes.

###### <a name="3.3.s2"></a>Details

Starting with version 1.0.0, xAPI will be versioned according to [Semantic Versioning 1.0.0](http://semver.org/spec/v1.0.0.html).
Every request from a Client and every response from the LRS includes an HTTP header with the name `X-Experience-API-Version` 
and the version as the value. For example, ``X-Experience-API-Version : 1.0.3`` for version 1.0.3; 
see the [Revision History](./xAPI-About.md#Appendix1A) for the current version of this specification. 

__Note:__ For patch versions of the specification later than 1.0.0, the "X-Experience-API-Version" header will not match the 
[statement version property](./xAPI-Data.md#version) which is always `1.0.0` for all 1.0.x versions of the spec. The
"X-Experience-API-Version" header enables the LRS and Client to determine the exact patch version of the specification being 
followed. While no communication incompatibility should arise among 1.0.x versions, there are sometimes clarifications 
of previously intended behavior.

###### <a name="3.3.s3"></a>LRS Requirements

* <a name="3.3.s3.b1"></a>The LRS MUST include the "X-Experience-API-Version" header in every response.
* <a name="3.3.s3.b2"></a>The LRS MUST set this header to the latest patch version.
* <a name="3.3.s3.b3"></a>The LRS MUST accept requests with a version header of `1.0` as if the version header was `1.0.0`.
* <a name="3.3.s3.b4"></a>The LRS MUST reject requests with version header prior to version 1.0.0 unless such requests are 
routed to a fully conformant implementation of the prior version specified in the header.
* <a name="3.3.s3.b4.1"></a>The LRS MUST reject requests without a version header unless such requests are 
routed to a fully conformant 0.9 implementation.
* <a name="3.3.s3.b5"></a>The LRS MUST accept requests with a version header starting with `1.0.` if the request is otherwise valid. 
* <a name="3.3.s3.b6"></a>The LRS MUST reject requests with a version header of `1.1.0` or greater.
* <a name="3.3.s3.b7"></a>The LRS MUST make these rejects by responding with a `400 Bad Request` error including a short 
description of the problem.

###### <a name="3.3.s4"></a>Client Requirements

* <a name="3.3.s4.b1"></a>The Client MUST include the "X-Experience-API-Version" header in every request.
* <a name="3.3.s4.b2"></a>The Client MUST set this header to the latest patch version.
* <a name="3.3.s4.b3"></a>The Client SHOULD tolerate receiving responses with a version of `1.0.0` or greater.
* <a name="3.3.s4.b4"></a>The Client SHOULD tolerate receiving data structures with additional properties.
* <a name="3.3.s4.b5"></a>The Client SHOULD ignore any properties not defined in version 1.0.0 of the spec.

###### <a name="3.3.s5"></a>Conversion Requirements

* <a name="3.3.s5.b1"></a>Statements of newer versions MUST NOT be converted into a prior version format, e.g., in order 
to handle version differences.
* <a name="3.3.s5.b2"></a>Statements of prior versions MAY be converted into a newer version only by following the methods 
described in [Appendix A: Converting Statements to 1.0.0](#Appendix3A).

<a name="authentication"/>

## <a name="4.0">4.0</a> Authentication

###### <a name="4.0.s1"></a>Rationale

In order to balance interoperability and the varying security requirements of different environments, several 
authentication options are defined.

###### <a name="4.0.s2"></a>Details
The following authentication methods are defined within the specification. Any given LRS will implement at least one 
of these methods and might implement additional methods not defined within this specification. 

* <a name="4.0.s2.b1"></a>[OAuth 1.0 (RFC 5849)](http://tools.ietf.org/html/rfc5849), with signature methods of 
"HMAC-SHA1", "RSA-SHA1", and "PLAINTEXT"
* <a name="4.0.s2.b2"></a>[HTTP Basic Authentication](http://tools.ietf.org/html/rfc7235)
* <a name="4.0.s2.b3"></a>Common Access Cards

While Common Access Cards are defined as an authentication method within this specification, the implementation details of 
this authentication method are not defined. The xAPI Working Group encourages LRS developers implementing Common Access Cards 
as an authentication method to collaborate in defining the details of this authentication method in a future version of this 
specification. 

No further details are provided in this specification to describe HTTP Basic Authentication as this authentication method
is clearly and completely defined in [RFC 7235](http://tools.ietf.org/html/rfc7235). 

###### <a name="4.0.s3"></a>Requirements

* <a name="4.0.s3.b1"></a>The LRS MUST support authentication using at least one of the authentication methods defined 
in this specification.

* <a name="4.0.s3.b2"></a>The LRS MUST handle making, or delegating, decisions on the validity of Statements, and 
determining what operations might be performed based on the credentials used.

<a name="authdefs"/>

### <a name="4.1">4.1</a> OAuth 1.0 Authentication Scenarios and Methods

The matrix and requirements below describe the possible authentication scenarios used within OAuth and recommends the 
authentication workflow to be used in these scenarios. The process described for each scenario is not intended 
to be comprehensive, but rather outline variations to the standard OAuth workflow. 

The requirements in this section only apply if the LRS supports OAuth 1.0.

A **registered application** is an application that will authenticate to the LRS as an OAuth consumer that has been 
registered with the LRS.

A **known user** is a user account on the LRS, or on a system which the LRS trusts to define users.


<table border="1">
<tr><th></th><th>Known user</th><th>User unknown</th></tr>
<tr id="4.1.table1.row1">
<td>Application is registered</td>
<td>Standard workflow for OAuth.</td>
<td>LRS trusts application to access xAPI without additional user credentials. OAuth token steps are not invoked</td>
</tr>
<tr id="4.1.table1.row2">
<td>Application is not registered</td>
<td>The application Agent is not identified as a registered Agent and the LRS cannot make assumptions on its identity.</td>
<td></br></td>
</tr>
<tr id="4.1.table1.row3">
<td>No application</td>
<td>HTTP Basic Authentication is used instead of OAuth, since no application is involved.</td>
<td></br></td>
</tr>
<tr id="4.1.table1.row4">
<td>No authentication</td>
<td align="center"colspan="2">MAY be supported by the LRS, possibly for testing purposes.</td>

</tr>

</table>

##### <a name="4.1.s2"></a>Requirements

* <a name="4.1.s2.b1"></a>The LRS MUST record the application's name and a unique consumer key (identifier).
* <a name="4.1.s2.b2"></a>The LRS MUST provide a mechanism to complete this registration, or delegate to another system 
that provides such a mechanism.
* <a name="4.1.s2.b3"></a>The LRS MUST be able to be configured for complete support of the xAPI:
	* <a name="4.1.s2.b3.b1"></a>With any of the methods below.
	* <a name="4.1.s2.b3.b2"></a>In any of the workflow scenarios below.
* <a name="4.1.s2.b4"></a>The LRS MAY (for security reasons): 
	* <a name="4.1.s2.b4.b1"></a>Support a subset of the methods below.
	* <a name="4.1.s2.b4.b2"></a>Limit the known users or registered applications.
* <a name="4.1.s2.b5"></a>The LRS SHOULD at a minimum supply OAuth with "HMAC-SHA1" and "RSA-SHA1" signatures.

###### <a name="4.1.s3"></a>Application registered + known user Process and Requirements
**Process:** The standard workflow for OAUth 1.0 is used. 

**Requirements:**
* <a name="4.1.s3.b1"></a>The LRS MUST support the resources in [OAuth Authorization Scope](#oauthscope) to complete 
the standard OAuth workflow (details not in this specification).
* <a name="4.1.s3.b2"></a>If this form of authentication is used to record Statements and no authority is specified, the LRS 
SHOULD record the authority as a Group consisting of an Agent representing the registered application, and an Agent 
representing the known user.

###### <a name="4.1.s4"></a>Application registered + user unknown Process and Requirements

**Process:** 
The LRS honors requests that are signed using OAuth with the registered application's credentials and with an empty token 
and token secret.

**Requirements:**
* <a name="4.1.s4.b1"></a>If this form of authentication is used to record Statements, the LRS SHOULD record the authority 
as the Agent representing the registered application.

###### <a name="4.1.s5"></a>Application Not Registered + Known User Process and Requirements

**Process:**
The Learning Record Provider uses a consumer secret consisting of an empty string to call the Temporary Credential 
Request endpoint specifying the "consumer_name" and other usual parameters.  The "consumer_name" contains a string 
representing the application requesting access. 

The Learning Record Provider then sends the user's browser to the Resource Owner Authorization using the temporary 
credentials obtained from the LRS. The Resource Owner Authorization presents a page displaying the "consumer_name" 
plus a warning that the identity of the application requesting authorization cannot be verified.

Otherwise the process follows the standard OAuth workflow. 

**Requirements:**
* <a name="4.1.s5.b1"></a>If this form of authentication is used to record Statements, the LRS MUST record an authority 
that includes both that application and the authenticating user, as a Group, since OAuth specifies an application.

###### <a name="4.1.s6"></a>No Application + Known User Process and Requirements
**Process:**
Use a username/password combination provided by the LRS for use by the known user.

**Requirements:**
* <a name="4.1.s6.b1"></a>If this form of authentication is used to record Statements, the LRS SHOULD 
record the authority as the Agent representing the known user.

###### <a name="4.1.s7"></a>No Authorization Process and Requirements

* <a name="4.1.s7.b1"></a>Requests MUST include headers for HTTP Basic Authentication based on a username and password 
containing zero or more space characters. 
* <a name="4.1.s7.b2"></a>Requests SHOULD* include headers for HTTP Basic Authentication based on a username and password 
each consisting of an empty string. In this case the HTTP Basic Authentication header will be `Basic ` followed by a base64 
encoded version of the string `:`.  This results in the string `Basic Og==`.

This is in order to distinguish an explicitly unauthenticated request from a request that needs to be given a 
HTTP Basic Authentication challenge.

<a name="oauthscope"/> 

### <a name="4.2">4.2</a> OAuth 1.0 Authorization Scope

##### <a name="4.2.s1"></a>Description
These are recommendations for scopes designed to enable an LRS and an application communicating using the xAPI to 
negotiate a level of access which accomplishes what the application needs while minimizing the potential for misuse. 
The limitations of each scope are in addition to any security limitations placed on the user account associated 
with the request.

Elements of this section draw on [OAuth 2.0](http://tools.ietf.org/html/rfc6749#section-3.3)
despite this section describing requirements for LRS supporting [OAuth 1.0](http://tools.ietf.org/html/rfc5849). 

The requirements in this section only apply if the LRS supports OAuth 1.0.

##### <a name="4.2.s2"></a>Details

The following table lists xAPI scope values:
<table>
	<tr><th>Scope</th><th>Permission</th></tr>
	<tr id="4.2.s2.table1.row1"><td>statements/write</td><td>write any Statement</td></tr>
	<tr id="4.2.s2.table1.row2">
		<td>statements/read/mine</td>
		<td>read Statements written by "me", that is with an authority 
			matching what the LRS would assign if writing a Statement with 
			the current token.
		</td>
	</tr>
	<tr id="4.2.s2.table1.row3"><td>statements/read</td><td>read any Statement</td>
	<tr>
		<td>state</td>
		<td>read/write state data, limited to Activities and Actors 
			associated with the current token to the extent it is 
			possible to determine this relationship.
		</td>
	</tr>
	<tr id="4.2.s2.table1.row4">
		<td>define</td>
		<td>(re)Define Activities and Actors. If storing a Statement 
			when this is not granted, ids will be saved and the LRS 
			MAY save the original Statement for audit purposes, but 
			SHOULD NOT update its canonical representation of any 
			Actors or Activities.
		</td>
	</tr>
	<tr id="4.2.s2.table1.row5">
		<td>profile</td>
		<td>read/write Profile document data, limited to Activities and Actors 
			associated with the current token to the extent it is 
			possible to determine this relationship.
		</td>
	</tr>
	<tr id="4.2.s2.table1.row6"><td>all/read</td><td>unrestricted read access</td></tr>
	<tr id="4.2.s2.table1.row7"><td>all</td><td>unrestricted access</td></tr>
</table>

###### <a name="4.2.s3"></a>OAuth Resources
<table>
	<tr>
		<th>Name</th>
		<th>Endpoint</th>
		<th>Example</th>
	</tr>
	<tr id="4.2.s3.table1.row1">
		<td>Temporary Credential Request</td>
		<td>OAuth/initiate</td>
		<td>http://example.com/xAPI/OAuth/initiate</td>
	</tr>
	<tr id="4.2.s3.table1.row2">
		<td>Resource Owner Authorization</td>
		<td>OAuth/authorize</td>
		<td>http://example.com/xAPI/OAuth/authorize</td>
	</tr>
	<tr id="4.2.s3.table1.row3">
		<td>Token Request</td>
		<td>OAuth/token</td>
		<td>http://example.com/xAPI/OAuth/token </td>
	</tr>
</table>

##### <a name="4.2.s4"></a>Example
The list of scopes determines the set of permissions that is being requested. For example, an instructor might grant 
"statements/read" to an application (Client), but the LRS would still limit that tool to Statements that the instructor could 
read if querying the LRS with their credentials directly (such as Statements relating to their students).

##### <a name="4.2.s5"></a>Requirements

* <a name="4.2.s5.b1"></a>The LRS MUST accept a scope parameter as defined in [OAuth 2.0](http://tools.ietf.org/html/rfc6749#section-3.3).
* <a name="4.2.s5.b2"></a>The LRS MUST assume a requested scope of "statements/write" and "statements/read/mine" if no 
scope is specified.
* <a name="4.2.s5.b3"></a>The LRS MUST support the scope of "all" as a minimum.
* <a name="4.2.s5.b4"></a>The LRS MAY support other scopes.
* <a name="4.2.s5.b5"></a>The Client SHOULD request only the minimal needed scopes, to increase the chances that the 
request will be granted.
* <a name="4.2.s5.b6"></a>The parameters "consumer_name" and "scope" are not part of OAuth 1.0, and therefore if used MUST be passed 
as query string or form parameters, not in the OAuth header.

<a name="security"/>

## <a name="5.0">5.0</a> Security 

Security beyond authentication (including the interpretation of OAuth authorization scopes) is beyond the current 
scope of this document and left to the individual LRS provider as an implementation detail. Implementors are encouraged 
to follow industry best practices, e.g., [The HTTPS-Only Standard](https://https.cio.gov) from the office of the White House CIO.

It is possible that security concerns may arise in the implementation of this specification, and implementers might choose to break a 
conformance requirement for the sake of security. In these cases, implementers are encouraged to consider both the security and 
interoperability implications of their implementation decisions. In any case, the LRS will still need to be configurable such that it
is able to pass conformance tests. 

While other security concerns are beyond the scope of this specification, the xAPI Community remains dedicated to determining 
security best practices. This effort has begun at [xAPIsec](https://github.com/xapisec/xapisec). 
Participation is highly encouraged.

<a name="append3"/>
## <a name="5.0.s1"></a>Appendices

<a name="Appendix3A"/>

### <a name="A">Appendix A</a>: Converting Statements to 1.0.0

###### <a name="A.s1"></a>Rationale
This is a 1.0.0 specification, and as such implementers do not have to consider prior versions of the specification. 
However, prior versions did see notable adoption. This data conversion is specified in order to preserve the data 
tracked using earlier versions, and make it available to new implementers in a consistent manner.

###### <a name="A.s2"></a>Details

###### <a name="A.s3"></a>Conversion of Statements created based on version 0.9

A 1.0.0 Client or other system converting a Statement created in 0.9 MUST follow the steps below:

* <a name="A.s3.b1"></a>If the Statement has been voided or uses Verbs, Activity types, or properties not included in the
 0.9 specification, do not convert it.
* <a name="A.s3.b2"></a>Prefix "verb" with `http://adlnet.gov/expapi/verbs/`.
* <a name="A.s3.b3"></a>Prefix any Activity ids which are not full absolute IRIs with `tag:adlnet.gov,2013:expapi:0.9:activities:`
* <a name="A.s3.b4"></a>Prefix any extension keys which are not full absolute IRIs with `tag:adlnet.gov,2013:expapi:0.9:extensions:`
* <a name="A.s3.b5"></a>Prefix Activity types with `http://adlnet.gov/expapi/activities/`
* <a name="A.s3.b6"></a>for each Agent (Actor):
    * <a name="A.s3.b6.b1"></a>Search for Inverse Functional Identifiers in this order: "mbox, mbox_sha1sum, openid,
    account". Keep the first populated Inverse Functional Identifier found and discard the rest.
    * <a name="A.s3.b6.b2"></a>For the above Inverse Functional Identifier, take the first element in the array and
    use that as the value of that Inverse Functional Identifier property, discarding any
    remaining elements.
    * <a name="A.s3.b6.b3"></a>If the "name" property is present, set it equal to the first element in the "name"
    array, discard the remaining elements.
    * <a name="A.s3.b6.b4"></a>Remove all remaining properties.
* <a name="A.s3.b7"></a>Remove the "voided" property from the Statement, if present. Remember, if the value of the
  voided property is `true`, then the Statement MUST NOT be converted.
* <a name="A.s3.b8"></a>Add `version": "1.0.0`
* <a name="A.s3.b9"></a>If an authority was not previously set, set the authority to an Agent identified by an account 
with a homePage set to the home page corresponding to the system performing the conversion and an accountName of `unknown`.
* <a name="A.s3.b10"></a>If the "statement" property in Context was set, remove it from the Statement.
* <a name="A.s3.b11"></a>Preserve all other properties without modification, including the "stored" property. The "stored" 
property will still be updated if the Statement is sent to an LRS.

###### <a name="A.s4"></a>Conversion of Statements created based on version 0.95

A 1.0.0 Client or other system converting a Statement created in 0.95 MUST follow the steps below:

* <a name="A.s4.b1"></a>If the Statement is voided, do not convert it.
* <a name="A.s4.b2"></a>Remove the "voided" property from the Statement, if present. Remember, if the value of the "voided" 
property is `true`, then the Statement MUST NOT be converted.
* <a name="A.s4.b3"></a>Add `version": "1.0.0`
* <a name="A.s4.b4"></a>If an authority was not previously set, set the authority to an Agent identified by an account 
with a homePage set to the home page corresponding to the system performing the conversion and an accountName of `unknown`.
* <a name="A.s4.b5"></a>If the Statement property in Context was set to anything other than a StatementRef, 
remove it from the Statement.
* <a name="A.s4.b6"></a>Preserve all other properties without modification, including the "stored" property. The "stored" 
property will still be updated if the Statement is sent to an LRS.


###### <a name="A.s5"></a>Example


A 0.9 Statement:
```
{
    "id": "d1eec41f-1e93-4ed6-acbf-5c4bd0c24269",
    "actor": {
        "objectType": "Person",
        "name": [
            "Joe Schmoe",
            "Joseph Schmoseph"
        ],
        "mbox": [
            "mailto:joe@example.com"
        ],
        "openid": [
            "http://openid.com/joe-schmoe"
        ]
    },
    "verb": "completed",
    "inProgress": false,
    "object": {
        "objectType": "Activity",
        "id": "http://www.example.com/activities/001",
        "definition": {
            "name": {
                "en-US": "Example Activity"
            },
            "type": "course"
        }
    },
    "result": {
        "completion": true
    },
    "context": {
        "instructor": {
            "objectType": "Person",
            "lastName": [
                "Dad"
            ],
            "firstName": [
                "Joe's"
            ],
            "mbox": [
                "mailto:joesdad@example.com"
            ]
        },
        "contextActivities": {
            "parent": {
                "objectType": "Activity",
                "id": "non-absolute-activity-id",
                "definition": {
                    "name": {
                        "en-US": "Another Activity"
                    }
                }
            }
        }
    },
    "timestamp": "2012-06-01T19:09:13.245Z",
    "stored": "2012-06-29T15:41:39.165Z"
}
```

Converted to 1.0.0:
```
{
    "version": "1.0.0",
    "id": "d1eec41f-1e93-4ed6-acbf-5c4bd0c24269",
    "actor": {
        "objectType": "Agent",
        "name": "Joe Schmoe",
        "mbox": "mailto:joe@example.com"
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/completed",
        "display": {
            "en-US": "completed"
        }
    },
    "object": {
        "objectType": "Activity",
        "id": "http://www.example.com/activities/001",
        "definition": {
            "name": {
                "en-US": "Example Activity"
            },
            "type": "http://adlnet.gov/expapi/activities/course"
        }
    },
    "result": {
        "completion": true
    },
    "context": {
        "instructor": {
            "objectType": "Agent",
            "mbox": "mailto:joesdad@example.com"
        },
        "contextActivities": {
            "parent": [
                {
                    "objectType": "Activity",
                    "id": "tag:adlnet.gov,2013:expapi:0.9:activities:non-absolute-activity-id",
                    "definition": {
                        "name": {
                            "en-US": "Another Activity"
                        }
                    }
                }
            ]
        }
    },
    "timestamp": "2012-06-01T19:09:13.245Z",
    "stored": "2012-06-29T15:41:39.165Z",
    "authority": {
        "objectType": "Agent",
        "account": {
            "homePage": "http://www.example.com",
            "name": "unknown"
        }
    }
}
```


<a name="Appendix3B"/>

### <a name="B">Appendix B</a>: Table of All Resources

### <a name="B.s1"></a>Required Resources
<table>
	<tr>
		<th>Base Resource Endpoint of the LRS Precedes Each Endpoint</th>
		<th>Function</th>
	</tr>
	<tr id="B.s1.table1.row1">
		<td>statements</td>
		<td>Statement Storage/Retrieval</td>
	</tr>
	<tr id="B.s1.table1.row2">
		<td>agents</td>
		<td>Agent Object Storage/Retrieval</td>
	</tr>
	<tr id="B.s1.table1.row3">
		<td>agents/profile</td>
		<td>Agent Profile Resource</td>
	</tr>
	<tr id="B.s1.table1.row4">
		<td>activities</td>
		<td>Activity Object Storage/Retrieval</td>
	</tr>
	<tr id="B.s1.table1.row5">
		<td>activities/profile</td>
		<td>Activity Profile Resource</td>
	</tr>
	<tr id="B.s1.table1.row6">
		<td>activities/state</td>
		<td>State Resource</td>
	</tr>
	<tr id="B.s1.table1.row7">
		<td>about</td>
		<td>LRS Information</td>
	</tr>
</table>

### <a name="B.s2"></a>OAuth Resources
<table>
	<tr>
		<th>Base Resource Endpoint of the LRS Precedes Each Endpoint</th>
		<th>Function</th>
	</tr>
	<tr id="B.s2.table1.row1">
		<td>OAuth/initiate</td>
		<td>Temporary Credential Request</td>
	</tr>
	<tr id="B.s2.table1.row2">
		<td>OAuth/authorize</td>
		<td>Resource Owner Authorization</td>
	</tr>
	<tr id="B.s2.table1.row3">
		<td>OAuth/token</td>
		<td>Token Request</td>
	</tr>
</table>

<a name="Appendix3C"/>

### <a name="C">Appendix C</a>: Cross Domain Request Example

[Alternate Request Syntax](#alt-request-syntax) outlines alternative syntax for use when the normal syntax cannot be used due 
to browser or querystring length restrictions. This appendix provides an example of a PUT request to the Statements Resource 
following this format. 

Request using normal syntax:

```
URL: http://example.com/xAPI/statements
Method: PUT

Query String Parameters:
    statementId=c70c2b85-c294-464f-baca-cebd4fb9b348

Request Headers:
    Accept:*/*
    Accept-Encoding:gzip, deflate, sdch
    Accept-Language:en-US,en;q=0.8
    Authorization: Basic VGVzdFVzZXI6cGFzc3dvcmQ=
    Content-Type: application/json
    X-Experience-API-Version: 1.0.3
    Content-Length: 351

Content:
{"id":"c70c2b85-c294-464f-baca-cebd4fb9b348","timestamp":"2014-12-29T12:09:37.468Z","actor":{"objectType":"Agent","mbox":"mailto:example@example.com","name":"Test User"},"verb":{"id":"http://adlnet.gov/expapi/verbs/experienced","display":{"en-US":"experienced"}},"object":{"id":"http://example.com/xAPI/activities/myactivity","objectType":"Activity"}}

```

Request using alternative syntax:

```
URL: http://example.com/xAPI/statements?method=PUT&statementId=c70c2b85-c294-464f-baca-cebd4fb9b348
Method: POST

Request Headers:
    Accept:*/*
    Accept-Encoding:gzip, deflate, sdch
    Accept-Language:en-US,en;q=0.8
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 745

Content (with added line breaks and not URL encoded for readability):
    statementId=c70c2b85-c294-464f-baca-cebd4fb9b348
    &Authorization=Basic VGVzdFVzZXI6cGFzc3dvcmQ=
    &X-Experience-API-Version=1.0.3
    &Content-Type=application/json
    &Content-Length=351
    &content={"id":"c70c2b85-c294-464f-baca-cebd4fb9b348","timestamp":"2014-12-29T12:09:37.468Z","actor":{"objectType":"Agent","mbox":"mailto:example@example.com","name":"Test User"},"verb":{"id":"http://adlnet.gov/expapi/verbs/experienced","display":{"en-US":"experienced"}},"object":{"id":"http://example.com/xAPI/activities/myactivity","objectType":"Activity"}}
```
