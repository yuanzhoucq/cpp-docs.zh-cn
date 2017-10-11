---
title: "错误 C1071 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1071
dev_langs:
- C++
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: acd48401d3abc17d994e861bf6fb046450d88ca6
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1071"></a>错误 C1071
在注释中遇到意外的文件结束  
  
 在扫描注释时，编译器到达文件末尾。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  缺少注释终止符 (* /)。  
  
2.  源文件的最后一行注释后缺少的换行符。  
  
 下面的示例生成 C1071:  
  
```  
// C1071.cpp  
int main() {  
}  
  
/* this comment is fine */  
/* forgot the closing tag        // C1071  
```
