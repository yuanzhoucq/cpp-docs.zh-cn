---
title: "__super |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __super_cpp
- __super
dev_langs:
- C++
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
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
ms.openlocfilehash: 64600f8cf642b0c7906873a73aa4da41897a57f5
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="super"></a>__super
**Microsoft 专用**  
  
 允许您显式说明要为正在重写的函数调用基类实现。  
  
## <a name="syntax"></a>语法  
  
```  
  
__super::  
member_function  
();  
  
```  
  
## <a name="remarks"></a>备注  
 在重载决策阶段将考虑所有可访问的基类方法，可提供最佳匹配项的函数就是调用的函数。  
  
 `__super` 只能在成员函数体内显示。  
  
 `__super` 不能与声明一起使用。 请参阅[using 声明](../cpp/using-declaration.md)有关详细信息。  
  
 通过引入[属性](../windows/cpp-attributes-reference.md)插入代码，你的代码可能包含一个或多个基类，您可能不知道但其名称包含你想要调用的方法。  
  
## <a name="example"></a>示例  
  
```  
// deriv_super.cpp  
// compile with: /c  
struct B1 {  
   void mf(int) {}  
};  
  
struct B2 {  
   void mf(short) {}  
  
   void mf(char) {}  
};  
  
struct D : B1, B2 {  
   void mf(short) {  
      __super::mf(1);   // Calls B1::mf(int)  
      __super::mf('s');   // Calls B2::mf(char)  
   }  
};  
```  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)
