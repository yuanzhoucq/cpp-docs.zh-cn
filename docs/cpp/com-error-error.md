---
title: "_com_error::Error | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error.Error"
  - "_com_error::Error"
  - "Error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Error 方法"
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::Error
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 检索传递给构造函数的 `HRESULT`。  
  
## 语法  
  
```  
  
HRESULT Error( ) const throw( );  
  
```  
  
## 返回值  
 已传入构造函数的原始 `HRESULT` 项。  
  
## 备注  
 检索 `_com_error` 对象中封装的 `HRESULT` 项。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)