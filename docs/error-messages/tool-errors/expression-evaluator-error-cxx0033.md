---
title: 表达式计算器错误 CXX0033 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 720b1aec6c9be16879119bc0e8148a301507577a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0033"></a>表达式计算器错误 CXX0033
OMF 类型信息时出错  
  
 可执行文件没有有效的对象模块格式 (OMF) 以进行调试。  
  
 此错误是与 CAN0033 相同。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  可执行文件不是通过发布与此版本的 Visual c + + 链接器创建的。 重新链接使用 LINK.exe 的当前版本的对象代码。  
  
2.  .Exe 文件可能已损坏。 重新编译并重新链接程序。