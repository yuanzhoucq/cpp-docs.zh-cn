---
title: 编译器错误 C2017
ms.date: 11/04/2016
f1_keywords:
- C2017
helpviewer_keywords:
- C2017
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
ms.openlocfilehash: 3911ef9af2eb0fab7d0f9296ddce8a0f9b32ae0d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751048"
---
# <a name="compiler-error-c2017"></a>编译器错误 C2017

非法的转义序列

转义序列（如 \t）出现在字符或字符串常量的外部。

下面的示例生成 C2017：

```cpp
// C2017.cpp
int main() {
   char test1='a'\n;   // C2017
   char test2='a\n';   // ok
}
```

当 stringize 运算符与包含转义序列的字符串一起使用时，可能会发生 C2017。

下面的示例生成 C2017：

```cpp
// C2017b.cpp
#define TestDfn(x) AfxMessageBox(#x)
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017
```
