---
title: "链接器工具错误 LNK1245 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1245
dev_langs: C++
helpviewer_keywords: LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 142d88489748f30308395d64f3db78178a9b856f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1245"></a>链接器工具错误 LNK1245
无效子系统子系统指定任何引用;/ 子系统必须是 WINDOWS、 WINDOWSCE 或控制台  
  
 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)用于编译对象和以下条件之一就是 true:  
  
-   定义自定义的入口点 ([/ENTRY](../../build/reference/entry-entry-point-symbol.md))，以便链接器无法推导出子系统。  
  
-   一个值传递到[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) /clr 对象无效的链接器选项。  
  
 对于这两种情况，解决方法是指定有效的值为 /SUBSYSTEM 链接器选项。