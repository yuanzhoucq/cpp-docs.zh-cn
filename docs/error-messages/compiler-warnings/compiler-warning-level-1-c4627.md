---
title: "编译器警告 （等级 1） C4627 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 66d199b8dede21f94a963113341eb6426f66a807
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4627"></a>编译器警告（等级 1）C4627
\<标识符 >： 在查找预编译标头使用时跳过  
  
 在搜索使用预编译标头的位置，编译器遇到了`#include`指令*\<标识符 >*包含文件。 编译器将忽略`#include`指令，但发出警告**C4627**如果预编译标头不包含*\<标识符 >*包含文件。  
  
## <a name="see-also"></a>请参阅  
 [创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)