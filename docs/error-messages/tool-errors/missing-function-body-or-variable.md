---
title: 缺少函数体或变量 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1337cf936d986c038aacc355490f13e5f0c2d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088444"
---
# <a name="missing-function-body-or-variable"></a>缺少函数体或变量

只有函数原型，编译器可以继续未生成错误，但链接器无法解析为地址的调用，因为没有函数代码或保留的变量空间。 创建链接器必须解析的函数调用之前，不会看到此错误。

## <a name="example"></a>示例

原型使编译器认为存在的函数，所以，在 main 中的函数调用将会导致 LNK2019。  链接器查找它不会。

```
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>示例

在 c + +，请确保在类定义中包括的一个类，而不只是原型的特定函数的实现。 如果你正在定义的标头文件的外部类，请务必包括前该函数的类名 (`Classname::memberfunction`)。

```
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

## <a name="see-also"></a>请参阅

[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)