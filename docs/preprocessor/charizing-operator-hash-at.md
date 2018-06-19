---
title: 字符化运算符 (#@) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#@'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9e0c0d140d937b7359ff3abf9c0eae145a89210
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912727"
---
# <a name="charizing-operator-"></a>字符化运算符 (#@)
**Microsoft 专用**  
  
 charizing 运算符只能与宏的自变量一起使用。 如果**#@** 的形参前在宏的定义，实际自变量是用单引号括起来，在扩展宏时视为一个字符。 例如：  
  
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