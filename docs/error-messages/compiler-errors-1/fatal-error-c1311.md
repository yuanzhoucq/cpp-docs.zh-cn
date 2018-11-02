---
title: 错误 C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: ba2b797c9bf521533e7c2ccff8d358b6216d392f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637900"
---
# <a name="fatal-error-c1311"></a>错误 C1311

COFF 格式无法以静态方式初始化 var 具有地址的数字 byte （s）

其值在编译时未知的地址不能以静态方式分配给变量的类型具有不超过四个字节的存储。

在代码，否则将会出现此错误有效 c + +。

以下示例显示了可能导致 C1311 的一种情况。

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```