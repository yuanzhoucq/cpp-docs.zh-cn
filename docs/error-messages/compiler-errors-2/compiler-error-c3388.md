---
title: 编译器错误 C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: bb2a847c24b2a0b7829008793f311459e76587f4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758341"
---
# <a name="compiler-error-c3388"></a>编译器错误 C3388

“type”: 不允许作为约束，假定 "ref class" 继续进行分析

对泛型类型指定了约束，但是未正确地指定约束。 有关详细信息，请参阅[泛型C++类型参数（/Cli）的约束](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C3388。

```cpp
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
