---
title: 编译器警告 （等级 3） C4278 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4278
dev_langs:
- C++
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f63337de2e14b1cb0f9d854df962ab2aa9c8014e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205776"
---
# <a name="compiler-warning-level-3-c4278"></a>编译器警告（等级 3）C4278

> '*标识符*： 类型库中的标识符*tlb*已经是宏; 使用 rename 限定符

使用时[#import](../../preprocessor/hash-import-directive-cpp.md)，您要导入类型库中的标识符，尝试声明标识符*标识符*。 但是，这已是有效的符号。

使用`#import`**重命名**属性分配到类型库中的符号的别名。