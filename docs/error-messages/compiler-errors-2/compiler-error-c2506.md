---
title: 编译器错误 C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 593fbbc6b561e6390624aa79af14dc665a552990
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746833"
---
# <a name="compiler-error-c2506"></a>编译器错误 C2506

"member"： "__declspec （修饰符）" 不能应用于此符号

不能为托管类的静态成员声明每进程或每个 appdomain。

有关更多信息，请参见 [appdomain](../../cpp/appdomain.md) 。

## <a name="example"></a>示例

下面的示例生成 C2506。

```cpp
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```
