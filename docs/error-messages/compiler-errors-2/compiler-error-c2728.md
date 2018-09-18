---
title: 编译器错误 C2728 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2728
dev_langs:
- C++
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe901a5798028378e6d84a807826b42cae0d64d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036158"
---
# <a name="compiler-error-c2728"></a>编译器错误 C2728

“type”：本机数组不能包含此类型

数组创建语法用于创建托管对象或 WinRT 对象的数组。 不能使用本机数组语法创建托管对象或 WinRT 对象的数组。

有关详细信息，请参阅 [数组](../../windows/arrays-cpp-component-extensions.md)。

以下示例将生成 C2728，并演示如何修复此错误：

```
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
