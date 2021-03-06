---
title: Отложенные выражения
description: 'Узнайте, как выражения F # Lazy могут улучшить производительность приложений и библиотек.'
ms.date: 08/15/2020
ms.openlocfilehash: 0b8496467295ce6793f80c341af88bb1819f4a47
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425507"
---
# <a name="lazy-expressions"></a>Отложенные выражения

*Отложенные выражения* — это выражения, которые не оцениваются немедленно, а оцениваются, когда требуется результат. Это поможет повысить производительность кода.

## <a name="syntax"></a>Синтаксис

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Remarks

В приведенном выше синтаксисе *выражение* — это код, который вычисляется только тогда, когда требуется результат, а *идентификатор* — это значение, в котором хранится результат. Значение имеет тип `Lazy<'T>` , где фактический тип, используемый для, `'T` определяется из результата выражения.

Отложенные выражения позволяют повысить производительность за счет ограниченного выполнения выражений только теми ситуациями, в которых требуется результат.

Чтобы принудительно выполнить выражения, вызовите метод `Force` . `Force` приводит к выполнению выполнения только один раз. Последующие вызовы `Force` возвращают тот же результат, но не выполняют никакой код.

В следующем коде показано использование отложенных выражений и использование `Force` . В этом коде тип `result` имеет значение `Lazy<int>` , а `Force` метод возвращает `int` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Отложенная оценка, но не `Lazy` тип, также используется для последовательностей. Дополнительные сведения см. в разделе [последовательности](sequences.md).

## <a name="see-also"></a>См. также

- [Справочник по языку F#](index.md)
- [Модуль Лазекстенсионс](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
