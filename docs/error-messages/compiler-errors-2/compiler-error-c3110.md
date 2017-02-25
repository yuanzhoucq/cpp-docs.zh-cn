---
title: "编译器错误 C3110 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3110"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3110"
ms.assetid: 821dc71f-896e-4b2d-af0e-aa9932934b7b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3110
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function\_name”: 无法重载 COM 接口方法  
  
 以接口特性开头的接口，如：  
  
-   [自定义](../../windows/custom-cpp.md)  
  
-   [dispinterface](../../windows/dispinterface.md)  
  
-   [dual](../../windows/dual.md)  
  
-   [object](../../windows/object-cpp.md)  
  
 无法重载。  例如：  
  
```  
// C3110.cpp  
#include <unknwn.h>  
[ object, uuid= "4F98A180-EF37-11D1-978D-0000F805D73B" ]  
__interface ITestInterface  
{  
   HRESULT mf1(void);  
   HRESULT mf1(BSTR); // C3110  
};  
  
int main()  
{  
}  
```