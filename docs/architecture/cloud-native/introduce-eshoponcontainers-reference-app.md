---
title: Введение в Справочное приложение eShopOnContainers
description: Общие сведения о приложении для ASP.NET Core и Azure, встроенном в облачные микрослужбы.
ms.date: 01/19/2021
ms.openlocfilehash: 35aa92794d8488c3de60f42af52654c4c26aad82
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505678"
---
# <a name="introducing-eshoponcontainers-reference-app"></a>Введение в Справочное приложение eShopOnContainers

Корпорация Майкрософт, в связи с ведущими экспертами сообщества, создала полнофункциональное облачное приложение-Справочник по микрослужбам, eShopOnContainers. Это приложение предназначено для демонстрации использования .NET и DOCKER, а также, при необходимости, Azure, Kubernetes и Visual Studio, для создания Интернет-магазина.

![Снимок экрана примера приложения eShopOnContainers.](./media/eshoponcontainers-sample-app-screenshot.png)

**Рис. 2-1**. Снимок экрана примера приложения eShopOnContainers.

Перед началом этой главы рекомендуется скачать [эталонное приложение eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers). В этом случае вам будет проще следовать представленной информации.

## <a name="features-and-requirements"></a>Функции и требования

Начнем с рассмотрения функций и требований приложения. Приложение eShopOnContainers представляет собой Интернет-магазин, который продает различные физические продукты, такие как t-рубашки и кофе кружки. Если вы уже приобрели что-то еще до этого, работа с магазином должна быть относительно знакома. Ниже приведены некоторые основные функции, реализуемые хранилищем.

- Список элементов каталога
- Фильтровать элементы по типу
- Фильтровать элементы по фирменной символике
- Добавление элементов в корзину покупок
- Изменение или удаление элементов из корзины
- Извлечение
- Регистрация учетной записи
- Войти
- Выйти
- Обзор заказов

Приложение также имеет следующие нефункциональные требования:

- Он должен быть высокодоступным, и его необходимо автоматически масштабировать, чтобы обеспечить соответствие увеличенному объему трафика (и масштабировать диск, когда он проходит в сторону).
- Он должен обеспечивать простой в использовании Мониторинг журнала работоспособности и диагностики, чтобы помочь в устранении возникающих проблем.
- Он должен поддерживать гибкий процесс разработки, включая поддержку непрерывной интеграции и развертывания (CI/CD).
- В дополнение к двум внешним веб-интерфейсам (традиционным и одностраничным приложениям) приложение также должно поддерживать мобильные клиентские приложения, работающие под управлением разных типов операционных систем.
- Она должна поддерживать кросс-платформенное размещение и межплатформенную разработку.

![архитектура разработки эталонного приложения eShopOnContainers.](./media/eshoponcontainers-development-architecture.png)

**Рис. 2-2**. архитектура разработки эталонного приложения eShopOnContainers.

Приложение eShopOnContainers доступно для мобильных и веб-клиентов, которые обращаются к приложению по протоколу HTTPS, предназначенному для приложения ASP.NET Core MVC Server или соответствующего шлюза API. Шлюзы API предлагают несколько преимуществ, таких как отделение серверных служб от отдельных клиентских клиентов и обеспечение лучшей безопасности. Приложение также использует связанный шаблон, известный как серверные части для внешних интерфейсов (БФФ), которые рекомендуют создавать отдельные шлюзы API для каждого клиентского клиента. Эталонная архитектура демонстрирует разделение шлюзов API в зависимости от того, поступает ли запрос из Интернета или с мобильного клиента.

Функциональные возможности приложения разбиваются на множество разных микрослужб. Существуют службы, отвечающие за проверку подлинности и идентификацию, список элементов из каталога продуктов, управление корзинами покупок пользователей и размещение заказов. Каждая из этих отдельных служб имеет собственное постоянное хранилище. Основного хранилища данных, с которым взаимодействуют все службы, нет. Вместо этого координация и взаимодействие между службами выполняются по мере необходимости и с помощью шины сообщений.

Каждая из разных микрослужб разработана по-разному в зависимости от их индивидуальных требований. Этот аспект означает, что их технологический стек может отличаться, хотя все они созданы с помощью .NET и предназначены для облака. Более простые службы предоставляют базовые хранилища данных с созданием операций создания, чтения и удаления (CRUD), в то время как более сложные службы используют Domain-Driven подходов к проектированию и закономерности для управления сложными бизнес-процессами.

![Различные виды микрослужб](./media/different-kinds-of-microservices.png)

**Рис. 2-3**. Различные виды микрослужб.

## <a name="overview-of-the-code"></a>Общие сведения о коде

Так как в нем используются микрослужбы, приложение eShopOnContainers включает в себя несколько отдельных проектов и решений в своем репозитории GitHub. В дополнение к отдельным решениям и исполняемым файлам, различные службы предназначены для работы внутри собственных контейнеров как во время локальной разработки, так и во время выполнения в рабочей среде. На рис. 2-4 показано полное решение Visual Studio, в котором организованы различные проекты.

![Проекты в решении Visual Studio.](./media/projects-in-visual-studio-solution.png)

**Рис. 2-4**. Проекты в решении Visual Studio.

Код организован для поддержки различных микрослужб, и в каждой микрослужбе код разбивается на логику домена, проблемы с инфраструктурой, Пользовательский интерфейс или конечную точку службы. Во многих случаях зависимости каждой службы могут быть выполнены службами Azure в рабочей среде и альтернативными вариантами для локальной разработки. Давайте рассмотрим, как требования приложения сопоставляются со службами Azure.

## <a name="understanding-microservices"></a>Общие сведения о микрослужбах

Эта книга посвящена собственным облачным приложениям, созданным с помощью технологии Azure. Дополнительные сведения о рекомендациях по работе с микрослужбами и проектировании приложений на основе микрослужб см. в сопроводительной книге, [микрослужбах .NET: архитектура для контейнерных приложений .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook).

>[!div class="step-by-step"]
>[Назад](candidate-apps.md)
>[Вперед](map-eshoponcontainers-azure-services.md)
