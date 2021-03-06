---
description: 'Дополнительные сведения: конечная точка: Проверка безопасности и ошибки проверки подлинности'
title: 'Конечная точка: количество сбоев при проверке безопасности и проверке подлинности'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: 9131eebcf85032c591ebf7f65e2b0e5f67ec60df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655426"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Конечная точка: количество сбоев при проверке безопасности и проверке подлинности

Имя счетчика: Security Validation and Authentication Failures  
  
## <a name="description"></a>Описание  

 Значение этого счетчика увеличивается всякий раз, когда сообщение отклоняется из-за проблемы безопасности, не относящейся к счетчику "Security Calls Not Authorized". К таким проблемам относятся следующие.  
  
- Невозможно прочесть в этом сообщении маркер клиента.  
  
- Токен клиента не прошел проверку подлинности (неправильный пароль).  
  
- Сбой при проверке подписи (сообщение было изменено).  
  
- Сообщение является копией предыдущего, что может свидетельствовать об атаке воспроизведения.  
  
- Произошел сбой при расшифровке.  
  
- В сообщении отсутствуют некоторые обязательные элементы (отметка времени или зашифрованный блок данных).  
  
- Во время подтверждения TLSNEGO/SPNEGO произошли ошибки.
