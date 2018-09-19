---
title: 编译器错误 C2461 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39d58b315fdd7e3c4e1899041cebf8400813ed40
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029294"
---
# <a name="compiler-error-c2461"></a>编译器错误 C2461

> '*类*： 构造函数语法缺少形参

类的构造函数不会指定任何形式的参数。 构造函数的声明必须指定形参列表。 列表可以为空。

若要解决此问题，请添加一对圆括号的声明后*类*:: **类*。

## <a name="example"></a>示例

下面的示例演示如何修复错误 C2461:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```