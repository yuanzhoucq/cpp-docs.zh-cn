---
title: 编译器错误 C2041
ms.date: 11/04/2016
f1_keywords:
- C2041
helpviewer_keywords:
- C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
ms.openlocfilehash: 7e148ced19e34a57172e3d606c6efdb2f5d012d6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740450"
---
# <a name="compiler-error-c2041"></a>编译器错误 C2041

基 "number" 的非法数字 "character"

指定的字符不是基的有效数字（如八进制或十六进制）。

下面的示例生成 C2041：

```cpp
// C2041.cpp
int i = 081;   // C2041  8 is not a base 8 digit
```

可能的解决方法：

```cpp
// C2041b.cpp
// compile with: /c
int j = 071;
```
