---
title: 编译器警告（等级 3）C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 8c5c15105581602566116d3ed82b89a6337435c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627625"
---
# <a name="compiler-warning-level-3-c4278"></a>编译器警告（等级 3）C4278

> '*标识符*： 类型库中的标识符*tlb*已经是宏; 使用 rename 限定符

使用时[#import](../../preprocessor/hash-import-directive-cpp.md)，您要导入类型库中的标识符，尝试声明标识符*标识符*。 但是，这已是有效的符号。

使用`#import`**重命名**属性分配到类型库中的符号的别名。