---
title: 错误 C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: 7f698262c73f0b311a92a8940107b552430919bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747236"
---
# <a name="fatal-error-c1197"></a>错误 C1197

无法引用 "mscorlib. dll_1"，因为程序已经引用了 "mscorlib. dll_2"

编译器与公共语言运行时的版本匹配。  但是，尝试引用以前版本中的公共语言运行时文件的版本。

若要解决此错误，只需要从您正在编译的 Visual C++语言运行时版本附带的公共语言运行时版本引用文件。

## <a name="example"></a>示例

下面的示例生成 C1197：

```cpp
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```
