---
title: "表达式计算器错误 CXX0033 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0033
dev_langs: C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 618dbe464adc64f36e35b9c329eb476166b8b5e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0033"></a>表达式计算器错误 CXX0033
OMF 类型信息时出错  
  
 可执行文件没有有效的对象模块格式 (OMF) 以进行调试。  
  
 此错误是与 CAN0033 相同。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  可执行文件不是通过发布与此版本的 Visual c + + 链接器创建的。 重新链接使用 LINK.exe 的当前版本的对象代码。  
  
2.  .Exe 文件可能已损坏。 重新编译并重新链接程序。