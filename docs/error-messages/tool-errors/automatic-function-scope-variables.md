---
title: 自动 （函数范围） 变量 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- automatic variables
- variables, automatic
- functions [C++], scope
- scope, declared within functions
ms.assetid: 6e1a14c2-1fb0-4937-8628-8d963cc35ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2cabf633245cfdf1b688b498bb5ec81aa5e7c486
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061388"
---
# <a name="automatic-function-scope-variables"></a>自动（函数范围）变量

仅在该函数的范围内使用函数内声明的变量。

```
// LNK2019_AV.cpp
// compile with: /c
void test(void);

static int lnktest3 = 3;
int lnktest4 = 4;

int main() {
   static int lnktest1 = 1;
   int lnktest2 = 2;
   test();
}
```

然后

```
// LNK2019_AV_2.cpp
// compile with: LNK2019_AV.cpp
// LNK2019 expected
extern int lnktest1;
extern int lnktest2;
extern int lnktest3;
extern int lnktest4;

void test(void) {
   int i = 0;
   i = lnktest1;
   i = lnktest2;
   i = lnktest3;
   i = lnktest4;   // OK
}
```

## <a name="see-also"></a>请参阅

[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)