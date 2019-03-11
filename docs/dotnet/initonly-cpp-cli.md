---
title: initonly (C++/CLI)
ms.date: 11/04/2016
f1_keywords:
- initonly_cpp
- initonly
helpviewer_keywords:
- initonly attribute [C++]
ms.assetid: f745d7fa-dc08-46f1-9b97-0977be58a008
ms.openlocfilehash: 91b1447231cbc189a701517e48890fea34c2858a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742893"
---
# <a name="initonly-ccli"></a>initonly (C++/CLI)

**initonly**是仅在声明或在同一个类中的静态构造函数中可能出现上下文相关的关键字，指示该变量赋值。

下面的示例演示如何使用 `initionly`：

```
// mcpp_initonly.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst1;

   initonly
   static int staticConst2 = 0;

   static Y1() {
      staticConst1 = 0;
   }
};
```

## <a name="see-also"></a>请参阅

[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)
