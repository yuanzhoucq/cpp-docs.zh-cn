---
title: "AsWeak 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::AsWeak"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsWeak 函数"
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsWeak 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索对指定实例的弱引用。  
  
## 语法  
  
```  
template<  
   typename T  
>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
#### 参数  
 `T`  
 对参数 `p`的类型的指针。  
  
 `p`  
 类型的命名实例。  
  
 `pWeak`  
 该操作完成，对一弱引用的指针到参数 `p`。  
  
## 返回值  
 S\_OK，如果该操作成功的；否则，一失败原因时的错误 HRESULT。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)