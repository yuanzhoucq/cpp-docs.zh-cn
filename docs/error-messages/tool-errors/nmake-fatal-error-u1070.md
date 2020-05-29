---
title: NMAKE 错误 U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 008d49df3460cb7cf760e4b278db20da444555fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182768"
---
# <a name="nmake-fatal-error-u1070"></a>NMAKE 错误 U1070

宏定义 "macroname" 中的循环

给定宏定义包含一个宏，其定义中包含了给定的宏。 循环宏定义无效。

## <a name="example"></a>示例

以下宏定义

```
ONE=$(TWO)
TWO=$(ONE)
```

导致以下错误：

```
cycle in macro definition 'TWO'
```
