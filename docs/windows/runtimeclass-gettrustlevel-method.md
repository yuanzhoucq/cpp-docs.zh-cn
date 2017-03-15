---
title: "RuntimeClass::GetTrustLevel 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass::GetTrustLevel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetTrustLevel 方法"
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# RuntimeClass::GetTrustLevel 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取当前 RuntimeClass 对象的信任级别。  
  
## 语法  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
## 参数  
 `trustLvl`  
 该操作完成，当前RuntimeClass对象的信任级别。  
  
## 返回值  
 始终是 S\_OK。  
  
## 备注  
 如果\_\_WRL\_STRICT\_\_or \_\_WRL\_FORCE\_INSPECTABLE\_CLASS\_MACRO 未定义，断言错误发出。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [RuntimeClass 类](../windows/runtimeclass-class.md)