---
title: "编译器错误 C2512 |Microsoft 文档"
ms.custom: 
ms.date: 02/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2512
dev_langs:
- C++
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57dbb542eee7e893253e6c3bdd3410c605a8d2db
ms.sourcegitcommit: 8ae12a602244a5853e941e5e8806e3545d876844
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2018
---
# <a name="compiler-error-c2512"></a>编译器错误 C2512

> *标识符*： 没有适当的默认构造函数可用  

A*默认构造函数*，不需要任何参数的构造函数不可用于指定的类、 结构或联合。 仅当提供了没有用户定义的构造函数，编译器将提供默认构造函数。

如果你提供具有非 void 参数的构造函数，你想要允许你的类以创建不带任何参数 （例如，作为数组的元素），你还必须提供一个默认构造函数。 默认构造函数可以是一个所有参数都使用默认值的构造函数。

## <a name="example"></a>示例

错误 C2512 的常见原因是当你定义的类或结构的构造函数采用自变量时，然后你尝试声明类或结构不带任何参数的实例。 例如，`struct B`下面声明的构造函数的需要`char *`自变量，而不是不带任何参数。 在`main`，声明 B 的实例，但未提供参数。 编译器生成 C2512，因为它找不到默认构造函数 b。

```cpp
// C2512.cpp
// Compile with: cl /W4 c2512.cpp
// C2512 expected
struct B {
   B (char *) {}
   // Uncomment the following line to fix.
   // B() {}
};

int main() {
   B b;   // C2512 - This requires a default constructor
}
```

你可以通过定义默认构造函数为结构或类，如修复此问题`B() {}`，或其中的所有自变量具有默认值，如构造函数`B (char * = nullptr) {}`。
