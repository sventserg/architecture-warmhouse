# Project_template

Это шаблон для решения проектной работы. Структура этого файла повторяет структуру заданий. Заполняйте его по мере работы над решением.

# Задание 1. Анализ и планирование

<aside>

Чтобы составить документ с описанием текущей архитектуры приложения, можно часть информации взять из описания компании и условия задания. Это нормально.

</aside

### 1. Описание функциональности монолитного приложения

**Управление отоплением:**

- Пользователи могут удалённо включать/выключать отопление в своих домах
- Система поддерживает управление отоплением через web-интерфейс
- Подключение к системе происходит с помощью выезда специалиста
- Самостоятельное подключение к системе пользователям не доступно

**Мониторинг температуры:**

- Пользователи могут просмартивать текущую температуру в своих домах через web-интерфейс
- Система поддерживает синхронную передачу данных
- Система получает данные о температуре с датчиков, установленных в домах
- Подключение датчиков происходит с помощью выезда специалиста
- Самостоятельное подключение датчиков к системе пользователям не доступно

### 2. Анализ архитектуры монолитного приложения

- Язык программирования: Go
- База данных: PostgreSQL
- Архитектура: Монолитная, все компоненты системы (обработка запросов, бизнес-логика, работа с данными) находятся в рамках одного приложения.
- Взаимодействие: Синхронное, запросы обрабатываются последовательно.
- Масштабируемость: Ограничена, так как монолит сложно масштабировать по частям.
- Развертывание: Требует остановки всего приложения.

### 3. Определение доменов и границы контекстов

- Домен "Управление устройствами", контекст "Включение/выключение системы отопления"
- Домен "Мониторинг температуры", контекст "Просмотр данных о температуре"
- Домен "Подключение устройств", контекст "Подключение нового устройства к системе"

### **4. Проблемы монолитного решения**

- Масштабируемость ограничена
- Развертывание требует остановки всего приложения
- Разработка замедлена
- Высокий риск ошибок

### 5. Визуализация контекста системы — диаграмма С4

