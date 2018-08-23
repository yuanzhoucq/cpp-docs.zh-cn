---
title: 函数模板实例化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e773fd8e2c38311a1c36aff4c97199cbebb503e8
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406476"
---
# <a name="function-template-instantiation"></a>函数模板实例化
当首次为每个类型调用函数模板时，编译器会创建一个实例化。 每个实例化是专用于该类型的模板化函数版本。 每次将该函数用于该类型时，此实例化都将调用。 如果有几个相同的实例化，即使在不同的模块中，也只有该实例化的一个副本将在可执行文件中结束。  
  
 允许在函数模板中为其中的参数不依赖于模板自变量的任何自变量和参数对进行函数参数转换。  
  
 通过将特定类型作为参数来声明模板，可以将函数模板显示实例化。 例如，以下代码是允许的：  
  
```cpp
// function_template_instantiation.cpp  
template<class T> void f(T) { }  
  
// Instantiate f with the explicitly specified template.  
// argument 'int'  
//  
template void f<int> (int);  
  
// Instantiate f with the deduced template argument 'char'.  
template void f(char);  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [函数模板](../cpp/function-templates.md)