---
title: "编译器警告 （等级 3） C4192 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 022c0e0aac8d231963ddf6d5d3715d55f726a8b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4192"></a>编译器警告 （等级 3） C4192
自动导入类型库库时排除 name  
  
 A`#import`库包含的项，*名称*，即也在 Win32 系统标头文件中定义。 由于类型库的限制，等名称**IUnknown**或 GUID 通常定义在类型库中，复制从系统标头的定义。 `#import`将检测这些项，并拒绝将它们合并在.tlh 和.tli 标头文件中。  
  
 若要重写此行为，使用`#import`属性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)和[include （)](../../preprocessor/include-parens.md)。