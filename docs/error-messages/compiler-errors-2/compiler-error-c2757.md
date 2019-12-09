---
title: 编译器错误 C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: a9f4661495e0fa5219a517b6f6ca410323a77269
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759524"
---
# <a name="compiler-error-c2757"></a>编译器错误 C2757

"symbol"：具有此名称的符号已存在，因此不能将此名称用作命名空间名称

当前编译中用作命名空间标识符的符号已在引用的程序集中使用。

下面的示例生成 C2757：

```cpp
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

然后，

```cpp
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
