---
title: 编译器错误 C3183
ms.date: 11/04/2016
f1_keywords:
- C3183
helpviewer_keywords:
- C3183
ms.assetid: dbd0f020-c739-43c9-947e-9ce21537331b
ms.openlocfilehash: 232e9999bc31ac3e01833e7982acfb03e9d0afaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497220"
---
# <a name="compiler-error-c3183"></a>编译器错误 C3183

不能在托管的或 WinRT 类型“type”的内部定义未命名的类、结构或联合

必须命名嵌入托管的或 WinRT 类型中的类型。

下列示例生成 C3183：

```
// C3183a.cpp
// compile with: /clr /c
ref class Test
{
   ref class
   {  // C3183, delete class or name it
      int a;
      int b;
   };
};
```
