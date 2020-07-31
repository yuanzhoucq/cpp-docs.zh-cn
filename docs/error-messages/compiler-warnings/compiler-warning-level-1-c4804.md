---
title: 编译器警告（等级 1）C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: aa2cdf0103a1ccc607f2e4a55e1d8f85bb8cc45d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233218"
---
# <a name="compiler-warning-level-1-c4804"></a>编译器警告（等级 1）C4804

"operation"：在操作中使用类型 "bool" 不安全

当你 **`bool`** 以意外方式使用变量或值时，将出现此警告。 例如，如果使用运算符（如负一元运算符（ **-** ）或补码运算符（）），则会生成 C4804 `~` 。 编译器将计算表达式的值。

## <a name="example"></a>示例

下面的示例生成 C4804：

```cpp
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```
