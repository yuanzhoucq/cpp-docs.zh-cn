---
title: 编译器警告（等级4） C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 6786d692785dbca575d4b241b7b3e3d40575b686
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198544"
---
# <a name="compiler-warning-level-4-c4092"></a>编译器警告（等级4） C4092

sizeof 返回 "无符号长"

`sizeof` 运算符的操作数非常大，因此 `sizeof` 返回无符号**长**整数。 此警告出现在 Microsoft 扩展（[/ze](../../build/reference/za-ze-disable-language-extensions.md)）下。 在 ANSI 兼容性（/Za）下，将改为截断结果。
