---
title: NMAKE 错误 U1070 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1070
dev_langs:
- C++
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6eb462e5c3c7e497cde55151bf92c62ffb2afcd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087014"
---
# <a name="nmake-fatal-error-u1070"></a>NMAKE 错误 U1070

宏定义 macroname 中的循环

在给定的宏的定义包含其定义包含给定的宏的宏。 循环宏定义均无效。

## <a name="example"></a>示例

以下宏定义

```
ONE=$(TWO)
TWO=$(ONE)
```

会导致以下错误：

```
cycle in macro definition 'TWO'
```