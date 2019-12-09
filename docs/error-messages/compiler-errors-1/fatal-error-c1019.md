---
title: 错误 C1019
ms.date: 11/04/2016
f1_keywords:
- C1019
helpviewer_keywords:
- C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
ms.openlocfilehash: f33139393f7f6225edf0c4b3f992b93d35bd6afa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756911"
---
# <a name="fatal-error-c1019"></a>错误 C1019

意外的 #else

`#else` 指令出现在 `#if`、 `#ifdef`或 `#ifndef` 构造外部。 仅在这些构造之一中使用 `#else` 。

下面的示例生成 C1019：

```cpp
// C1019.cpp
#else   // C1019
#endif

int main() {}
```

可能的解决方法：

```cpp
// C1019b.cpp
#if 1
#else
#endif

int main() {}
```
