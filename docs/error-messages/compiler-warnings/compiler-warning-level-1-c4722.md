---
title: 编译器警告 （等级 1） C4722 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4722
dev_langs:
- C++
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f450120ff05c7e13888bf4b4ce4425405525b4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112494"
---
# <a name="compiler-warning-level-1-c4722"></a>编译器警告（等级 1）C4722

“function”：析构函数永远不会返回，可能会发生内存泄漏

控制流在析构函数中终止。 该线程或整个程序将终止且分配的资源可能不会发布。  此外，如果在异常处理期间为堆栈展开调用了析构函数，则无法确定可执行文件的行为。

若要解决，请删除导致析构函数不能返回的函数调用。

## <a name="example"></a>示例

下面的示例生成 C4722：

```
// C4722.cpp
// compile with: /O1 /W1 /c
#include <stdlib.h>
class C {
public:
   C();
   ~C() { exit(1); };   // C4722
};

extern void func (C*);

void Test(){
   C x;
   func(&x);
   // control will not leave Test because destructor will exit
}
```