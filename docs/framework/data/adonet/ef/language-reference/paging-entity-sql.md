---
description: 'Дополнительные сведения: разбиение на страницы (Entity SQL)'
title: Разбивка на страницы (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: c32474b772be359dbf2ffd46e5489cc0b4b2abb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791859"
---
# <a name="paging-entity-sql"></a>Разбивка на страницы (Entity SQL)

Физическое разбиение на страницы может быть выполнено с помощью вложенных предложений [Skip](skip-entity-sql.md) и [Limit](limit-entity-sql.md) в предложении [ORDER BY](order-by-entity-sql.md) . Для детерминированного физического разбиения на страницы необходимо использовать предложения SKIP и LIMIT. Если требуется ограничить количество строк в результате недетерминированным способом, следует использовать [Top](top-entity-sql.md). Предложения TOP и SKIP/LIMIT являются взаимоисключающими.  
  
## <a name="top-overview"></a>Общие сведения о предложении TOP  

 Предложение SELECT может иметь необязательное вложенное предложение TOP, которое следует за необязательным модификатором ALL/DISTINCT. Предложение TOP указывает, что в результатах запроса возвращается только набор первых строк. Дополнительные сведения см. в разделе [Top](top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Общие сведения о предложениях SKIP и LIMIT  

 Предложения SKIP и LIMIT являются частью предложения ORDER BY. Если в предложении ORDER BY имеется вложенное предложение SKIP, результаты будут отсортированы в соответствии со спецификацией сортировки, а результирующий набор будет включать строку или строки, начиная со строки, следующей непосредственно за значением выражения SKIP. Например, SKIP 5 пропустит первые пять строк и возвратит все, начиная с шестой. Если в предложении ORDER BY имеется подчиненное выражение LIMIT, результаты запроса будут отсортированы в соответствии со спецификацией сортировки, а количество строк в наборе будет ограничено выражением LIMIT. Например, LIMIT 5 ограничит результирующий набор пятью экземплярами строк. Предложения SKIP и LIMIT необязательно использовать вместе: в предложение ORDER BY можно включить только SKIP или только LIMIT. Дополнительные сведения см. в следующих разделах:  
  
- [СРАЗУ](skip-entity-sql.md)  
  
- [Размер](limit-entity-sql.md)  
  
- [ORDER BY](order-by-entity-sql.md)  
  
## <a name="see-also"></a>См. также

- [Справочник по Entity SQL](entity-sql-reference.md)
- [Общие сведения об Entity SQL](entity-sql-overview.md)
- [Практическое руководство. Разбивка на страницы результатов запроса](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
