---
title: 编译器错误 C2362
ms.date: 06/03/2019
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: d48806982bbb6cdda4d29e47f6692e7e3601d6de
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503214"
---
# <a name="compiler-error-c2362"></a>编译器错误 C2362

> 初始化*标识符*通过跳过 goto*标签*

通过使用在编译时[/Za](../../build/reference/za-ze-disable-language-extensions.md)，跳转到标签会无法标识符初始化。

如果不输入的块中括在声明或变量已初始化，仅可以跳过具有初始值设定项的声明。

下面的示例生成 C2362:

```cpp
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

可能的解决方法：

```cpp
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```