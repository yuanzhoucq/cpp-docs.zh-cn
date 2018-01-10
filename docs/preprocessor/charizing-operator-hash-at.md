---
title: "字符化运算符 (#@) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#@'
dev_langs: C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 933e97732462b61919d9e5a1e73f2a72d26ea01b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="charizing-operator-"></a>字符化运算符 (#@)
**Microsoft 专用**  
  
 charizing 运算符只能与宏的自变量一起使用。 如果 **#@** 的形参前在宏的定义，实际自变量是用单引号括起来，在扩展宏时视为一个字符。 例如:  
  
```  
#define makechar(x)  #@x  
```  
  
 导致以下语句  
  
```  
a = makechar(b);  
```  
  
 扩展为  
  
```  
a = 'b';  
```  
  
 单引号字符不能与 charizing 运算符一起使用。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [预处理器运算符](../preprocessor/preprocessor-operators.md)