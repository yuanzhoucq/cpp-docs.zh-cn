---
title: "_com_error::WCodeToHRESULT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error::WCodeToHRESULT"
  - "_com_error.WCodeToHRESULT"
  - "WCodeToHRESULT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WCodeToHRESULT 方法"
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::WCodeToHRESULT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将 16 位 `wCode` 映射到 32 位 `HRESULT`。  
  
## 语法  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### 参数  
 `wCode`  
 要映射为 32 位 `HRESULT` 的 16 位 `wCode`。  
  
## 返回值  
 已从 16 位 `wCode` 映射的 32 位 `HRESULT`。  
  
## 备注  
 请参阅 [WCode](../cpp/com-error-wcode.md) 成员函数。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error::WCode](../cpp/com-error-wcode.md)   
 [\_com\_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [\_com\_error 类](../cpp/com-error-class.md)