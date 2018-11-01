---
title: 编译器警告（等级 1）C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: 892e6c37e54a868be48ced35354a1096aa7bf9d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536698"
---
# <a name="compiler-warning-level-1-c4526"></a>编译器警告（等级 1）C4526

function： 静态成员函数不能重写虚函数虚拟 function'override 被忽略，将隐藏虚函数

静态成员函数可以满足用来重写虚函数，这使得虚拟和静态成员函数的条件。

下面的代码生成 C4526:

```
// C4526.cpp
// compile with: /W1 /c
// C4526 expected
struct myStruct1 {
   virtual void __stdcall func( int ) = 0;
};

struct myStruct2: public myStruct1 {
   static void __stdcall func( int );
};
```

以下是可能的修复方法：

- 如果该函数用于重写基类的虚函数，则移除静态说明符。

- 如果该函数本来就是静态成员函数，重命名它，以便与基类虚函数不会发生冲突。