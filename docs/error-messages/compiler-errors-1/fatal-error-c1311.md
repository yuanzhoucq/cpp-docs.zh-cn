---
title: 错误 C1311 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d93aa28d0cef3c07fd469349d485c4009fa4771d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091057"
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