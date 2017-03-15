---
title: "RuntimeClass::GetIids 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass::GetIids"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetIids 方法"
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# RuntimeClass::GetIids 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取可以包含当前 RuntimeClass 对象实现的接口 ID 的数组。  
  
## 语法  
  
```  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### 参数  
 `iidCount`  
 该操作完成，元素的总数。数组 `iids`。  
  
 `iids`  
 该操作完成，对数组的指针。接口 ID。  
  
## 返回值  
 S\_OK，如果成功；否则，E\_OUTOFMEMORY。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [RuntimeClass 类](../windows/runtimeclass-class.md)