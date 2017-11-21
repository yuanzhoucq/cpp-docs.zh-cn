---
title: "C + + 中的全局常量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f47be9bad6cf7c8ccafac5dc8ce3786f8ada0dfb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="global-constants-in-c"></a>C++ 中的全局常量
C + + 全局常量具有静态链接。 这是与 C 不同。如果你尝试使用全局常数多个文件中的 c + + 中，将得到无法解析的外部错误。 编译器优化掉全局常数，离开没有为该变量保留的空间。  
  
 若要解决此错误的一种方法是将 const 初始化包括头文件中并将该标头包括在你 CPP 文件，如有必要，就像它是函数原型。 另一种可能是让变量成为非常量并评估它时使用的常量引用。  
  
 下面的示例生成 C2019:  
  
```  
// global_constants.cpp  
// LNK2019 expected  
void test(void);  
const int lnktest1 = 0;  
  
int main() {  
   test();  
}  
```  
  
 然后，  
  
```  
// global_constants_2.cpp  
// compile with: global_constants.cpp  
extern int lnktest1;  
  
void test() {  
  int i = lnktest1;   // LNK2019  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)