---
title: 编译器警告 （等级 C4702 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4702
dev_langs:
- C++
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d15072099c6329eced8ab9dd9c78f8f48c31fe7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057128"
---
# <a name="compiler-warning-level-4-c4702"></a>编译器警告（等级 4）C4702

无法访问的代码

此警告是适用于 Visual Studio.NET 2003年执行的编译器一致性工作的结果： 无法访问的代码。 当编译器 （后端） 检测到无法访问的代码时，它将生成 C4702，第 4 级警告。

有关在 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效的代码，删除无法访问的代码，或确保所有的源代码是可访问的某些流的执行。

## <a name="example"></a>示例

下面的示例生成 C4702。

```
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

## <a name="example"></a>示例

使用编译时 **/GX**，**了 /EHc**， **/EHsc**，或者 **/EHac**和使用 extern C 函数，代码可能会变得无法访问因为 extern C函数假定不引发，因此 catch 块无法访问。  如果您认为，此警告不有效因为函数可以引发，使用编译 **/EHa**或 **/EHs**，取决于引发的异常。

有关详细信息，请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md)有关详细信息。

下面的示例生成 C4702。

```
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```