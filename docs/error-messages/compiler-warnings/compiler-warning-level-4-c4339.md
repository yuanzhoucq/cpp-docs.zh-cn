---
title: 编译器警告（等级 4）C4339
ms.date: 11/04/2016
f1_keywords:
- C4339
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
ms.openlocfilehash: fffdaa255f6b8f2259488df610f163bebf8d6dec
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683292"
---
# <a name="compiler-warning-level-4-c4339"></a>编译器警告（等级 4）C4339

“type”: 在 WinRT 或 CLR 元数据中检测到使用了未定义的类型 - 使用此类型可能导致运行时异常

类型未在针对 Windows 运行时或公共语言运行时编译的代码中定义。 定义类型以避免可能的运行时异常。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

下面的示例将生成 C4339，并演示如何修复此错误：

```cpp
// C4339.cpp
// compile with: /W4 /clr /c
// C4339 expected
#pragma warning(default : 4339)

// Delete the following line to resolve.
class A;

// Uncomment the following line to resolve.
// class A{};

class X {
public:
   X() {}

   virtual A *mf() {
      return 0;
   }
};

X * f() {
   return new X();
}
```