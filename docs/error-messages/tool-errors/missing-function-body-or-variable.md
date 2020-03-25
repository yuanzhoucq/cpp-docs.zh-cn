---
title: 缺少函数体或变量
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 6d2ef22b90009d320485fb6fe3f7e308ae05c442
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173616"
---
# <a name="missing-function-body-or-variable"></a>缺少函数体或变量

除了函数原型外，编译器可以继续而不会出错，但链接器无法解析对地址的调用，因为没有保留函数代码或变量空间。 在创建对链接器必须解析的函数的调用之前，您将看不到此错误。

## <a name="example"></a>示例

Main 中的函数调用将导致 LNK2019，因为原型允许编译器认为函数存在。  链接器将发现它不会。

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>示例

在C++中，请确保在类定义中包括类的特定函数实现，而不仅仅是类定义中的原型。 如果要在标头文件之外定义类，请确保在函数之前包含类名（`Classname::memberfunction`）。

```cpp
// LNK2019_MFBV_2.cpp
// LNK2019 expected
struct A {
   static void Test();
};

// Should be void A::Test() {}
void Test() {}

int main() {
   A AObject;
   AObject.Test();
}
```

## <a name="see-also"></a>另请参阅

[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