[Диаграмма контекста](https://www.plantuml.com/plantuml/dpng/RP11RnGn38NlyolCd1Pfw5muSUfgYqGbG5MXwh7AphYxaH8xiXrQ_Zt9D2iYn2cH_TxdPr-hER4Sms3U0iAZa_Y5ioBizLRXm6JuQd3ZtKbS70RZ1CPmP3EEi7h1nJpJCBppj8IyOfO0PxEad-PPtClLoTiv7mjGbieYkreuplT-SRBoTuy9mtpu-E4kEBA7Rr_dwDHGIkdfm34nLKUg-OOx56NQLTG4uqDvnlBkeHQ0dy7EVNpzNJXnV7-nUL9p8MpUs_PlWDRw7-N7He4LV_a5jT26jyhkvI8fX7_b8qpZpUQ0wCYTC2BP18zuX7rAyCooPTO9Vc9CACwo52cJDnPFfpBc3VJq-TLsRVO4ZQarj7L6HL8M1KShdD5P8RJjePvSkAvMezzZQDVhqsUjYzLcVwDUKIY4YsbtXghk97ypjeczThX6MdCCVm00)

# Задание 2. Проектирование микросервисной архитектуры

В этом задании вам нужно предоставить только диаграммы в модели C4. Мы не просим вас отдельно описывать получившиеся микросервисы и то, как вы определили взаимодействия между компонентами To-Be системы. Если вы правильно подготовите диаграммы C4, они и так это покажут.

**Диаграмма контейнеров (Containers)**

[Диаграмма контейнеров](//www.plantuml.com/plantuml/png/ZPHFRvj04CNlV8gfJwdKn9UUUieVLsdLf7BYHZr6OnZRgy8ktHrgMLM-Uncm1p06zsApmtjFyvjbzpemUYwoD6B3AS5FzDaNLmJuuIvl2UwSPJIMFCmChZrcKSGk1tQmTCmkWyHuYjau6qNlZ8tJ8g72fx1XpiEdwTJZzcfjU5CiYq0-BjF8ybNiikcpYT4dxhkXdDBftSVBUOgMNnuVfXa69b-MNkzSbZihZbmwZERaWxCNBsNK1vZ8twJylm791hS2tZG0164NcBB9-sXHFLpeczBJg1O7LQIihxUki0dwtHaB_3tbkSdDFJ9jSLVhfCFvLzZNAXU0-bhohb38xftyVhRiTv0xOnbMpWEcQKKSmDFlWWA7iljEP25JDZ7AlaXgUtteNkDbZ805RnfDbVSccNsyHme1r_HKK44Ak2z2LOK5-JycfXvgszetQLlVSFKB9o90MxvlC4VRSjQmyyQkcwQqDDoHIhhwenbf9qmfPIJRaI1ZT-opPIjkXenB3DIDFLGbSku2hpqjdXvajIWLxVmnr1a9YsBMIwXRpCZo86sjR8IdpGFeIQKCFUOwGNaryWoh1keaXt3b-rHOMVmFgkWQcHhFOyh1waEAkuKeo_E04dMMRX6JHMzS3QBXX_8WeFegZfvj30_2NjNZrDGMgqQEy_Qo5JfwYw9dIlUtTkUw2sGJFTwbGMHjmV55rhsbkiRUbX_jcITCmdJh3LDdPyJQlWQQvm6pdj5sGlzerPM13FtsDQ6teOVrwGITiqOSZQvzrmvCkYlfdPXgIBbtAvFIgBDpYMQw6FMSk8hgcK2cjT60tlUl0sbSqNL9NMJfFm00)

**Диаграмма компонентов (Components)**

[Device Management Service](//www.plantuml.com/plantuml/png/dLF1ZjCm4BtxAqnEkn9iBfmuBMmHYzX2jmLnhDnaDhMmup8pPgbG_nqxSTsqQON4fQhVp7lpvjcv9LR8tXh1cWt8xmhjlVC4SWA_T0LogbhLW8MMvGAmW-wStRWs8XEj6bHM20DFBDb9rCsQPQqHAjQk5UA5RYlZQ_1ev9fvGs_A4jNpJQDvxLUU02lNSj2wgPmjvxfIMBlF6ZPWohlNhsP6jVnj-b1QHGmOe6MUVhE9jiLTu2lT0YxVET_M2hTNUOd5Dh3iIrb4HFPxzLXnBVy8AS-G-xqFQwUjWyZ5H4x5HXfdoSb8g7rmyRSlaQoxJYgkXvAJLHATA5OhHGC_UoHgp1nnWx1uV8Yd1JlCWh8EVPtexiZh58Z2t4SFFegce-pE0u-VrDCFDRI9yDC3SUzJx4JVkdp_cvDJoXQfCsCLifpavSJ_n_Kb1PwVmjNRsSUpf817nhrgQmCaRLSPMX-AB5YnfvwD1xaUbWdl303dL2bMJvLwPbmGdJ53iOnrGkcq5pkL-Ge6B31kGnzvs-baJEx1uOASg-csnwxci76asU7suEg05HcaJaAgAlmbQLoZgw2t4s8EvkJHnFIBGQYn8sAZ68hn1SJUKT_nJHGDCEMWn_F7CHKvXqiJqevxH_a6Kl-HWV60PEcVKqQ95mYgfl8PDQU04tNKUVorNoQElGsp6IIn3ptmRg6jlJL_0G00)
[Monitoring Service](https://www.plantuml.com/plantuml/png/dL9DRnCn4BtxLvWzfH9qBvmu5HhK8Xf84n37ojaTjXR-MCPZIeJotnat6oUxiJXmMCdxnk_Dc-Uv2gIGeZM2D1cGtnJQMny3o8LtcZngryaru2_TWBpsjlSE7CcvLXqgAmJvNfAN6q_ahMmrGaFQEo5UQDUOs4948n-9-l2chb4zNNQQ7kE66s3Z7R7MPUDjlTADmjP_qj23gQzVlreQvUZhugwsAX0WGm-v-sMV_8fhvYlj01_U-UXQXTjPTh_UCik-b5L2v7wWFLPTo3z2oaoUBI04rS5zX7Ya3Q1CQ6Oo_b5z_w7IOQ4SruD4-1aXKAWkMBJWw9ZY429ppvETcZgbPKj7LiX-RZwVcY4mO85mArj5QcnflZaHdNDveyB4p05DaaiVg4DOtz-blpNVAEll-1CxiNVvyFutpUQG9WhC6axF0bOXoG5WelYVKOUKyXxCtYu_Z6ypaAxUAjSQzcjpPV9EMM6rXvVeszW0ClTBdd6eoKCnAJ-V0qiZO54mq_SUnee3bYsM8os8hQ3t8Oso7UaTuMg4guPJ3jBuJZSikHDY1QQuw2d1Ae1hHvlCjukz2mjK8QWsr4-e2S9X1kQV9JiDPjBsNwonYw7bQQyqnPHPb3ypSLZMwWQey1WbJjdJ441HOMgjy123sqndvXKZqPg_)
[Scenario Service](https://www.plantuml.com/plantuml/png/bPD1RnCn48Nl-ok6FRKIP2-SE1KIYI9QI1CXZjN4EzrOtRN3pBXLXFhViTDuc-m6K0-HdEVvdb-UdGjHP0rTMwZLbk0dSdVfWn0i3Jbaws59_60DmTHt6-_8ASmiDenTKRHqfw0Us3PhXTeo6RNU5SKRwqmRQWhSmbfr8n-gYl5nqbXTXrMqP-ETHg-9yLsri0QvzjyiRQYjfk_VpLjq-kFwgkfGb3XAj_tfaqrAMqmZZzOHttxomTN8sxC--t8RgUujb4c1dGJFMdaElmk07Zwx9X5iw2PGUC7s8YIr9wF-5U_kiKm3wEA-0DElGA9IdYVJSQBSuRx2I0vR7GNgaHoc9wJFyVdxOOX-e4R5uoIpLUytYvihbACCMKjkSo_QC2rlhieqefvFMZ_5J_5K5AyDd7zdliMpZ_ClXxFnQnfSa27xG0AIDmOLPpo3b-ZgblZGQYybkzto5MvpzdKmntQBPmJoNlBThOK4Ek-iUhQkWNWKTBih0IR-vp4BsdX9tFRueAoMXp8QGoBG-iQQw1UxNr1xyjscIaiXLnyzp3IzAtjGsM1qFpbkuaJeaWdhbrRbh-muvUc0u-iSUcLEKUx_nuoILezibII_uWmFhsBqLpb9NyGSeMl_0000)
[User Management Service](//www.plantuml.com/plantuml/png/dL9DRzD04BtlhnXyQYM8Bvmu5HA98Xf84rKSgybwS5ViXvcTfOfG_plUs4xCAbouM9gtyvxVUxitKP0bEQl4Y2NuXknkGue43v4OrkYn9KTUO4VyosY2PN1Ty1bP6MmPdL8IEf00-o0I73I6IOi9NgbNnckR6afiuKcaY-_gcl5vqHfvIliKYNNmqcijT73rrcZa9dmnr96jbs_VR2nwULZVrGwZ4FVGu-dlYowRLikUZyOJFtu8oJV8XwjJXDsXPxdNK6K4XbG3Lbt3RmLmWPnJdqEFcNk9VxHH2XNyIyJ1G7_oCUJlS1GXbn6hwxdOQd-KMw7W7kF9nJHdzYP4QPbsztTvsadWKGeQ53pAlVpbRqqnOaltYL8M74SupZDld_7x3vpRO_gPAChWKBqezN-Hlqw5JTTuzNxpwGAbH_F-BVh6Jedc5cO2cPhDSB2MUD8w8rbdd6Oj5m9Rwa8q4lWmRndES3NXJSPHQueHR6YDhgvp7LkoHRSvM3Npd3SoLlYjZjdq042nN-mMJdjrR6Bzp4QAMy_SOdd-aWhcI58tv9lax1y0)


**Диаграмма кода (Code)**

[User Controller](//www.plantuml.com/plantuml/png/bL9DQyCm3BtxLsWvxOCc6-nKHYcaWnswChgL7OThYyHWMy5MDiROVryTqv92BZivxptfFKba6La6xfqLRDWYl5DmJzH7X5t4K9FdGDPYW9eqmih89aWd15C7JB0dPdAWJK35XhmG5yOhssliWuMMkOlpgWhogsmCj_t-u1iKUKRFfI9NROsIGTF6O8UsgkzdBrPwtZslAoSZOpXG7pMvZdpgwDAOGbaPup0T_0Y0crSEnZVWfSCHH2UDJNXj8ZyC6osWJKyyiIlyDEf0w_HcNhNIDvZCDzBXvTKvzvXCCocr7ampqcYHyKXaERkFzHFpUznYw9XQ8m-u9N8B24Gk9YvWKizJKiau8-5nGiBJ0TCNo27PvZ-RP6OoAKjltns2FdscJf5k2iLT0RCP5BTbULr0liWSMXadv6DCrdFjMK7UTmxvByGe4fxq61U99NhTE_i7)

# Задание 3. Разработка ER-диаграммы

[ER Диаграмма](//www.plantuml.com/plantuml/png/TPHHRzCm4CVVyobC7q5jcSHJXUX4YqIbKT3MYKVaEgVMaksBx3DG8RxxuZZPnLtsrhlx-_U_EyUz3IGzHMigqcH0_4Hlls8C81u3-0qwycWCUB716iHMovENjge86q4eZaY4LjJQWoADhghUQATCh25w8yv4JLWjbrx-MPmqdUEnvNhLCi7HGg5TtcibVOrx3GsOvUR3_8UHZXw_tIsj30I-JVtQe6tGfHDDQhDIHeRGTIV-LKAyspaIYRkhK_H0NhkJSDB2A0GhjKdndGxqiJtnIPpJaA7CrV1RgpRvVt3fDi4stPcnJyxiUpC6UKGxmjot8LDIiO2aHC7OTdrCz9CBZCg234inNHgEU2ifMh_qRSjQcdsqH_2SNdVBIvxWekqj3vTci6KR9gL4ce0xFO012-GlMqbokk7FY0Qa4pfyTodUOZmQM0i2su2N5Fs8zw30IQ-HKQ7FJCDu_l9c5BfQfqyrb7du2ofsUVRS35esVJw-gwT6AgUc8Ne6lS0SkaqEosP7tlU4d1VFbIq4vNMJVl80NuQX63NCEJq0ImQteJLcSMiidcYDArUjTIztTZCJyxcOlLyitixwPxOIPnccolaJVBNEtqPMP5eXoIzm9Ve_fr1ryRGBYtBcIbPUSNQy4jumBp-Sh1hQB85yvspzgfOlTAHb03TGW4SzC82r32wrrIsuEbhp1000)

# Задание 4. Создание и документирование API

### 1. Тип API

Async API имеет следующие преимущества:
- уменьшение нагрузки на сервер
- хорошая масштабируемость
- лучше подходит для работы с умными устройствами

### 2. Документация API

[Документация API](https://studio.asyncapi.com/?share=51cab963-c4bd-485c-9d31-8cb0fc8a94ba)

# Задание 5. Работа с docker и docker-compose

Перейдите в apps.

Там находится приложение-монолит для работы с датчиками температуры. В README.md описано как запустить решение.

Вам нужно:

1) сделать простое приложение temperature-api на любом удобном для вас языке программирования, которое при запросе /temperature?location= будет отдавать рандомное значение температуры.

Locations - название комнаты, sensorId - идентификатор названия комнаты

```
	// If no location is provided, use a default based on sensor ID
	if location == "" {
		switch sensorID {
		case "1":
			location = "Living Room"
		case "2":
			location = "Bedroom"
		case "3":
			location = "Kitchen"
		default:
			location = "Unknown"
		}
	}

	// If no sensor ID is provided, generate one based on location
	if sensorID == "" {
		switch location {
		case "Living Room":
			sensorID = "1"
		case "Bedroom":
			sensorID = "2"
		case "Kitchen":
			sensorID = "3"
		default:
			sensorID = "0"
		}
	}
```

2) Приложение следует упаковать в Docker и добавить в docker-compose. Порт по умолчанию должен быть 8081

3) Кроме того для smart_home приложения требуется база данных - добавьте в docker-compose файл настройки для запуска postgres с указанием скрипта инициализации ./smart_home/init.sql

Для проверки можно использовать Postman коллекцию smarthome-api.postman_collection.json и вызвать:

- Create Sensor
- Get All Sensors

Должно при каждом вызове отображаться разное значение температуры

Ревьюер будет проверять точно так же.


