---
title: 编译器警告 （等级 1） C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 76aab2160bd5f7918771dcf63b7297a869da751e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651290"
---
# <a name="compiler-warning-level-1-c4005"></a>编译器警告 （等级 1） C4005

identifier： 宏重定义

宏标识符定义了两次。 编译器将使用在第二个宏的定义。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 在命令行上和与代码中定义宏`#define`指令。

1. 从包含文件中导入的宏。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 删除其中一个定义。

1. 使用[#undef](../../preprocessor/hash-undef-directive-c-cpp.md)指令之前第二个定义。

下面的示例生成 C4005:

```
// C4005.cpp
// compile with: /W1 /EHsc
#include <iostream>
using namespace std;

#define TEST "test1"
#define TEST "test2"   // C4005 delete or rename to resolve the warning

int main() {
   cout << TEST << endl;
}
```