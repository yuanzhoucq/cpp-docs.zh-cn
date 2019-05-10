---
title: 编译器错误 C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 3b48bebde6d7baedea73ed181cd4ea33adc44a69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361329"
---
# <a name="compiler-error-c2491"></a>编译器错误 C2491

identifier： 不允许使用 dllimport 函数的定义

可以将数据、静态数据成员和函数声明为 `dllimport`，但不能定义为 `dllimport`。

若要解决此问题，请从函数定义中 `__declspec(dllimport)` 删除说明符。

以下示例生成 C2491：

```
// C2491.cpp
// compile with: /c
// function definition
void __declspec(dllimport) funcB() {}   // C2491

// function declaration
void __declspec(dllimport) funcB();   // OK
```