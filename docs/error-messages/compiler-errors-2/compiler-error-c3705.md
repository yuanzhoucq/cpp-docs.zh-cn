---
title: "编译器错误 C3705 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3705"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3705"
ms.assetid: 8361017d-5782-4214-a9d7-e9825fd29bc8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3705
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：找不到事件接口  
  
 必须定义事件接口来使用 COM 事件。  请注意，使用 COM 事件需要下面的示例中所显示的 ATL 头文件的 `#include` 行。  若要修复此错误，请取消注释代码示例中 `IEvents` 接口的定义。  
  
 下面的示例生成 C3705：  
  
```  
// C3705.cpp  
// compile with: /c  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];  
  
// Uncomment the following 4 lines to resolve.  
// [object, uuid("00000000-0000-0000-0000-000000000003")]  
// __interface IEvents : IUnknown {  
//    HRESULT event1([in] int i);  
// };  
  
[dual, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IBase {  
   HRESULT fireEvents();  
};  
  
[coclass, event_source(com), uuid("00000000-0000-0000-0000-000000000002")]  
class CEventSrc : public IBase {  
public:  
   __event __interface IEvents;   // C3705 uncomment IEvents to resolve  
   HRESULT fireEvents() {  
      HRESULT hr = IEvents_event1(123);  
      return hr;  
   }  
};  
```