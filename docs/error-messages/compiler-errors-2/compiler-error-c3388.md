---
title: 编译器错误 C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: 3b56aae115b1a1721f3f8a8688e36b25edc7f33f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780023"
---
# <a name="compiler-error-c3388"></a>编译器错误 C3388

“type”: 不允许作为约束，假定 "ref class" 继续进行分析

对泛型类型指定了约束，但是未正确地指定约束。 请参阅[泛型类型参数的约束 (C + + CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C3388。

```
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```