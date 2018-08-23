---
title: 编译器警告 （等级 4） C4211 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4211
dev_langs:
- C++
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8112927940e5e2f17a4e74e2855a035bc7d5e5cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292342"
---
# <a name="compiler-warning-level-4-c4211"></a>编译器警告（等级 4）C4211
使用的非标准扩展： 重新定义为静态 extern  
  
 具有默认的 Microsoft 扩展 (/Ze) 中，您可以重新定义`extern`标识符，则为**静态**。  
  
## <a name="example"></a>示例  
  
```  
// C4211.c  
// compile with: /W4  
extern int i;  
static int i;   // C4211  
  
int main()  
{  
}  
```  
  
 此类重新定义是在 ANSI 兼容性无效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。  
  
## <a name="see-also"></a>请参阅  


