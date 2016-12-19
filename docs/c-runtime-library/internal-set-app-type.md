---
title: "__set_app_type | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__set_app_type"
  - "_set_app_type"
apilocation: 
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__set_app_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__set_app_type"
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __set_app_type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

设置当前应用类型。  
  
## 语法  
  
```cpp  
void __set_app_type (  
   int at  
   )  
```  
  
#### 参数  
 `at`  
 指示应用程序类型的值。  可能的值包括：  
  
|值|说明|  
|-------|--------|  
|\_UNKNOWN\_APP|未知应用程序类型。|  
|\_CONSOLE\_APP|控制台 \(命令行\) 应用程序。|  
|\_GUI\_APP|\(GUI\) Windows 应用程序。|  
  
## 备注  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_\_set\_app\_type|internal.h|