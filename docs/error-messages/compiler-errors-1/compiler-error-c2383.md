---
title: 编译器错误 C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 2aa922ebeadb374a7eac73a0f452376472b00984
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206023"
---
# <a name="compiler-error-c2383"></a>编译器错误 C2383

"*symbol*"：此符号上不允许使用默认参数

C++编译器不允许指向函数的指针的默认参数。

此代码已被 Visual Studio 2005 C++之前的版本中的 Microsoft 编译器接受，但现在提供错误。 对于在所有版本的 Visual C++中都适用的代码，请不要为指向函数的指针参数赋值。

## <a name="example"></a>示例

下面的示例生成 C2383，并显示一个可能的解决方案：

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
