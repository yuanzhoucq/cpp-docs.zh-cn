---
title: C++ 中的声明点 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e42f43e6187e19df6e9c1111c0e92aa4b9929199
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="point-of-declaration-in-c"></a>C++ 中的声明点
名称被视为在紧靠其声明符之后，但位于其（可选）初始值设定项之前的位置进行声明。 (有关声明符的详细信息，请参阅[声明和定义](declarations-and-definitions-cpp.md)。)  
  
 请看以下示例：  
  
```  
// point_of_declaration1.cpp  
// compile with: /W1   
double dVar = 7.0;  
int main()  
{  
   double dVar = dVar;   // C4700  
}  
```  
  
 如果声明点*后*初始化，然后再在本地`dVar`将初始化为 7.0，全局变量的值`dVar`。 但是，由于情况并非如此，`dVar` 将初始化为未定义值。  
  
## <a name="see-also"></a>请参阅  
 [范围](../cpp/scope-visual-cpp.md)