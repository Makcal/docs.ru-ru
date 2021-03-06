---
description: 'Узнайте подробнее о: Сериализация'
title: Сериализация
ms.date: 10/22/2008
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
ms.openlocfilehash: a12163c01da2f9eed19de05b0434c02d05ca99b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713303"
---
# <a name="serialization"></a>Сериализация

Сериализация представляет собой процесс преобразования объекта в формат, подготовленный для сохранения и передачи. Например, можно сериализовать объект и передать его по Интернету с использованием протокола HTTP и десериализировать его на компьютере назначения.

 Платформа .NET Framework предусматривает три основные технологии сериализации, оптимизированные для различных сценариев сериализации. В следующей таблице описаны эти технологии, а также связанные с ними основные типы Framework.

|**Имя технологии**|**Основные типы**|**Сценарии**|
|-------------------------|--------------------|-------------------|
|**Сериализация контрактов данных**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Общее сохранение<br />Веб-службы<br />JSON|
|**XML-сериализация**|<xref:System.Xml.Serialization.XmlSerializer>|Формат XML с полным контролем над формой XML-кода|
|**Сериализация времени выполнения (двоичная и SOAP-сериализация)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Удаленное взаимодействие .NET|

 ✔️ Разработка новых типов ДОЛЖНА производиться с учетом сериализации.

## <a name="choosing-the-right-serialization-technology-to-support"></a>Правильный выбор сериализации для поддержки

 ✔️ Если экземпляры типа необходимо сохранять или использовать в веб-службах, РЕКОМЕНДУЕТСЯ выбрать поддержку сериализации контракта данных.

 ✔️ Если требуется дополнительный контроль над XML-форматом, создаваемым при сериализации типа, РЕКОМЕНДУЕТСЯ выбрать поддержку XML-сериализации вместо сериализации контракта данных или в дополнение к ней.

 Поддержка этой технологии может потребоваться в определенных сценариях взаимодействий, где необходимо использование конструкций XML, неподдерживаемых при сериализации контракта данных, например при создании XML-атрибута.

 ✔️ Если экземпляры типа должны передаваться за пределы границ архитектуры удаленного взаимодействия .NET, РЕКОМЕНДУЕТСЯ выбрать поддержку сериализации среды выполнения.

 ❌ НЕ рекомендуется выбирать сериализацию среды выполнения или XML-сериализацию для использования общих преимуществ, обеспечиваемых сохранением. Вместо этого рекомендуется использовать сериализацию контракта данных.

## <a name="supporting-data-contract-serialization"></a>Поддержка сериализации контракта данных

 Типы могут поддерживать сериализацию контракта данных при применении <xref:System.Runtime.Serialization.DataContractAttribute> к типу и применении <xref:System.Runtime.Serialization.DataMemberAttribute> к элементам (полям и свойствам) типа.

 ✔️ РЕКОМЕНДУЕТСЯ пометить элементы данных типа как открытые, если тип может быть использован в среде с частичным доверием.

 В среде с полным доверием сериализаторы контрактов данных могут выполнять сериализацию и десериализацию закрытых типов и элементов, но в среде с частичным доверием эти операции могут выполняться только для открытых элементов.

 ✔️ НЕОБХОДИМО реализовать метод считывания и метод задания для всех свойств, имеющих <xref:System.Runtime.Serialization.DataMemberAttribute>. При использовании сериализаторов контрактов данных тип считается сериализуемым только при наличии обоих методов - считывания и задания. (В платформе .NET Framework 3.5 с пакетом обновления 1 (SP1) некоторые свойства коллекции могут быть доступны только для получения.) Если тип не будет использоваться в среде с частичным доверием, то один или несколько методов доступа к свойству могут быть закрытыми.

 ✔️ РЕКОМЕНДУЕТСЯ для инициализации десериализованных экземпляров использовать обратные вызовы сериализации.

 При десериализации объектов конструкторы не вызываются. (Существуют исключения из правил. Конструкторы коллекций, помеченные <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, вызываются во время десериализации.) Следовательно, любая логика, выполняемая при нормальном построении, должна быть реализована как один из обратных вызовов сериализации.

 `OnDeserializedAttribute` является наиболее часто используемым атрибутом обратного вызова. Кроме того, в семейство входят атрибуты <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute> и <xref:System.Runtime.Serialization.OnSerializedAttribute>. Их можно использовать для пометки обратных вызовов, которые выполняются перед десериализацией, перед сериализацией и после сериализации соответственно.

 ✔️ РЕКОМЕНДУЕТСЯ использовать <xref:System.Runtime.Serialization.KnownTypeAttribute> для указания конкретных типов, которые должны использоваться при десериализации более сложного графа объекта.

 ✔️ При создании и изменении сериализуемых типов РЕКОМЕНДУЕТСЯ обеспечивать прямую и обратную совместимость.

 Необходимо помнить, что сериализуемые потоки будущих версий типа могут быть десериализованы в текущую версию типа и наоборот.

 Необходимо учитывать, что элементы данных, даже закрытые и внутренние, не могут изменять свои имена, типы и даже свой порядок в будущих версиях типов, если не предприняты специальные меры для сохранения контракта с помощью явных параметров в его атрибутах.

 При изменении сериализуемых типов проверьте совместимость сериализации. Попробуйте десериализовать новую версию в предыдущую и наоборот.

 ✔️ РЕКОМЕНДУЕТСЯ реализовать <xref:System.Runtime.Serialization.IExtensibleDataObject>. Это даст возможность обеспечить цикл обработки значений между различными версиями типа.

 Интерфейс дает сериализатору гарантию отсутствия потерь данных при выполнении циклов обработки значений. Свойство <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> используется для сохранения любых данных из будущих версий типа, неизвестных текущей версии. Таким образом оно не может сохранить их в элементах данных. Если текущая версия затем сериализуется и десериализуется в будущую, то дополнительные данные будут доступны в сериализованном потоке.

