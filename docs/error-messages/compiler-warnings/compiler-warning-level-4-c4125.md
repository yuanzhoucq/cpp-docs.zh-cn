---
title: 编译器警告（等级 4）C4125
ms.date: 11/04/2016
f1_keywords:
- C4125
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
ms.openlocfilehash: f194f0efc8012bf027e4785c2f398a0a7027b368
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991583"
---
# <a name="compiler-warning-level-4-c4125"></a>编译器警告（等级 4）C4125

十进制数字终止八进制转义序列

编译器未用十进制数求八进制数，并假定十进制数字是一个字符。

## <a name="example"></a>示例

```cpp
// C4125a.cpp
// compile with: /W4
char array1[] = "\709"; // C4125
int main()
{
}
```

如果数字 9 作为一个字符，请如下更正示例：

```cpp
// C4125b.cpp
// compile with: /W4
char array[] = "\0709";  // C4125 String containing "89"
int main()
{
}
```
