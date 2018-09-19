---
title: C + + 中的全局常量 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00d033c1c4fc8fc3e534c8e4ee0c3d7867b83834
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103161"
---
# <a name="global-constants-in-c"></a>C++ 中的全局常量

C + + 的全局常量具有静态链接。 这是与 C 不同。如果你尝试使用全局常数在多个文件中的 c + + 中，将得到未解析的外部错误。 编译器优化了全局常量，留出的变量保留任何空间。

若要解决此错误的一种方法是 const 初始化包括标头文件中，并在 CPP 文件，如有必要，就像它是函数原型中包括该标头。 另一种可能性是使变量成为非常量并评估它时使用的常量引用。

下面的示例生成 C2019:

```
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

然后，

```
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>请参阅

[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)