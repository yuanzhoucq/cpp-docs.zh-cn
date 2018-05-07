---
title: 编译器警告 （等级 3） C4995 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4995
dev_langs:
- C++
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c6bf1bbab4ee9a5a08a1376c91c6a7bba160625
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4995"></a>编译器警告 （等级 3） C4995
function： 名称被标记为弃用 #pragma  
  
 编译器遇到标记有杂注的函数[弃用](../../preprocessor/deprecated-c-cpp.md)。 在未来版本中可能不再支持此函数。 你可以关闭此警告与[警告](../../preprocessor/warning.md)杂注 （例所示）。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4995:  
  
```  
// C4995.cpp  
// compile with: /W3  
#include <stdio.h>  
  
// #pragma warning(disable : 4995)  
void func1(void)  
{  
    printf("\nIn func1");  
}  
  
int main()   
{  
    func1();  
    #pragma deprecated(func1)  
    func1();   // C4995  
}  
```