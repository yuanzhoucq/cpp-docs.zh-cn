---
title: 编译器错误 C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 8456e9b17b72cd4ac98349d2f2871a1c59f56911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311477"
---
# <a name="compiler-error-c3418"></a>编译器错误 C3418

不支持访问说明符“specifier”

不正确地指定了 CLR 访问说明符。  有关详细信息，请参阅类型可见性和中的成员可见性[如何：定义和使用类和结构 (C++/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C3418。

```cpp
// C3418.cpp
// compile with: /clr /c
ref struct m {
internal public:   // C3418
   void test(){}
};

ref struct n {
internal:   // OK
   void test(){}
};
```