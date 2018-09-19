---
title: NMAKE 错误 U1001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1001
dev_langs:
- C++
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4e465af5b4fa22c5f0ba5a9e01ebde0a7ee89e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068138"
---
# <a name="nmake-fatal-error-u1001"></a>NMAKE 错误 U1001

语法错误： 非法字符 character 在宏

给定的字符出现在宏中，而不是字母、 数字或下划线。

此错误可能被引起宏扩展中缺少冒号：

```
syntax error : illegal character '=' in macro
```