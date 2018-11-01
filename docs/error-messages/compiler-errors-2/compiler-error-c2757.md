---
title: 编译器错误 C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: 98b43a2f3c0888fc385226cd80889b9911c84690
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668515"
---
# <a name="compiler-error-c2757"></a>编译器错误 C2757

symbol： 具有此名称的符号已存在，因此此名称不能用作命名空间名称

中引用的程序集中已使用的命名空间标识符作为当前编译中使用的符号。

下面的示例生成 C2757:

```
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

然后，

```
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
