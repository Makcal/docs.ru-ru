---
description: 'Дополнительные сведения: файл, указанный в FileName, не является допустимым XML-файлом'
title: Файл, указанный в FileName, не является допустимым XML-файлом
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: c7d521986f3489345117a3947ed1e9b459af897e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472986"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Файл, указанный в FileName, не является допустимым XML-файлом

Указанное имя файла не представляет допустимый XML-файл. Чтобы задать допустимую структуру и содержимое XML-документа, можно использовать схему DTD, Microsoft XML-Data Reduced (XDR) или языка определения схемы XML. Схемы XSD — предпочтительный способ указания грамматики XML в платформа .NET Framework.

> [!NOTE]
> В некоторых более ранних версиях Visual Studio **конструктор XML** — это конструктор для типизированных наборов данных и схемы XML. **Конструктор XML** по-прежнему можно использовать для создания и редактирования файлов схемы XML. Однако в Visual Studio 2012 конструктор для создания и редактирования типизированных наборов данных — это **Конструктор наборов данных**. Дополнительные сведения см. в разделе [Создание и изменение типизированных наборов данных](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).

## <a name="to-correct-this-error"></a>Исправление ошибки

- Убедитесь, что вы указали правильное имя файла.

- Убедитесь, что указанный файл содержит допустимый XML, загрузив XML-файл, который требуется проверить, в **конструктор XML**. В меню **XML** выберите **Проверить XML**. Ошибки отображаются в **списке задач**.

- Если XML-файл имеет связанную схему XML, удостоверьтесь, что элементы существуют в определенной структуре и что содержимое отдельных элементов соответствует объявленным типам данных, указанным в схеме.

## <a name="see-also"></a>См. также раздел

- <xref:System.Xml>
- [Практическое руководство. Анализ путей к файлам](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
