---
title: 编译器错误 C2008 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2008
dev_langs:
- C++
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88dcbc88b50ee46b406d383ec36e1fed167eca05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165514"
---
# <a name="compiler-error-c2008"></a>编译器错误 C2008
“character”: 宏定义中的意外  
  
 在紧靠宏名称之后出现的字符。 若要解决此错误，必须有一个空格后的宏名称。  
  
 下面的示例生成 C2008:  
  
```  
// C2008.cpp  
#define TEST1"mytest1"    // C2008  
```  
  
 可能的解决方法：  
  
```  
// C2008b.cpp  
// compile with: /c  
#define TEST2 "mytest2"  
```