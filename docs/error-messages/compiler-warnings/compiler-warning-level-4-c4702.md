---
title: 编译器警告（等级 4）C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 5e46bfef925f999ed7f04b5bbe7c88800209ed14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990646"
---
# <a name="compiler-warning-level-4-c4702"></a>编译器警告（等级 4）C4702

无法访问的代码

此警告是针对 Visual Studio .NET 2003：无法访问的代码所执行的编译器一致性工作的结果。 当编译器（后端）检测到无法访问的代码时，它将生成 C4702，第4级警告。

对于在 visual Studio .NET 2003 和 visual Studio .NET 版本的 Visual C++studio 中都有效的代码，请删除无法访问的代码，或确保所有源代码都可通过某个执行流访问。

## <a name="example"></a>示例

下面的示例生成 C4702。

```cpp
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

## <a name="example"></a>示例

使用 **/gx**、 **/EHc**、 **/ehsc**或 **/EHac**并使用 extern c 函数进行编译时，代码可能会无法访问，因为假定 extern c 函数不会引发，因此无法到达 catch 块。  如果你认为此警告无效，因为函数可以引发、使用 **/eha**或 **/ehs**进行编译，具体取决于引发的异常。

有关详细信息，请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md) 。

下面的示例生成 C4702。

```cpp
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
