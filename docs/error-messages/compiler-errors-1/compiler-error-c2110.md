---
title: 编译器错误 C2110
ms.date: 11/04/2016
f1_keywords:
- C2110
helpviewer_keywords:
- C2110
ms.assetid: 48fd76ed-90d6-4a60-9c7b-f6ce9355b4ca
ms.openlocfilehash: b20e68ec032abdfae9afb1c94fed064010275149
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646961"
---
# <a name="compiler-error-c2110"></a>编译器错误 C2110

“+L”：不能添加两个指针

尝试使用加号 ( `+` ) 运算符添加两个指针值。

以下示例生成 C2110：

```
// C2110.cpp
int main() {
   int a = 0;
   int *pa;
   int *pb;
   a = pa + pb;   // C2110
}
```