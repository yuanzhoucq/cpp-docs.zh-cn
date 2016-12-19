---
title: "lock::operator== | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "lock::operator=="
  - "msclr.lock.operator=="
  - "msclr::lock::operator=="
  - "lock.operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock::operator=="
ms.assetid: 3dcf1e5a-53fc-495d-9df5-d7849a41c36c
caps.latest.revision: 6
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock::operator==
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

相等运算符。  
  
## 语法  
  
```  
template<class T> bool operator==(  
   T t  
);  
```  
  
#### 参数  
 `t`  
 要比较是否相等的对象。  
  
## 返回值  
 返回 `true`，如果 `t` 与锁的对象，则为 `false`。  
  
## 示例  
  
```  
// msl_lock_op_eq.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
int main () {  
   Object^ o1 = gcnew Object;  
   lock l1(o1);  
   if (l1 == o1) {  
      Console::WriteLine("Equal!");  
   }  
}  
```  
  
  **Equal\!**   
## 要求  
 **Header file** \<msclr\\lock.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [锁定成员](../dotnet/lock-members.md)   
 [lock::operator\!\=](../dotnet/lock-operator-inequality.md)