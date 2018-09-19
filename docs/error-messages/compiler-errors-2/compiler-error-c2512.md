---
title: 编译器错误 C2512 |Microsoft Docs
ms.custom: ''
ms.date: 02/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2512
dev_langs:
- C++
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba1fbba98237879927fd82d6535c0c2688c1c304
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036912"
---
# <a name="compiler-error-c2512"></a>编译器错误 C2512

> '*标识符*： 没有合适的默认构造函数可用

一个*默认构造函数*，不需要任何参数的构造函数不是可用于指定的类、 结构或联合。 仅当没有用户定义的构造函数提供，编译器将提供默认构造函数。

如果提供构造函数采用非 void 参数，并且你想要允许您创建不带任何参数 （例如，为数组的元素） 的类，还必须提供默认构造函数。 默认构造函数可以是一个所有参数都使用默认值的构造函数。

## <a name="example"></a>示例

错误 C2512 的常见原因是当定义的类或结构的构造函数采用参数，然后您尝试声明类或结构不带任何参数的实例。 例如，`struct B`下面声明一个构造函数需要`char *`参数，而不是不采用任何参数。 在`main`，声明 B 的实例，但未提供参数。 编译器生成 C2512，因为它找不到默认构造函数 b。

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

可以通过定义默认构造函数的结构或类，如修复此问题`B() {}`，或构造函数的所有参数都具有默认值，如`B (char * = nullptr) {}`。
