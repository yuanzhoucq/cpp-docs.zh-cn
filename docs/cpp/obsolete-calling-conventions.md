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
ms.openlocfilehash: 156482a395c7dfc8711e273141a09a37ea3e135d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188553"
---
# <a name="obsolete-calling-conventions"></a>已过时调用约定

**Microsoft 专用**

不再支持 **__pascal**、 **__fortran**和 **__syscall**调用约定。 通过使用支持的调用约定之一和适当的链接器选项，可以模拟其功能。

\<的 windows .h > 现在支持 WINAPI 宏，该宏会转换为目标的适当调用约定。 使用在以前使用 PASCAL 或 **__far \__pascal**的 WINAPI。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)
