---
title: 编译器错误 C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: d20bc61df2d0bab9115768b3bc0589f11a9bcdb9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302089"
---
# <a name="compiler-error-c2032"></a>编译器错误 C2032

"identifier"：函数不能是结构/联合 "structorunion" 的成员

结构或联合具有成员函数，该函数在中C++是允许的，但在 C 中是不允许的。若要解决此错误，请将编译C++为程序或删除成员函数。

下面的示例生成 C2032：

```c
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

可能的解决方法：

```c
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```
