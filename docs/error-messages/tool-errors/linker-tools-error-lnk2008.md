---
title: "链接器工具错误 LNK2008 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7c2fecff55677653c25c7d87fb22fa984526159
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2008"></a>链接器工具错误 LNK2008
修正目标不对齐 symbol_name  
  
 没有正确对齐的对象文件中，找到修正目标链接。  
  
 此错误可能由自定义 secton 对齐方式 (例如，#pragma[包](../../preprocessor/pack.md))，[对齐](../../cpp/align-cpp.md)修饰符，或通过修改 secton 对齐方式的程序集语言代码。  
  
 如果你的代码不使用上述任一操作，原因可能是由编译器。