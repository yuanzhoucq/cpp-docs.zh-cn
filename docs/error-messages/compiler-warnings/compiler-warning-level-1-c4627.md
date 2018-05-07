---
title: 编译器警告 （等级 1） C4627 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcde9e6707465fd95dbcb10e073a852624f0de0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4627"></a>编译器警告（等级 1）C4627
\<标识符 >： 在查找预编译标头使用时跳过  
  
 在搜索使用预编译标头的位置，编译器遇到了`#include`指令*\<标识符 >* 包含文件。 编译器将忽略`#include`指令，但发出警告**C4627**如果预编译标头不包含*\<标识符 >* 包含文件。  
  
## <a name="see-also"></a>请参阅  
 [创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)