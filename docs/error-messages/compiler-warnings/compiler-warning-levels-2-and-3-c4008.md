---
title: 编译器警告（等级 2 和等级 3）C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 9b6fb56045d53cd18689f3903bb3d7a08c3d4e4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197999"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>编译器警告（等级 2 和等级 3）C4008

“identifier”：“attribute”属性被忽略

编译器忽略了函数（级别 3 警告）或数据（等级 2 警告）的 `__fastcall`、 **static**或 **inline** 属性。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 带数据的`__fastcall` 属性。

1. 带**inline** 函数的 **static** 或 **inline** 属性。
