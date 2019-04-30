---
title: NMAKE 错误 U1001
ms.date: 11/04/2016
f1_keywords:
- U1001
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
ms.openlocfilehash: bfe2edf9c57eda073826a8c161ae0c358f3a6232
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378448"
---
# <a name="nmake-fatal-error-u1001"></a>NMAKE 错误 U1001

语法错误： 非法字符 character 在宏

给定的字符出现在宏中，而不是字母、 数字或下划线。

此错误可能被引起宏扩展中缺少冒号：

```
syntax error : illegal character '=' in macro
```