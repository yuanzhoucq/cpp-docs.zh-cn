---
title: 编译器警告（等级 3）C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 7994ae05d6cb16b5ddc9775b1044de7f3a22d542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174227"
---
# <a name="compiler-warning-level-3-c4278"></a>编译器警告（等级 3）C4278

> "*identifier*"：类型库 "*tlb*" 中的标识符已经是宏;使用 "重命名" 限定符

使用[#import](../../preprocessor/hash-import-directive-cpp.md)时，要导入的类型库中的标识符试图声明标识符*标识符*。 但是，这已是一个有效符号。

使用 `#import` **rename**特性可为类型库中的符号分配别名。
