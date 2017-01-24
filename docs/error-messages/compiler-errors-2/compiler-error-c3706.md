---
title: "编译器错误 C3706 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3706"
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3706
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 激发 COM 事件必须是 COM 接口  
  
 用于引发 COM 事件的事件接口必须是 COM 接口。  在此情况下，该接口应使用 Visual C\+\+ 特性进行定义，或者使用 [\#import](../../preprocessor/hash-import-directive-cpp.md) 从具有 \#import 的 embedded\_idl 特性的类型库中导入。  
  
 请注意，使用 COM 事件需要下面的示例中所显示的 ATL 头文件的 `#include` 行。  若要修复此错误，请通过将以下特性之一应用于接口定义，使 `IEvents`（事件接口）成为 COM 接口：[object](../../windows/object-cpp.md)、[dual](../../windows/dual.md) 或 [dispinterface](../../windows/dispinterface.md)。  
  
 如果接口来自 MIDL 生成的头文件，则编译器不会将其识别为 COM 接口。  
  
 下面的示例生成 C3706：  
  
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