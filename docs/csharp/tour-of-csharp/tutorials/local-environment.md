---
title: Знакомство со средствами разработки. Вводное руководство по C#
description: Эта статья содержит базовое описание средств разработки, которые вы будете использовать для создания приложений C# и .NET на локальном компьютере.
ms.date: 02/02/2021
ms.openlocfilehash: 72116154126b0a97fffe417b2807576b1d9689df
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100626663"
---
# <a name="set-up-your-local-environment"></a>Настройка локальной среды

Для выполнения этого руководства прежде всего нужно настроить на компьютере среду разработки. Выберите один из следующих вариантов:

* Сведения об использовании .NET CLI и любого текстового редактора или редактора кода см. в статье [Руководство по .NET — Hello World за 10 минут](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro). В этом руководстве содержатся инструкции по настройке локальной среды разработки в macOS, Windows или Linux.
* Чтобы использовать .NET CLI и Visual Studio Code, установите пакет [SDK для .NET](https://dotnet.microsoft.com/download) и [Visual Studio Code](https://code.visualstudio.com/).
* Сведения об использовании Visual Studio 2019, см. в статье [Руководство. Создание простого консольного приложения C# в Visual Studio](/visualstudio/get-started/csharp/tutorial-console).

## <a name="basic-application-development-flow"></a>Базовый поток разработки приложения

В инструкциях, приведенных в этих руководствах, предполагается, что вы используете .NET CLI для создания, сборки и запуска приложений. Вы будете использовать следующие команды:

* [`dotnet new`](../../../core/tools/dotnet-new.md) создает приложение. Эта команда создает файлы и ресурсы, необходимые для приложения. Во всех ознакомительных руководствах по C# используется тип приложения `console`. Освоив описанные здесь основы, вы сможете перейти и к другим типам приложений.
* [`dotnet build`](../../../core/tools/dotnet-build.md) выполняет сборку исполняемого файла.
* [`dotnet run`](../../../core/tools/dotnet-run.md) запускает исполняемый файл.

Если вы используете Visual Studio 2019 для работы с этими руководствами, выберите вариант с меню Visual Studio, когда в руководстве будет предложено выполнить одну из следующих команд CLI:

* **Файл** > **Создать** > **Проект** — создание приложения;
* **Сборка** >  **Собрать решение** — сборка исполняемого файла;
* **Отладка** > **Запуск без отладки** — запуск исполняемого файла.

## <a name="pick-your-tutorial"></a>Выбор руководства

Вы можете начать изучение с любого из следующих руководств:

## <a name="numbers-in-c"></a>Числа в C\#

Из руководства [Числа в C#](numbers-in-csharp-local.md) вы узнаете, как на компьютере хранятся числа и как выполнять вычисления с разными числовыми типами. Вы ознакомитесь с основами округления и научитесь выполнять математические вычисления с помощью C#.

В этом руководстве предполагается, что вы уже прошли занятие [Hello World](hello-world.yml).

## <a name="branches-and-loops"></a>Ветви и циклы

В руководстве [Ветви и циклы](branches-and-loops-local.md) представлены общие принципы организации ветвления кода в зависимости от значений, хранящихся в переменных. Вы узнаете, что такое поток управления, являющийся основой принятия решений и выбора различных действий в программах.

В этом руководстве предполагается, что вы уже прошли занятия [Hello World](hello-world.yml) и [Числа в C#](numbers-in-csharp-local.md).

## <a name="list-collection"></a>Коллекция списков

Занятие [Коллекция списков](arrays-and-collections.md) содержит обзор типа "Коллекция списков", в котором хранятся последовательности данных. Вы узнаете, как добавлять и удалять элементы, выполнять их поиск и сортировать списки. Вы ознакомитесь с различными типами списков.

В этом руководстве предполагается, что вы уже прошли перечисленные выше занятия.
