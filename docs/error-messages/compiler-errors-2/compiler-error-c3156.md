---
title: 编译器错误 C3156
ms.date: 11/04/2016
f1_keywords:
- C3156
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
ms.openlocfilehash: 115e8cd63562964b19e4a67f7a649ecfab2596c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465255"
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
