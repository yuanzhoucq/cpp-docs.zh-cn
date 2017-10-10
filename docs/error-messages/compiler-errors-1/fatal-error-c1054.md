---
title: "错误 C1054 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d02d8eb05633d7250dc3f7ee85dd78ccf4153052
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1054"></a>错误 C1054
编译器限制： 初始值设定项嵌套太深  
  
 代码超过初始值设定项 （10-15 级别，具体取决于正在初始化的类型的组合） 的嵌套限制。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  简化正在初始化以减少嵌套的数据类型。  
  
2.  初始化声明后的单独的语句中的变量。
