---
title: "编译器错误 C2975 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2975
dev_langs: C++
helpviewer_keywords: C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65644cc13629481941ffdd8676e51311c665f106
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="compiler-error-c2975"></a>编译器错误 C2975

> *参数*： 模板参数无效*类型*，应输入编译时常量表达式

模板自变量与模板声明中; 不匹配常量表达式应出现在尖括号中。 变量不允许作为模板自变量。 请检查模板定义，以找到正确的类型。

## <a name="example"></a>示例

下面的示例生成 C2975，并还显示正确用法：

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 也会发生当你使用 &#95; &#95;行 &#95; &#95;作为编译时常量[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)。 一个解决方案是使用进行编译[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)而不是**/ZI**。

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```