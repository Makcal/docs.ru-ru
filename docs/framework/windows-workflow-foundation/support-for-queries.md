---
description: Дополнительные сведения см. в статье поддержка запросов.
title: Поддержка запросов
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 418e511e8b845653b9f3ec86d90c6cbfb25d5671
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755217"
---
# <a name="support-for-queries"></a>Поддержка запросов

Хранилище экземпляров рабочих процессов SQL записывает набор известных свойств в хранилище. Пользователи могут выполнить запрос экземпляров на основе этих свойств. В следующем списке приведены некоторые из этих известных свойств.  
  
- **Имя сайта.** Имя веб-узла, содержащего службу.  
  
- **Относительный путь приложения.** Путь приложения относительно веб-узла.  
  
- **Относительный путь службы.** Путь службы относительно приложения.  
  
- **Имя службы.** Имя службы.  
  
- **Пространство имен службы.** Имя пространства имен, которое использует служба.  
  
- **Текущий компьютер.**  
  
- **Последний компьютер**. Компьютер, на котором экземпляр службы рабочего процесса был запущен последний раз.  
  
> [!NOTE]
> Для резидентных сценариев, использующих узел службы рабочего процесса, заполняются только последние четыре свойства. Для сценариев приложения рабочего процесса заполняется только последнее свойство.  
  
 Среда выполнения рабочего процесса предоставляет значения для первых трех свойств. Узел службы рабочего процесса предоставляет значение для свойства **Причина приостановки** . Хранилище экземпляров рабочих процессов SQL предоставляет значения для **последнего обновленного свойства компьютера** .  
  
 Возможность хранилища экземпляров рабочих процессов SQL также позволяет указать пользовательские свойства, значения которых требуется сохранять в базе данных сохраняемости и которые будут в дальнейшем использованы в запросах. Дополнительные сведения о пользовательских рекламных акциях см. в разделе [Хранение расширяемости](store-extensibility.md).  
  
## <a name="views"></a>Представления  

 Хранилище экземпляров содержит следующие представления. Дополнительные сведения см. в разделе [схема базы данных сохраняемости](persistence-database-schema.md) .  
  
### <a name="the-instances-view"></a>Представление экземпляров  

 Представление экземпляров содержит следующие поля:  
  
1. **Id**  
  
2. **PendingTimer**  
  
3. **CreationTime**  
  
4. **LastUpdatedTime**  
  
5. **ServiceDeploymentId**  
  
6. **SuspensionExceptionName**  
  
7. **SuspensionReason**  
  
8. **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>Представление ServiceDeployments  

 Представление ServiceDeployments содержит следующие поля:  
  
1. **Значением**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **Служба**  
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>Представление InstancePromotedProperties  

 Представление InstancePromotedProperties содержит следующие поля. Дополнительные сведения о повышенных свойствах см. в статье о [расширении хранилища](store-extensibility.md) .  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **PromotionName**  
  
4. **Значение #** (диапазон полей от **Значение1** до **Value64**).
