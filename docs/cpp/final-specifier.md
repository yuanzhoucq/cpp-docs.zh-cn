---
title: "final 说明符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- final
- final_CPP
dev_langs:
- C++
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
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
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: c9f0a638707466778e75a3eabfe838c84b0355d7
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="final-specifier"></a>final 说明符
可以使用 `final` 关键字指定无法在派生类中重写的虚函数。 您还可以使用它指定无法继承的类。  
  
## <a name="syntax"></a>语法  
  
```  
  
function-declaration final;  
```  
  
```  
  
class class-name final base-classes  
```  
  
## <a name="remarks"></a>备注  
 `final` 只有在函数声明或类名称后使用时才是区分上下文的且具有特殊含义；否则，它不是保留的关键字。  
  
 在类声明中使用 `final` 时，`base-classes` 是声明的可选部分。  
  
## <a name="example"></a>示例  
 下面的示例使用 `final` 关键字指定无法重写虚函数。  
  
```cpp  
class BaseClass  
{  
    virtual void func() final;  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void func(); // compiler error: attempting to   
                         // override a final function  
};  
```  
  
 有关如何指定，可以重写成员函数的信息，请参阅[重写说明符](../cpp/override-specifier.md)。  
  
 下一个示例使用 `final` 关键字指定无法继承类。  
  
```cpp  
class BaseClass final   
{  
};  
  
class DerivedClass: public BaseClass // compiler error: BaseClass is   
                                     // marked as non-inheritable  
{  
};  
```  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [override 说明符](../cpp/override-specifier.md)
