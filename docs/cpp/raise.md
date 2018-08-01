---
title: __raise |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __raise
- __raise_cpp
dev_langs:
- C++
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5ee7e0b9679fc4fd4e4cd9c541c38dd4446e47c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404361"
---
# <a name="raise"></a>__raise
强调一个事件的调用站点。  
  
## <a name="syntax"></a>语法  
  
```  
__raise method-declarator;  
```  
  
## <a name="remarks"></a>备注  
 在托管代码中，事件只能从定义它的类中引发。 请参阅[事件](../windows/event-cpp-component-extensions.md)有关详细信息。  
  
 关键字 **__raise**导致调用非事件会发出的错误。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## <a name="example"></a>示例  
  
```cpp 
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