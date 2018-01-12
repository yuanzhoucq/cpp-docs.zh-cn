---
title: "编译器错误 C2097 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2097
dev_langs: C++
helpviewer_keywords: C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e50154d88a5019cdc181c4921c09cbd222d8b530
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2097"></a>编译器错误 C2097
初始化非法  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  使用一个非常量值变量的初始化。  
  
2.  使用长地址短地址初始化。  
  
3.  初始化的局部结构、 联合或数组时，用非常量表达式使用编译**/Za**。  
  
4.  初始化包含逗号运算符的表达式。  
  
5.  既不常量，也不符号的表达式初始化。