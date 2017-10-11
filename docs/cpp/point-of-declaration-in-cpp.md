---
title: "C + + 中的声明点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 77f66182052cc2a031b7f1f8db8018f49b36801d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

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
  
## <a name="see-also"></a>另请参阅  
 [范围](../cpp/scope-visual-cpp.md)
