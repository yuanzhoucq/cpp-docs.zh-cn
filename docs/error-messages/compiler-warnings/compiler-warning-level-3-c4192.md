---
title: 编译器警告 （等级 3） C4192 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bae9b7af95de94b8f667cb09710af21044f8b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291409"
---
# <a name="compiler-warning-level-3-c4192"></a>编译器警告 （等级 3） C4192
自动导入类型库库时排除 name  
  
 A`#import`库包含的项，*名称*，即也在 Win32 系统标头文件中定义。 由于类型库的限制，等名称**IUnknown**或 GUID 通常定义在类型库中，复制从系统标头的定义。 `#import` 将检测这些项，并拒绝将它们合并在.tlh 和.tli 标头文件中。  
  
 若要重写此行为，使用`#import`属性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)和[include （)](../../preprocessor/include-parens.md)。