---
description: 'Дополнительные сведения: тип ассоциации'
title: тип ассоциации
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 4df84d97c798e9f2d06e0f5dce442e05cb4c67b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697560"
---
# <a name="association-type"></a>тип ассоциации

*Тип ассоциации* (называемый также Ассоциацией) — это фундаментальный Стандартный блок для описания связей в EDM (EDM). В концептуальной модели Ассоциация представляет связь между двумя [типами сущностей](entity-type.md) (например `Customer` , и `Order` ). В приложении экземпляр ассоциации представляет собой специфическую ассоциацию (такую как ассоциация между экземпляром `Customer` и экземпляром `Order`). Экземпляры ассоциаций логически группируются в [набор ассоциаций](association-set.md).  
  
 Определение ассоциации содержит следующую информацию.  
  
- Уникальное имя. (обязательно)  
  
- Две [ассоциации завершаются](association-end.md), по одной для каждого типа сущности в связи. (обязательно)  
  
    > [!NOTE]
    > Ассоциация не может представлять связь между более чем двумя типами сущностей. Ассоциация может, тем не менее, определять связь с самим собой посредством указания одного и того же типа сущности для каждой из его конечных точек ассоциаций.  
  
- [Ограничение ссылочной целостности](referential-integrity-constraint.md). (необязательно)  
  
 Каждый элемент ассоциации должен указывать количество [элементов ассоциации](association-end-multiplicity.md) , которое указывает число экземпляров типа сущности, которые могут находиться на одном конце ассоциации. Кратность окончания ассоциации может иметь значение один (1), ноль или один (0.. 1) или многие ( \* ). Доступ к экземплярам типа сущности на одном конце ассоциации возможен через [Свойства навигации](navigation-property.md) или внешние ключи, если они представлены в типе сущности. Дополнительные сведения см. в разделе [EDM: внешние ключи](foreign-key-property.md).  
  
## <a name="example"></a>Пример  

 На приведенной ниже схеме показана концептуальная модель с двумя ассоциациями: `PublishedBy` и `WrittenBy`. Конечные точки ассоциации для ассоциации `PublishedBy` - это типы сущности `Book` и `Publisher`. Кратность `Publisher` конца равна единице (1), а кратность `Book` End — many ( \* ), что означает, что издатель публикует много книг, а книга публикуется одним издателем.  
  
 ![Пример модели с тремя типами сущностей](./media/association-type/example-model-three-entity-types.gif)  
  
 [Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей. Далее язык CSDL определяет ассоциацию `PublishedBy`, которая ранее приводилась в схеме.  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>См. также

- [Основные понятия модели EDM](entity-data-model-key-concepts.md)
- [EDM (модель данных с использованием сущностей)](entity-data-model.md)
