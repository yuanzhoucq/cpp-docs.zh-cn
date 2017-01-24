---
title: "编译器错误 C3763 | Microsoft Docs"
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
  - "C3763"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3763"
ms.assetid: 58b1f079-cd1d-46e0-9431-ea18210106b7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3763
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”:“retval”和“out”只能出现在数据指针类型上  
  
 [out](../../windows/out-cpp.md) 或 [retval](../../windows/retval.md) 特性只能出现在指针类型的参数中。  或者移除该特性，或者创建指针类型的参数。  
  
 下面的示例生成 C3763：  
  
```  
// C3763.cpp  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atlcom.h>  
  
[ module(name=test) ];  
  
[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface IF84 : IDispatch  
{  
   [id(0x00000002)]HRESULT m2([out]unsigned char);  
};  
  
[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]  
class CF84 : public IF84  
{   // C3763  
public:  
   HRESULT __stdcall m2(unsigned char i)  
   {  
      return S_OK;  
   }  
};  
  
int main()  
{  
}  
```