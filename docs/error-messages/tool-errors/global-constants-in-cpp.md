---
title: C + + 中的全局常量 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f1ee5fdf3d50f30e02bd48fe3664c10d26a8449
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>请参阅  
 [链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)