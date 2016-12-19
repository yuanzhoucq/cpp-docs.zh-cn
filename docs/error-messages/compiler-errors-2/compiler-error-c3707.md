---
title: "编译器错误 C3707 | Microsoft Docs"
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
  - "C3707"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3707"
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3707
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 调度接口方法必须有 dispid  
  
 如果使用 `dispinterface` 方法，则必须向其分配 `dispid`。  若要修复此错误，请将 `dispid` 分配给 `dispinterface` 方法，例如，通过取消注释下面示例中的方法上的 `id` 特性。  有关更多信息，请参见特性 [dispinterface](../../windows/dispinterface.md) 和 [id](../../windows/id.md)。  
  
 下面的示例生成 C3707：  
  
```  
// C3707.cpp  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(name="xx")];  
[dispinterface]  
__interface IEvents : IDispatch  
{  
   HRESULT event1([in] int i);   // C3707  
   // try the following line instead  
   // [id(1)] HRESULT event1([in] int i);  
};  
  
int main() {  
}  
```