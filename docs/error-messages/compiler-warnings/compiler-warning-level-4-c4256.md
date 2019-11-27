---
title: 编译器警告（等级 4）C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: e087e3cd36ab85d6f3f6b5cfed1b55cac66ea142
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541696"
---
# <a name="compiler-warning-level-4-c4256"></a>编译器警告（等级 4）C4256

"function"：具有虚拟基的类的构造函数具有 "...";调用可能与早期版本的视觉对象不兼容C++

可能的不兼容性。

请看如下代码示例。 如果在版本7之前使用 Microsoft C++编译器版本编译了构造函数 s2：： S2 （int i，...）的定义，但以下示例是使用当前版本编译的，则对 S3 的构造函数的调用将无法正常工作，因为有特殊的 case 调用约定更改。 如果两者都是使用 Visual C++ 6.0 编译的，该调用也无法完全正常工作，除非不为省略号传递任何参数。

若要修复此警告，

1. 不要在构造函数中使用省略号。

1. 请确保使用当前版本（包括可定义或引用此类的任何库）生成项目中的所有组件，然后使用[警告](../../preprocessor/warning.md)杂注禁用此警告。

下面的示例生成 C4256：

```cpp
// C4256.cpp
// compile with: /W4
// #pragma warning(disable : 4256)
struct S1
{
};

struct S2: virtual public S1
{
   S2( int i, ... )    // C4256
   {
      i = 0;
   }
   /*
   // try the following line instead
   S2( int i)
   {
      i = 0;
   }
   */
};

void func1()
{
   S2 S3( 2, 1, 2 );   // C4256
   // try the following line instead
   // S2 S3( 2 );
}

int main()
{
}
```