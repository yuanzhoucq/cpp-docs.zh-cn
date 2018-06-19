---
title: 编译器警告 （等级 4） C4201 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4201
dev_langs:
- C++
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56805506c112d0d92b627b905199bcbbeae8d2f7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292287"
---
# <a name="compiler-warning-level-4-c4201"></a>编译器警告（等级 4）C4201
使用的非标准扩展： 无名称结构/联合  
  
 在 Microsoft 扩展 (/Ze) 中，可以指定没有声明符的结构，作为另一个结构或联合的成员。 这些结构生成在 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。  
  
## <a name="example"></a>示例  
  
```  
// C4201.cpp  
// compile with: /W4  
struct S  
{  
   float y;  
   struct  
   {  
      int a, b, c;  // C4201  
   };  
} *p_s;  
  
int main()  
{  
}  
```