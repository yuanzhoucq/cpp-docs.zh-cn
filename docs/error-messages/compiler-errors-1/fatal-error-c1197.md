---
title: 错误 C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: e1c00a001c807b0cc6a5946b61ca4e9d5dc0167a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229112"
---
# <a name="fatal-error-c1197"></a>错误 C1197

不能引用 mscorlib.dll_1，因为程序已经引用 mscorlib.dll_2

编译器与公共语言运行时版本匹配。  但是，尝试从以前的版本中引用公共语言运行时文件的版本。

若要解决此错误，只能从引用文件与视觉对象的版本附带的公共语言运行时版本C++正在使用进行编译。

## <a name="example"></a>示例

下面的示例生成 C1197:

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```