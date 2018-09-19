---
title: 编译器警告 （等级 C4571 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4571
dev_langs:
- C++
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1291466ffd9071929194ffbe7795addfec62eb27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088314"
---
# <a name="compiler-warning-level-4-c4571"></a>编译器警告（等级 4）C4571

Visual c + + 7.1; 之后更改的信息： 自语义不再捕获结构化的异常 (SEH)

C4571 时为生成的每个自块进行编译 **/EHs**。

使用编译时 **/EHs**，自块将不会捕获结构化的异常 （除 null 指针，例如零）; 自仅捕获显式引发，而 c + + 异常。  有关详细信息，请参阅[异常处理](../../cpp/exception-handling-in-visual-cpp.md)。

默认情况下，此警告处于关闭状态。  启用此警告，在使用编译时，确保 **/EHs** catch （...） 块不想要捕获结构化的异常。  请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

可以通过以下方式之一来解决 C4571

- 使用编译 **/EHa**仍然想要在自块来捕获结构化的异常。

- 如果不希望在自块来捕获结构化的异常，但仍想要使用自块，则不要启用 C4571。  您仍可以捕获结构化的异常通过结构化的异常处理关键字 (**__try**， **__except**，并 **__finally**)。  但是请记住，在编译时 **/EHs** SEH 异常发生时不引发 c + + 异常时，只会调用析构函数。

- 自块替换为特定的 c + + 异常的 catch 块和 （可选） 添加结构化的异常处理 c + + 异常处理 (**__try**， **__except**，和 **___identifier**)。  请参阅[结构化异常处理 （C/c + +）](../../cpp/structured-exception-handling-c-cpp.md)有关详细信息。

请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C4571。

```
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```