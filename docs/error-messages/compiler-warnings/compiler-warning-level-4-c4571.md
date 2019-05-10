---
title: 编译器警告（等级 4）C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 92164bf297a44871897b6c6150eb54f8c5ccf3cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220450"
---
# <a name="compiler-warning-level-4-c4571"></a>编译器警告（等级 4）C4571

信息性： 自 Visual 更改自语义C++7.1;不再捕获结构化的异常 (SEH)

C4571 时为生成的每个自块进行编译 **/EHs**。

使用编译时 **/EHs**，自块不会捕获结构化的异常 （除 null 指针，例如零）; 自块只捕捉显式引发C++异常。  有关详细信息，请参阅[异常处理](../../cpp/exception-handling-in-visual-cpp.md)。

默认情况下，此警告处于关闭状态。  启用此警告，在使用编译时，确保 **/EHs** catch （...） 块不想要捕获结构化的异常。  请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

可以通过以下方式之一来解决 C4571

- 使用编译 **/EHa**仍然想要在自块来捕获结构化的异常。

- 如果不希望在自块来捕获结构化的异常，但仍想要使用自块，则不要启用 C4571。  您仍可以捕获结构化的异常通过结构化的异常处理关键字 (**__try**， **__except**，并 **__finally**)。  但是请记住，在编译时 **/EHs**时，才会调用析构函数C++SEH 异常发生时不引发异常。

- 自块替换为特定的 catch 块C++异常，并 （可选） 将结构化的异常处理周围添加C++异常处理 (**__try**， **__except**，并 **__finally**)。  请参阅[结构化异常处理 (C /C++)](../../cpp/structured-exception-handling-c-cpp.md)有关详细信息。

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