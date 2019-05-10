---
title: 编译器错误 C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 72646d7611163748fe7e27ea6c78cd38426eb6ad
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447814"
---
# <a name="compiler-error-c3279"></a>编译器错误 C3279

不允许对在 cli 命名空间中声明的类模板进行部分专用化、显式专用化和显式实例化

`cli` 命名空间由 Microsoft 定义并包含伪模板。 MicrosoftC++编译器不允许使用用户定义的、 部分和显式专用化和显式实例化类模板的此命名空间中。

以下示例生成 C3279：

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```