---
title: Выражения соответствия
description: Узнайте, как F# выражение match обеспечивает управление ветвлением, основанное на сравнении выражения с набором шаблонов.
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627608"
---
# <a name="match-expressions"></a>Выражения соответствия

`match` Выражение обеспечивает управление ветвлением, основанное на сравнении выражения с набором шаблонов.

## <a name="syntax"></a>Синтаксис

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a>Примечания

Выражения сопоставления шаблонов позволяют выполнять сложное ветвление на основе сравнения тестового выражения с набором шаблонов. В выражении выражение *теста* сравнивается с каждым шаблоном, а при обнаружении совпадения вычисляется соответствующее результирующее выражение, а итоговое значение возвращается в качестве значения выражения соответствия. `match`

Функция сопоставления шаблонов, показанная в предыдущем синтаксисе, представляет собой лямбда-выражение, в котором сопоставление шаблонов выполняется непосредственно над аргументом. Функция сопоставления шаблонов, показанная в предыдущем синтаксисе, эквивалентна следующей.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Дополнительные сведения о лямбда-выражениях см [. в разделе Лямбда-выражения: Ключевое](./functions/lambda-expressions-the-fun-keyword.md)слово. `fun`

Весь набор шаблонов должен охватывать все возможные совпадения входной переменной. Часто шаблон подстановочного знака (`_`) используется в качестве последнего шаблона для сопоставления с любыми ранее несовпадающими входными значениями.

В следующем коде показаны некоторые способы `match` использования выражения. Справочные сведения и примеры всех возможных шаблонов, которые можно использовать, см. в разделе [сопоставление шаблонов](pattern-matching.md).

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Условия для шаблонов

`when` Предложение можно использовать для указания дополнительного условия, которым должна удовлетворять переменная для соответствия шаблону. Такое предложение называется *условием*. Выражение, следующее `when` за ключевым словом, не вычисляется, если в шаблон, связанный с этим условием, не установлено соответствие.

В следующем примере показано использование условия для указания числового диапазона для шаблона переменной. Обратите внимание, что несколько условий объединяются с помощью логических операторов.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Обратите внимание, что, поскольку значения, отличные от литералов, не могут использоваться в шаблоне, необходимо использовать `when` предложение, если необходимо сравнить некоторую часть входных данных со значением. Это продемонстрировано в приведенном ниже коде.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Обратите внимание, что если шаблон объединения охватывается условием, условие применяется ко **всем** шаблонам, а не только к последнему. Например, при наличии следующего кода условие `when a > 12` применяется `A a` к и `B a`:

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a>См. также

- [Справочник по языку F#](index.md)
- [Активные шаблоны](active-patterns.md)
- [Соответствие шаблону](pattern-matching.md)
