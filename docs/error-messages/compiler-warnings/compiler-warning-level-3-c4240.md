---
title: "编译器警告 （等级 3） C4240 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4240
dev_langs:
- C++
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 662aaeb3246fac20bd0ac9f3412424bfacac5698
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4240"></a>编译器警告（等级 3）C4240
使用的非标准扩展： 访问 classname 现在定义为访问说明符，而以前它被定义为访问说明符  
  
 在 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，不能对嵌套类更改的访问权限。 在默认的 Microsoft 扩展 (/Ze) 中，可以对，并发出以下警告。  
  
## <a name="example"></a>示例  
  
```  
// C4240.cpp  
// compile with: /W3  
class X  
{  
private:  
   class N;  
public:  
   class N  
   {   // C4240  
   };  
};  
  
int main()  
{  
}  
```