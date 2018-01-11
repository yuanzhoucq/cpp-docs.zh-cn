---
title: "编译器错误 C2390 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2390
dev_langs: C++
helpviewer_keywords: C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 93d4cbd9de274d53fdc0369c2b85dbf2e97af48f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2390"></a>编译器错误 C2390
identifier： 不正确的存储类 specifier  
  
 存储类对于全局范围标识符无效。 默认的存储类用于替换无效的类。  
  
 可能的解决方法：  
  
-   如果该标识符是一个函数，将其与声明`extern`存储。  
  
-   如果该标识符是正式参数或局部变量，则将其声明使用自动存储。  
  
-   如果该标识符是全局变量，则在使用没有任何存储类 （自动存储） 的情况下声明它。  
  
## <a name="example"></a>示例  
  
-   下面的示例生成 C2390:  
  
```  
// C2390.cpp  
register int i;   // C2390  
  
int main() {  
   register int j;   // OK  
}  
```