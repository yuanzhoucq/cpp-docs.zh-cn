---
title: 编译器警告 （等级 4） C4220 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4220
dev_langs:
- C++
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f5a48bc836bbead8bc9004f797855fcc4c1baaf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294162"
---
# <a name="compiler-warning-level-4-c4220"></a>编译器警告（等级 4）C4220
varargs 匹配其余参数  
  
 在默认的 Microsoft 扩展 (/Ze) 中，指向函数的指针与指向具有类似，但变量，自变量的函数的指针相匹配。  
  
## <a name="example"></a>示例  
  
```  
// C4220.c  
// compile with: /W4  
  
int ( *pFunc1) ( int a, ... );  
int ( *pFunc2) ( int a, int b);  
  
int main()  
{  
   if ( pFunc1 != pFunc2 ) {};  // C4220  
}  
```  
  
 此类指针不匹配在 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。