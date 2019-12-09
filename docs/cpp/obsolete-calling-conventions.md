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
ms.openlocfilehash: 7f059afe02cbbad77920fd8c4a0e6cb7c958e992
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857354"
---
# <a name="obsolete-calling-conventions"></a>已过时调用约定

**Microsoft 专用**

不再支持 **__pascal**、 **__fortran**和 **__syscall**调用约定。 通过使用支持的调用约定之一和适当的链接器选项，可以模拟其功能。

\<的 windows .h > 现在支持 WINAPI 宏，该宏会转换为目标的适当调用约定。 使用在以前使用 PASCAL 或 **__far \__pascal**的 WINAPI。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)