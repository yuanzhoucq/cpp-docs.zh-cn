---
title: "_com_error::WCode | Microsoft Docs"
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
  - "_com_error.WCode"
  - "_com_error::WCode"
  - "WCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WCode 方法"
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::WCode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 检索映射到封装的 `HRESULT` 中的 16 位错误代码。  
  
## 语法  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## 返回值  
 如果 `HRESULT` 在范围 0x80040200 到 0x8004FFFF 内，**WCode** 方法将返回 `HRESULT` 减去 0x80040200；否则，该方法返回零。  
  
## 备注  
 **WCode** 方法用于撤消发生在 COM 支持代码中的映射。  **dispinterface** 属性或方法的包装器将调用打包参数的支持例程并调用 **IDispatch::Invoke**。  当调用返回后，如果返回了 `DISP_E_EXCEPTION` 的失败 `HRESULT`，则从传递到 **IDispatch::Invoke** 的 **EXCEPINFO** 结构检索错误信息。  错误代码可能是存储在 **EXCEPINFO** 结构的 `wCode` 成员中的 16 位值或存储在 **EXCEPINFO** 结构的 **scode** 成员中的完整的 32 位值。  如果返回了 16 位 `wCode`，则必须先将其映射到 32 位失败 `HRESULT`。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [\_com\_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [\_com\_error 类](../cpp/com-error-class.md)