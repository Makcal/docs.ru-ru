---
description: 'Дополнительные сведения: служба: Проверка безопасности и ошибки проверки подлинности'
title: 'Служба: количество сбоев при проверке безопасности и проверке подлинности'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 8938c74e706526a02bf2ea5885951d067d6ebae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759488"
---
# <a name="service-security-validation-and-authentication-failures"></a>Служба: количество сбоев при проверке безопасности и проверке подлинности

Имя счетчика: Security Validation and Authentication Failures  
  
## <a name="description"></a>Описание  

 Значение этого счетчика увеличивается всякий раз, когда сообщение отклоняется из-за проблемы безопасности, не относящейся к счетчику "Security Calls Not Authorized". К таким проблемам относятся следующие.  
  
- Невозможно прочесть в этом сообщении маркер клиента.  
  
- Маркер клиента не прошел проверку подлинности (например, неправильный пароль).  
  
- Сбой при проверке подписи (например, сообщение было искажено).  
  
- Сообщение является копией предыдущего, что может свидетельствовать об атаке воспроизведения.  
  
- Произошел сбой при расшифровке.  
  
- В сообщении отсутствуют некоторые обязательные элементы (например, отсутствует отметка времени или зашифрованный блок данных).  
  
- Во время подтверждения TLSNEGO/SPNEGO произошли ошибки.
