---
title: 已过时调用约定
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 86c75c779158d9f191dd015410cf16c9ce25690d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245011"
---
# <a name="obsolete-calling-conventions"></a>已过时调用约定

## <a name="microsoft-specific"></a>Microsoft 专用

**__Pascal**， **__fortran**，并 **__syscall**调用约定不再受支持。 通过使用支持的调用约定之一和适当的链接器选项，可以模拟其功能。

\<windows.h > 现在支持 WINAPI 宏，这会转换为目标的适当调用约定。 使用以前使用 PASCAL WINAPI 或 **__far \__pascal**。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)