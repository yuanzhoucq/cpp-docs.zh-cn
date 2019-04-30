---
title: NMAKE 错误 U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 35bea47f6626dfe283a537d3d96340921c37f3f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367234"
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