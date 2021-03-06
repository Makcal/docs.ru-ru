---
description: 'Дополнительные сведения: использование настраиваемого действия'
title: Применение пользовательского действия
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: f036b3851878f83b461e6d692002501ea7d87649
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755113"
---
# <a name="using-a-custom-activity"></a>Применение пользовательского действия

Действия, которые являются производными от <xref:System.Activities.Activity> или его подклассов, можно составить в более крупные рабочие процессы или создать непосредственно в коде. В этом разделе описано, как использовать пользовательские действия в рабочих процессах, созданных в коде или в конструкторе.  
  
> [!NOTE]
> Пользовательские действия могут использоваться в том же проекте, в котором они определены, при условии, что как настраиваемое действие, так и действие, которое его использует, компилируются (т. е. загружается экземплярным типом, созданным в процессе сборки), если ссылающееся действие загружается динамически (например, с помощью ActivityXAMLServices), то указанная сборка должна быть размещена в другом проекте или XAML, созданный конструктором, необходимо изменить вручную, чтобы сделать это.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Использование пользовательского действия в проекте рабочего процесса  
  
1. Добавьте ссылку из базового проекта в проект библиотеки действий, где содержится пользовательское действие.  
  
2. Создайте решение.  
  
3. Для использования пользовательского действия в конструкторе выберите действие на панели инструментов и перетащите его на рабочую область.  
  
4. Для использования пользовательского действия в коде добавьте инструкцию Using, которая ссылается на проект пользовательского действия, и передайте новый экземпляр действия в <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
