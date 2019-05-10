---
title: 编译器错误 C3156
ms.date: 11/04/2016
f1_keywords:
- C3156
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
ms.openlocfilehash: 115e8cd63562964b19e4a67f7a649ecfab2596c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375335"
---
# <a name="compiler-error-c3156"></a>编译器错误 C3156

“class”：不能局部定义托管或 WinRT 类型

函数不能包含托管或 WinRT 类、结构或接口的定义或声明。

## <a name="example"></a>示例

下面的示例生成 C3156。

```
// C3156.cpp
// compile with: /clr /c
void f() {
   ref class X {};   // C3156
   ref class Y;   // C3156
}
```
