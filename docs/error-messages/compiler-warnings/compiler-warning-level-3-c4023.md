---
title: 编译器警告（等级 3）C4023
ms.date: 11/04/2016
f1_keywords:
- C4023
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
ms.openlocfilehash: 4d433ff7d6b323fcb8508872d4e755f893a50f5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402354"
---
# <a name="compiler-warning-level-3-c4023"></a>编译器警告（等级 3）C4023

“symbol”：基指针传递到非原型函数：参数数目

将基指针传递给非原型函数会导致该指针被正常化，并产生不可预知的结果。

如果你使用传递基指针的原型函数，则可能会修复此警告。