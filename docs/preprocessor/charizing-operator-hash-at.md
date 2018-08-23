---
title: 字符化运算符 (#@) |Microsoft Docs
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
ms.openlocfilehash: c6aa18936497f0415da331697aceb26f26345500
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42544384"
---
# <a name="charizing-operator-"></a>字符化运算符 (#@)
**Microsoft 专用**  
  
charizing 运算符只能与宏的自变量一起使用。 如果`#@`的形参前有宏的定义，在实际自变量是括在单引号内，扩展宏时视为一个字符。 例如：  
  
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