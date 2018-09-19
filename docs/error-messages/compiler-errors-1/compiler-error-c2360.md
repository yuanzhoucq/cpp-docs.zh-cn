---
title: 编译器错误 C2360 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2360
dev_langs:
- C++
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f443c27c496d5d05c17bde854181b0fdde58f545
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089198"
---
# <a name="compiler-error-c2360"></a>编译器错误 C2360

按 case 标签跳过 identifier 的初始化

初始化`identifier`中，可以跳过`switch`语句。 除非声明将封闭的块中，不能跳过具有初始值设定项的声明。 (除非它被声明块中，变量是作用域内的结束前一直`switch`语句。)

下面的示例生成 C2360:

```
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

可能的解决方法：

```
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```