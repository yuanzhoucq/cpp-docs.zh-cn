---
title: 编译器错误 C2953
ms.date: 11/04/2016
f1_keywords:
- C2953
helpviewer_keywords:
- C2953
ms.assetid: 8dbcfa24-8296-4e40-bdc4-5526c07d8892
ms.openlocfilehash: 8fa0e533b23f735f948fdad0ecf11beb3766f452
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591033"
---
# <a name="compiler-error-c2953"></a>编译器错误 C2953

“identifier”：类模板已经定义

检查源文件并包含其他定义的文件。

以下示例生成 C2953：

```
// C2953.cpp
// compile with: /c
template <class T>  class A {};
template <class T>  class A {};   // C2953
template <class T>  class B {};   // OK
```