---
title: "编译器警告 （等级 1） C4005 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4005
dev_langs: C++
helpviewer_keywords: C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf0c5777cecf89bb0723b30c87dc4c856de0a016
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4005"></a>编译器警告 （等级 1） C4005
identifier： 宏重定义  
  
 宏标识符定义了两次。 编译器使用在第二个宏的定义。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  定义宏，在命令行和在代码中使用`#define`指令。  
  
2.  从包含文件导入的宏。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  删除其中一个定义。  
  
2.  使用[#undef](../../preprocessor/hash-undef-directive-c-cpp.md)指令之前第二个定义。  
  
 下面的示例生成 C4005:  
  
```  
// C4005.cpp  
// compile with: /W1 /EHsc  
#include <iostream>  
using namespace std;  
  
#define TEST "test1"  
#define TEST "test2"   // C4005 delete or rename to resolve the warning  
  
int main() {  
   cout << TEST << endl;  
}  
```