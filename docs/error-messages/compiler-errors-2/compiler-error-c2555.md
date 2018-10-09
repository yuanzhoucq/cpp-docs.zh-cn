---
title: 编译器错误 C2555 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0cd401aa1ee3611befb39d630f48f6aed36211c
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2018
ms.locfileid: "48889941"
---
# <a name="compiler-error-c2555"></a>编译器错误 C2555

class1::function1： 重写虚函数返回类型有差异，不是从 class2::function2 协变

虚函数和派生的重写函数具有相同的参数列表，但不同的返回类型。 在派生类中的重写函数不能从基类仅由其返回类型中的虚拟函数。

若要解决此错误，将返回值转换后调用的虚拟函数。

如果您使用 /clr 进行编译，也可能会看到此错误。   例如，Visual c + + 等效于下面的 C# 声明：

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

下面的示例生成 C2555:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```