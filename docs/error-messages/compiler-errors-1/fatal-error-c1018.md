---
title: 错误 C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 3273288f1d60fad840fd8e9c459ce5d209ddb6a4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756924"
---
# <a name="fatal-error-c1018"></a>错误 C1018

意外的 #elif

`#elif` 指令出现在 `#if`、 `#ifdef`或 `#ifndef` 构造外部。 仅在这些构造之一中使用 `#elif` 。

下面的示例生成 C1018：

```cpp
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

可能的解决方法：

```cpp
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```
