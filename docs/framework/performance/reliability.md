---
title: Надежность
description: Общие сведения о надежности в .NET. Защита от асинхронных исключений в узлах, выполняемых в .NET, например SQL Server.
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
ms.openlocfilehash: 00af439a12476addbe564ecf81152a1bc435d637
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245605"
---
# <a name="reliability"></a>Надежность

Крайне важно обеспечить защиту кода, выполняющегося в серверных средах, таких как SQL Server, от асинхронных исключений. Вопросы, обсуждаемые в этой статье, относятся не только к SQL Server, но касаются общих принципов написания надежного кода для любого ведущего приложения, выполняющегося в среде .NET Framework версии 2.0. Тем не менее служба SQL Server приводится в качестве примера, поскольку именно в ней впервые стали широко использоваться новые возможности обеспечения надежности, представленные в версии 2.0.  
  
 В отношении кода, выполняемого в SQL Server, должны действовать более строгие правила надежности, чем для других серверных сред. Это связано с тем, что SQL Server постоянно функционирует на границе потребления ресурсов.  Исключения <xref:System.OutOfMemoryException> и <xref:System.Threading.ThreadAbortException> встречаются в среде SQL Server достаточно часто. Эти правила в целом ориентированы не столько на обеспечение надежности, сколько на гарантию корректного завершения сбоем полностью доверенного управляемого кода при повторном использовании на уровне <xref:System.AppDomain>, что является основным способом обеспечить согласованность и доступность сервера.  
  
## <a name="in-this-section"></a>в этом разделе  

 [программирование SQL Server и атрибуты защиты ведущего приложения](sql-server-programming-and-host-protection-attributes.md)  
 Описывает использование атрибута <xref:System.Security.Permissions.HostProtectionAttribute> в SQL Server для ограничения выполнения управляемого кода.  
  
 [Рекомендации по обеспечению надежности](reliability-best-practices.md)  
 Содержит рекомендации по написанию кода, отвечающего требованиям надежности.  
  
 [Области ограниченного выполнения](constrained-execution-regions.md)  
 Описывает функции и поведения областей ограниченного выполнения (CER).  
  
## <a name="reference"></a>Справочник  

 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
