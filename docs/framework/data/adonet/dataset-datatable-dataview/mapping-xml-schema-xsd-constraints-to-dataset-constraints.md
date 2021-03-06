---
description: 'Дополнительные сведения: сопоставление ограничений схемы XML (XSD) с ограничениями набора данных'
title: Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b1a958029e541b6ac95b5c509665005c9006adfa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651890"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных

Язык XSD позволяет задавать ограничения применительно к элементам и атрибутам, которые он определяет. При сопоставлении схемы XML с реляционной схемой в <xref:System.Data.DataSet> ограничения XML-схемы сопоставляются с соответствующими реляционными ограничениями для таблиц и столбцов в **наборе данных**.  
  
 В этом разделе рассматривается сопоставление следующих ограничений схемы XML:  
  
- Ограничение уникальности, заданное с помощью **уникального** элемента.  
  
- Ограничение Key, заданное с помощью элемента **Key** .  
  
- Ограничение keyref, заданное с помощью элемента **keyref** .  
  
 С помощью ограничения элемента или атрибута задаются определенные ограничения значений элемента в любом экземпляре документа. Например, ограничение ключа для дочернего элемента **CustomerID** элемента **Customer** в схеме указывает на то, что значения дочернего элемента **CustomerID** должны быть уникальными в любом экземпляре документа, и эти значения NULL не допускаются.  
  
 Ограничения также можно указывать между элементами и атрибутами документа для установления связи внутри документа. Ограничения key и keyref используются в схеме для указания ограничения внутри документа, что приводит к созданию связи между элементами и атрибутами документа.  
  
 Процесс сопоставления преобразует эти ограничения схемы в соответствующие ограничения для таблиц, созданных в **наборе данных**.  
  
## <a name="in-this-section"></a>В этом разделе  

 [Сопоставление уникальных ограничений XML-схемы (XSD) с ограничениями набора данных](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Описывает элементы XML-схемы, используемые для создания ограничений UNIQUE в **наборе данных**.  
  
 [Сопоставление ключевых ограничений XML-схемы (XSD) с ограничениями набора данных](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Описывает элементы XML-схемы, используемые для создания ограничений ключа (ограничения UNIQUE, в которых значения NULL не допускаются) в **наборе данных**.  
  
 [Сопоставление ограничений XML-схемы (XSD) keyref с ограничениями набора данных](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Описывает элементы XML-схемы, используемые для создания ограничений keyref (FOREIGN KEY) в **наборе данных**.  
  
## <a name="related-sections"></a>См. также  

 [Наследование реляционной структуры набора данных от схемы XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Описывает реляционную структуру или схему **набора данных** , созданного из схемы XSD.  
  
 [Создание отношений наборов данных из схемы XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Описывает элементы XML-схемы, используемые для создания связей между столбцами таблицы в **наборе данных**.  
  
## <a name="see-also"></a>См. также

- [Общие сведения об ADO.NET](../ado-net-overview.md)
