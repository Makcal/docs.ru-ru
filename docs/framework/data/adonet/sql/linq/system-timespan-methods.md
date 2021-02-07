---
description: Дополнительные сведения о методах System. TimeSpan
title: Методы System.TimeSpan
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: fa3192d18a59e589f2c7510776f8510b2c12cac4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681192"
---
# <a name="systemtimespan-methods"></a><span data-ttu-id="77cbb-103">Методы System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="77cbb-103">System.TimeSpan Methods</span></span>

<span data-ttu-id="77cbb-104">Поддержка элементов типа <xref:System.TimeSpan?displayProperty=nameWithType> в значительной степени зависит от используемых версий платформы .NET Framework и сервера Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="77cbb-104">Member support for <xref:System.TimeSpan?displayProperty=nameWithType> greatly depends on the versions of the .NET Framework and Microsoft SQL Server that you are using.</span></span>  
  
 <span data-ttu-id="77cbb-105">Если метод, оператор или свойство не поддерживаются, это означает, что LINQ to SQL не может перевести элемент для выполнения на SQL Server.</span><span class="sxs-lookup"><span data-stu-id="77cbb-105">When a method, operator, or property is unsupported; it means that LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="77cbb-106">Но эти элементы, тем не менее, можно использовать в коде.</span><span class="sxs-lookup"><span data-stu-id="77cbb-106">You may still be able to use these members in your code.</span></span> <span data-ttu-id="77cbb-107">Однако их следует вычислять до преобразования запроса в Transact-SQL или после получения результатов из базы данных.</span><span class="sxs-lookup"><span data-stu-id="77cbb-107">However, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="previous-limitations"></a><span data-ttu-id="77cbb-108">Предыдущие ограничения</span><span class="sxs-lookup"><span data-stu-id="77cbb-108">Previous Limitations</span></span>  

 <span data-ttu-id="77cbb-109">При использовании LINQ to SQL с версиями платформы .NET Framework, выпущенными до .NET Framework 3.5 с пакетом обновления 1 (SP1), невозможно сопоставлять поля баз данных SQL Server типу <xref:System.TimeSpan?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="77cbb-109">When using LINQ to SQL with versions of the .NET Framework prior to .NET Framework 3.5 SP1, you cannot map SQL Server database fields to <xref:System.TimeSpan?displayProperty=nameWithType>.</span></span> <span data-ttu-id="77cbb-110">При этом операции с типом <xref:System.TimeSpan> поддерживаются, поскольку значения <xref:System.TimeSpan> могут возвращаться операцией вычитания <xref:System.DateTime> или входить в выражение в виде литерала или привязанной переменной.</span><span class="sxs-lookup"><span data-stu-id="77cbb-110">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
## <a name="supported-systemtimespan-member-support"></a><span data-ttu-id="77cbb-111">Поддерживаемая поддержка членов System. TimeSpan</span><span class="sxs-lookup"><span data-stu-id="77cbb-111">Supported System.TimeSpan member support</span></span>

 <span data-ttu-id="77cbb-112">Следующие поддерживаемые в LINQ to SQL методы, операторы и свойства доступны для использования в запросах LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="77cbb-112">The following LINQ to SQL-supported methods, operators, and properties are available for you to use in your LINQ to SQL queries.</span></span> <span data-ttu-id="77cbb-113">После их сопоставления в модели объектов или внешнем файле сопоставления LINQ to SQL позволяет использовать многие элементы <xref:System.TimeSpan?displayProperty=nameWithType> внутри запросов LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="77cbb-113">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call many of the <xref:System.TimeSpan?displayProperty=nameWithType> members inside your LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="77cbb-114">Поддерживаемые методы <xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="77cbb-114">Supported <xref:System.TimeSpan> Methods</span></span>|<span data-ttu-id="77cbb-115">Поддерживаемые операторы <xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="77cbb-115">Supported <xref:System.TimeSpan> Operators</span></span>|<span data-ttu-id="77cbb-116">Поддерживаемые свойства <xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="77cbb-116">Supported <xref:System.TimeSpan> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
> <span data-ttu-id="77cbb-117">Чтобы сопоставлять тип <xref:System.TimeSpan?displayProperty=nameWithType> со столбцами SQL типа `TIME` с помощью LINQ to SQL, необходима платформа .NET Framework 3.5 с пакетом обновления 1 (SP1) и более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="77cbb-117">The ability to map <xref:System.TimeSpan?displayProperty=nameWithType> to a SQL `TIME` column with LINQ to SQL requires the .NET Framework 3.5 SP1 and beyond.</span></span> <span data-ttu-id="77cbb-118">Тип данных SQL `TIME` доступен только в версиях Microsoft SQL Server 2008 и выше.</span><span class="sxs-lookup"><span data-stu-id="77cbb-118">The SQL `TIME` data type is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
### <a name="addition-and-subtraction"></a><span data-ttu-id="77cbb-119">Сложение и вычитание</span><span class="sxs-lookup"><span data-stu-id="77cbb-119">Addition and Subtraction</span></span>  

 <span data-ttu-id="77cbb-120">Хотя тип CLR <xref:System.TimeSpan?displayProperty=nameWithType> поддерживает сложение и вычитание, тип SQL `TIME` их не поддерживает.</span><span class="sxs-lookup"><span data-stu-id="77cbb-120">Although the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type does support addition and subtraction, the SQL `TIME` type does not.</span></span> <span data-ttu-id="77cbb-121">Поэтому запросы LINQ to SQL будут вызывать ошибки при попытке выполнить сложение или вычитание, когда они сопоставлены с типом SQL `TIME`.</span><span class="sxs-lookup"><span data-stu-id="77cbb-121">Because of this, your LINQ to SQL queries will generate errors if they attempt addition and subtraction when they are mapped to the SQL `TIME` type.</span></span> <span data-ttu-id="77cbb-122">Другие рекомендации по работе с типами даты и времени SQL можно найти в [сопоставлении типов SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="77cbb-122">You can find other considerations for working with SQL date and time types in [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cbb-123">См. также</span><span class="sxs-lookup"><span data-stu-id="77cbb-123">See also</span></span>

- [<span data-ttu-id="77cbb-124">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="77cbb-124">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="77cbb-125">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="77cbb-125">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="77cbb-126">Сопоставление типов SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="77cbb-126">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="77cbb-127">Типы данных и функции</span><span class="sxs-lookup"><span data-stu-id="77cbb-127">Data Types and Functions</span></span>](data-types-and-functions.md)
