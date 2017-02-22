---
title: "RuntimeClass::GetRuntimeClassName 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRuntimeClassName 方法"
ms.assetid: f6388163-fe65-4948-a4bc-ae6826f480e7
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# RuntimeClass::GetRuntimeClassName 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取当前 RuntimeClass 对象的运行时类名。  
  
## 语法  
  
```  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
## 参数  
 `runtimeName`  
 该操作完成，运行时类名。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 备注  
 如果\_\_WRL\_STRICT\_\_or \_\_WRL\_FORCE\_INSPECTABLE\_CLASS\_MACRO 未定义，断言错误发出。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [RuntimeClass 类](../windows/runtimeclass-class.md)