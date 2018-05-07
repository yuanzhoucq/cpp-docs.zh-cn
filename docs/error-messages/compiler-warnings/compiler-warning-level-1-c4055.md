---
title: 编译器警告 （等级 1） C4052 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4055
dev_langs:
- C++
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47d7d8891b589dc8205b0d799f88466c1e7d8a59
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4055"></a>编译器警告（等级 1）C4055

> *转换*： 从数据指针*type1*到函数指针*type2*

## <a name="remarks"></a>备注

**已过时：**不由 Visual Studio 2017 及更高版本生成此警告。

数据指针被（可能是错误地）强制转换为函数指针。 这是 /Za 下的 1 级警告和 /Ze 下的 4 级警告。

## <a name="example"></a>示例

以下示例生成 C4055：

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

在 /Ze 下，这是 4 级警告。

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
