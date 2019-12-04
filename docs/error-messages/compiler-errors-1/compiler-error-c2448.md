---
title: 编译器错误 C2448
ms.date: 11/04/2016
f1_keywords:
- C2448
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
ms.openlocfilehash: 8a71fe05e2a046a65b659840f94d104a3c526778
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744155"
---
# <a name="compiler-error-c2448"></a>编译器错误 C2448

"identifier"：函数样式初始值设定项显示为函数定义

函数定义不正确。

此错误可能由旧式 C 语言形式列表引起。

下面的示例生成 C2448：

```cpp
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```
