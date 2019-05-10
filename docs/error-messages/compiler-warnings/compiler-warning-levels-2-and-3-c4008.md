---
title: 编译器警告（等级 2 和等级 3）C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 99b78e1426cf1618e68ae74ae7e16dd0f08606ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359964"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>编译器警告（等级 2 和等级 3）C4008

“identifier”：“attribute”属性被忽略

编译器忽略了函数（级别 3 警告）或数据（等级 2 警告）的 `__fastcall`、 **static**或 **inline** 属性。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 带数据的`__fastcall` 属性。

1. 带**inline** 函数的 **static** 或 **inline** 属性。