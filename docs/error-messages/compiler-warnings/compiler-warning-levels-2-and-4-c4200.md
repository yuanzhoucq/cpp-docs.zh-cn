---
title: 编译器警告（等级 2 和等级 4）C4200
ms.date: 11/04/2016
f1_keywords:
- C4200
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
ms.openlocfilehash: 56a2ba641df610519949f64f6feeca18d9a99e93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519803"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>编译器警告（等级 2 和等级 4）C4200

使用了非标准扩展： 结构/联合中大小为零的数组

指示结构或联合包含大小为零的数组。

大小为零数组的声明为 Microsoft 扩展。 编译 C++ 文件时，这会造成等级 2 警告，而在编译 c 文件时会造成等级 4 警告。 C + + 编译也发出以下警告:"无法生成复制构造函数或复制赋值运算符当 UDT 包含大小为零的数组。" 此示例生成警告 C4200：

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

此非标准扩展常用于将代码与具有可变长度的外部数据结构连接起来。 如果此方案适用于你的代码，则可禁用此警告：

## <a name="example"></a>示例

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```