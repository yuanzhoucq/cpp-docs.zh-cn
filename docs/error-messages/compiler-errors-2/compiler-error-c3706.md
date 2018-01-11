---
title: "编译器错误 C3706 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3706
dev_langs: C++
helpviewer_keywords: C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b33ea3c7de9afc605622cc55f4a45f73350d7db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3706"></a>编译器错误 C3706
function： 必须是一个 COM 接口激发 COM 事件  
  
 使用激发 COM 事件的事件接口必须是 COM 接口。 在此情况下，接口也应通过使用 Visual c + + 特性，定义，或使用导入[#import](../../preprocessor/hash-import-directive-cpp.md)从具有 #import 的 embedded_idl 特性的类型库。  
  
 请注意，`#include`在下面的示例所示的 ATL 标头文件的行所需的使用 COM 事件。 若要修复此错误，请`IEvents`（事件接口） 接口定义属性的 COM 接口通过应用以下项之一：[对象](../../windows/object-cpp.md)，[双重](../../windows/dual.md)，或[调度接口](../../windows/dispinterface.md)。  
  
 如果接口是从由 MIDL 生成的标头文件中，编译器将无法识别它为 COM 接口。  
  
 下面的示例生成 C3706:  
  
```  
// C3706.cpp  
// compile with: /c  
// C3706 expected  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];  
  
// Uncomment the following line to resolve.  
// [object, uuid="12341234-1234-1234-1234-123412341237"]  
__interface IEvents : IUnknown {  
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]  
};  
  
[dual, uuid="12341234-1234-1234-1234-123412341235"]  
__interface IBase {  
   HRESULT fireEvents();  
};  
  
[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]  
class CEventSrc : public IBase {  
   public:  
   __event __interface IEvents;  
  
   HRESULT fireEvents() {  
      HRESULT hr = IEvents_event1(123);  
      return hr;  
   }  
};  
```