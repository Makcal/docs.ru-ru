---
description: 'Дополнительные сведения о методе: IGCThreadControl:: Среадисблоккингфорсуспенсион'
title: Метод IGCThreadControl::ThreadIsBlockingForSuspension
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: 13023a75ab1c438abebbeb16fd9fe7c4b95c37ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709208"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a>Метод IGCThreadControl::ThreadIsBlockingForSuspension

Уведомляет узел о том, что поток, выполняющий вызов, будет заблокирован, возможно, для сборки мусора или другой приостановки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a>Remarks  

 Основное приложение может выбрать в `ThreadIsBlockingForSuspension` обратном вызове, следует ли перепланировать поток.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE. h  
  
 **Библиотека:** Включается в качестве ресурса в MSCorEE.dll  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс IGCThreadControl](igcthreadcontrol-interface.md)
