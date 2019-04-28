---
title: C++ 中的全局常量
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 2f0621f52fe445f8f2058ef902824ddc1f5e2bb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255425"
---
# <a name="global-constants-in-c"></a>C++ 中的全局常量

C++全局常量具有静态链接。 这是与 C 不同。如果尝试使用中的全局常量C++多个文件中获取无法解析的外部错误。 编译器优化了全局常量，留出的变量保留任何空间。

若要解决此错误的一种方法是 const 初始化包括标头文件中，并在 CPP 文件，如有必要，就像它是函数原型中包括该标头。 另一种可能性是使变量成为非常量并评估它时使用的常量引用。

下面的示例生成 C2019:

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

然后，

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>请参阅

[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)