---
title: 编译器错误 C2333
ms.date: 11/04/2016
f1_keywords:
- C2333
helpviewer_keywords:
- C2333
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
ms.openlocfilehash: e9119a8375a276a59cbf3a6db9541f6ccaef5122
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300815"
---
# <a name="compiler-error-c2333"></a>编译器错误 C2333

function： 函数声明; 中的错误跳过函数体

在另一个错误，因为成员函数在其类定义后出现此错误。

下面的示例生成 C2333:

```
// C2333.cpp
struct s1 {
   s1(s1) {}   // C2333
};
```