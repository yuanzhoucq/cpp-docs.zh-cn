---
title: "函数模板的显式专用化 |Microsoft 文档"
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
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions, specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: f460497071445cff87308fa9bf6e0d43c6f13a3e
ms.openlocfilehash: c5caabae41383edbdc92806249026ce8a0daa5d5
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="explicit-specialization-of-function-templates"></a>函数模板的显式专用化
利用函数模板，您可以通过为特定类型提供函数模板的显式专用化（重写）来定义该类型的特殊行为。 例如:   
  
```cpp
template<> void MySwap(double a, double b);  
```  
  
 此声明使您能够定义不同函数的**double**变量。 如非模板函数，标准类型转换 (如类型的变量提升**float**到**double**) 应用。  
  
## <a name="example"></a>示例  
  
```cpp
// explicit_specialization.cpp  
template<class T> void f(T t)  
{  
};  
  
// Explicit specialization of f with 'char' with the  
// template argument explicitly specified:  
//  
template<> void f<char>(char c)  
{  
}  
  
// Explicit specialization of f with 'double' with the  
// template argument deduced:  
//  
template<> void f(double d)  
{  
}  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [函数模板](../cpp/function-templates.md)

