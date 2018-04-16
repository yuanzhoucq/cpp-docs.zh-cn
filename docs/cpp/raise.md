---
title: "__raise |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __raise
- __raise_cpp
dev_langs:
- C++
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a59485af5532276a125b020213e2ce01212511d9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="raise"></a>__raise
强调一个事件的调用站点。  
  
## <a name="syntax"></a>语法  
  
```  
  
__raise   
method-declarator  
;  
  
```  
  
## <a name="remarks"></a>备注  
 在托管代码中，事件只能从定义它的类中引发。 请参阅[事件](../windows/event-cpp-component-extensions.md)有关详细信息。  
  
 如果您调用了一个非事件，则关键字 `__raise` 将导致发出一个错误。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## <a name="example"></a>示例  
  
```  
// EventHandlingRef_raise.cpp  
struct E {  
   __event void func1();  
   void func1(int) {}  
  
   void func2() {}  
  
   void b() {  
      __raise func1();  
      __raise func1(1);  // C3745: 'int Event::bar(int)':   
                         // only an event can be 'raised'  
      __raise func2();   // C3745  
   }  
};  
  
int main() {  
   E e;  
   __raise e.func1();  
   __raise e.func1(1);  // C3745  
   __raise e.func2();   // C3745  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [事件处理](../cpp/event-handling.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)