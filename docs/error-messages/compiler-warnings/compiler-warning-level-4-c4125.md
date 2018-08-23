---
title: 编译器警告 （等级 4） C4125 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4125
dev_langs:
- C++
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af7fdd16925f080137be386cb3d2dd0dd3d8b446
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293840"
---
# <a name="compiler-warning-level-4-c4125"></a>编译器警告（等级 4）C4125
十进制数字终止八进制转义序列  
  
 编译器未用十进制数求八进制数，并假定十进制数字是一个字符。  
  
## <a name="example"></a>示例  
  
```  
// C4125a.cpp  
// compile with: /W4  
char array1[] = "\709"; // C4125  
int main()  
{  
}  
```  
  
 如果数字 9 作为一个字符，请如下更正示例：  
  
```  
// C4125b.cpp  
// compile with: /W4  
char array[] = "\0709";  // C4125 String containing "89"  
int main()  
{  
}  
```