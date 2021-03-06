---
description: 'Дополнительные сведения: Включение межбазовых доступа в SQL Server'
title: Организация межбазового доступа в SQL Server
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 4e818b4f0294fdc7edd351a1e60203357579a320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695870"
---
# <a name="enabling-cross-database-access-in-sql-server"></a>Организация межбазового доступа в SQL Server

Межбазовые цепочки владения возникают, когда процедура в одной базе данных зависит от объектов в другой базе данных. Межбазовая цепочка владения работает так же, как цепочка владения внутри единой базы данных, но для непрерывной цепочки владения необходимо, чтобы все владельцы объекта были сопоставлены с одной учетной записью входа. Если одна учетная запись входа является владельцем исходного объекта в исходной базе данных и целевых объектов в целевых базах данных, то SQL Server не проверяет наличие разрешений в целевых объектах.  
  
## <a name="off-by-default"></a>Отключено по умолчанию  

 Формирование межбазовых цепочек владения отключено по умолчанию. Майкрософт рекомендует отключить межбазовые цепочки владения, так как с ними связаны следующие угрозы безопасности:  
  
- Владельцы баз данных и члены ролей базы данных `db_ddladmin` или `db_owners` могут создавать объекты, владельцами которых являются другие пользователи. Эти объекты потенциально могут обращаться к объектам в другой базе данных. Это значит, что при включенных межбазовых цепочках владения этим пользователям необходимо полностью доверять при доступе к данным во всех базах данных.  
  
- Пользователи с разрешением CREATE DATABASE могут создавать новые базы данных и присоединять существующие базы данных. Если межбазовые цепочки владения включены, то эти пользователи могут обращаться к объектам в других базах данных, в которых у них нет прав доступа, из вновь созданных или присоединенных баз данных, которые они создали.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Включение межбазовых цепочек владения  

 Межбазовые цепочки владения нужно включать только в среде с привилегированными пользователями, имеющими полный уровень доверия. Их можно настроить во время установки всех баз данных или выборочно для определенных баз данных с помощью команд Transact-SQL `sp_configure` и `ALTER DATABASE`.  
  
 Для выборочной настройки межбазовых цепочек владения служит хранимая процедура `sp_configure`, с помощью которой эти цепочки отключаются для сервера. Затем с помощью команды ALTER DATABASE с параметром SET DB_CHAINING ON настраиваются межбазовые цепочки владения только в требуемых базах данных.  
  
 В следующем примере включены межбазовые цепочки владения для всех баз данных.  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 В следующем примере включены межбазовые цепочки владения для конкретных баз данных.  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Динамический SQL  

 Межбазовые цепочки владения неприменимы в тех случаях, когда выполняются динамически созданные инструкции SQL, если только один и тот же пользователь не присутствует в обеих базах данных. Это можно обойти в SQL Server, создав хранимую процедуру для доступа к данным другой базы данных и подписав эту процедуру сертификатом, существующим в обеих базах данных. Это дает пользователям доступ к ресурсам базы данных, используемым процедурой, без предоставления им разрешений или доступа к базе данных.  
  
## <a name="external-resources"></a>Внешние ресурсы  

 Для получения дополнительных сведений см. следующие ресурсы.  
  
|Ресурс|Описание|  
|--------------|-----------------|  
|[Расширение олицетворения базы данных с помощью параметра выполнить как](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) и [перекрестный межбазовые цепочки владения](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).|В статьях описано, как настроить межбазовые цепочки владения для экземпляра SQL Server.|  
  
## <a name="see-also"></a>См. также

- [Защита приложений ADO.NET](../securing-ado-net-applications.md)
- [Общие сведения о безопасности SQL Server](overview-of-sql-server-security.md)
- [Управление разрешениями с использованием хранимых процедур в SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Написание безопасного динамического кода SQL в SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Подписывание хранимых процедур в SQL Server](signing-stored-procedures-in-sql-server.md)
- [Общие сведения об ADO.NET](../ado-net-overview.md)
