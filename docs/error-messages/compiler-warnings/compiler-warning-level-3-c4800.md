---
title: 编译器警告（等级 3）C4800
ms.date: 11/04/2016
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 591b706249201691c7a9743d2cad082eb61e68b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636132"
---
# <a name="compiler-warning-level-3-c4800"></a>编译器警告（等级 3）C4800

> '*类型*： 值强制到 bool 'true' 或 'false' （性能警告）

值时，不会生成此警告`bool`分配或强制转换为类型`bool`。 通常情况下，此消息由分配`int`到变量`bool`变量其中`int`变量仅包含值**true**并**false**，并且可能重新声明为类型`bool`。 如果您不能重写表达式以使用类型`bool`，然后可以将添加"`!=0`"到表达式中，它可使表达式类型`bool`。 强制转换表达式到类型`bool`不会禁用警告，这是设计使然。

在 Visual Studio 2017 中不再生成此警告。

## <a name="example"></a>示例

下面的示例生成 C4800 并演示如何修复此错误：

```cpp
// C4800.cpp
// compile with: /W3
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```