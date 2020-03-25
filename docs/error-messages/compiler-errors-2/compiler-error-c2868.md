---
title: 编译器错误 C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 0cbcf7dc80aedc554594f88992059f98b7091c21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201626"
---
# <a name="compiler-error-c2868"></a>编译器错误 C2868

> "*identifier*"：非法的 using 声明语法;应为限定名

[Using 声明](../../cpp/using-declaration.md)需要*限定名称*，以命名空间（`::`）分隔的命名空间、类或枚举名称序列，以标识符名称结尾。 单个范围解析运算符可用于引入全局命名空间的名称。

## <a name="example"></a>示例

下面的示例生成 C2868，并显示正确的用法：

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```
