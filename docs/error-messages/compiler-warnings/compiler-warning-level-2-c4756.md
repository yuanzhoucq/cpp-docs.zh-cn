---
title: 编译器警告 （等级 2） C4756 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4756
dev_langs:
- C++
helpviewer_keywords:
- C4756
ms.assetid: 5a16df83-6b82-4619-83bd-319af4ef1d1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b80596ede2cc93e64b79b1d5c08e091a880c7771
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086611"
---
# <a name="compiler-warning-level-2-c4756"></a>编译器警告（等级 2）C4756

常量算法中溢出

编译器生成在编译期间执行常数算法时出现异常。

下面的示例生成 C4756:

```
// C4756.cpp
// compile with: /W2 /Od
int main()
{
   float f = 1e100+1e100;   // C4756
}
```