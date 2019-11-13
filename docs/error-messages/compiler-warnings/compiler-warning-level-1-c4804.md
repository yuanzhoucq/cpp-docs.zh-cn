---
title: 编译器警告（等级1） C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 97ad076325b11329896d98367fb3ac311ec5ded9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051570"
---
# <a name="compiler-warning-level-1-c4804"></a>编译器警告（等级1） C4804

"operation"：在操作中使用类型 "bool" 不安全

当你以意外方式使用 `bool` 变量或值时，会出现此警告。 例如，如果使用运算符（如负一元运算符（ **-** ）或补码运算符（`~`）），则会生成 C4804。 编译器将计算表达式的值。

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