## <a name="supporting-xml-serialization"></a>Поддержка XML-сериализации

 Сериализация контрактов данных является основной (задаваемой по умолчанию) технологией сериализации в .NET Framework, однако существуют сценарии сериализации, которые эта технология не поддерживает. Например, она не обеспечивает полный контроль над формой XML-кода, создаваемого или используемого сериализатором. Если необходим столь высокий уровень контроля, используйте XML-сериализацию, разработав типы для поддержки этой технологии сериализации.

 ❌ Необходимо ИЗБЕГАТЬ разработки типов специально для XML-сериализации, за исключением случаев, когда необходим контроль над формой создаваемого XML-кода. Эта технология сериализации была заменена сериализацией контракта данных, описанной в предыдущем разделе.

 ✔️ РЕКОМЕНДУЕМ использовать реализацию интерфейса <xref:System.Xml.Serialization.IXmlSerializable>, если необходим более высокий уровень контроля над формой сериализуемого XML-кода, чем тот, который обеспечивается при применении атрибутов XML-сериализации. Два метода интерфейса, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> и <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, обеспечивают полный контроль над сериализуемым потоком XML. При этом обеспечивается возможность контроля над схемой XML, которая создается для типа путем применения `XmlSchemaProviderAttribute`.

## <a name="supporting-runtime-serialization"></a>Поддержка сериализации во время выполнения

 Сериализация во время выполнения представляет собой технологию, используемую при удаленном взаимодействии .NET. Если планируется передача типов с использованием удаленного взаимодействия .NET, то необходимо убедиться, что они поддерживают сериализацию во время выполнения.

 Базовая поддержка сериализации во время выполнения может быть обеспечена с помощью <xref:System.SerializableAttribute>. При более сложных сценариях выполняется реализация простого шаблона сериализации во время выполнения (реализация <xref:System.Runtime.Serialization.ISerializable> и обеспечение конструктора сериализации).

 ✔️ РЕКОМЕНДУЕТСЯ обеспечить для типов поддержку сериализации во время выполнения, если типы будут использоваться при удаленном взаимодействии .NET. Например, в пространстве имен <xref:System.AddIn?displayProperty=nameWithType> используется удаленное взаимодействие .NET и поэтому все типы, передаваемые между надстройками `System.AddIn`, должны поддерживать сериализацию во время выполнения.

 ✔️ РЕКОМЕНДУЕТСЯ реализовать шаблон сериализации во время выполнения, если требуется полный контроль над процессом сериализации. Например, в том случае, когда необходимо преобразовать сериализуемые или десериализуемые данные.

 Шаблон очень прост. Нужно всего лишь реализовать интерфейс <xref:System.Runtime.Serialization.ISerializable> и предусмотреть специальный конструктор, который будет использоваться при десериализации объекта.

 ✔️ СДЕЛАЙТЕ конструктор сериализации защищенным и принимающим два параметра, типы и имена которых точно совпадают с показанными в этом образце.

```csharp
[Serializable]
public class Person : ISerializable
{
    protected Person(SerializationInfo info, StreamingContext context)
    {
        // ...
    }
}
```

 ✔️ Элементы <xref:System.Runtime.Serialization.ISerializable> НЕОБХОДИМО реализовать явно.

 ✔️ К реализации <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> НЕОБХОДИМО применить запрос ссылки. Это гарантирует, что доступ к элементу имеют только полностью доверенный сериализатор и ядро.

 *Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*

 *Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*

## <a name="see-also"></a>См. также

- [Рекомендации по проектированию на основе Framework](index.md)
- [Правила использования](usage-guidelines.md)
