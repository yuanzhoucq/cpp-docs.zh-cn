---
title: C++ 中的全局常量
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 1ae29b8744e24b6471f0d5536f3f13cc5ae59499
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030188"
---
# <a name="global-constants-in-c"></a>C++ 中的全局常量

C++全局常量具有静态链接。 这是与 C 不同。如果尝试使用中的全局常量C++多个文件中获取无法解析的外部错误。 编译器优化了全局常量，留出的变量保留任何空间。

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