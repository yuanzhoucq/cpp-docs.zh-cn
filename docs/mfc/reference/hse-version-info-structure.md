---
title: "HSE_VERSION_INFO 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "HSE_VERSION_INFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HSE_VERSION_INFO 结构"
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# HSE_VERSION_INFO 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由 `CHttpServer::GetExtensionVersion` 成员函数的 `pVer` 参数指向的结构。  它提供 ISA 版本号、ISA 的文本说明。  
  
## 语法  
  
```  
  
      typedef struct _HSE_VERSION_INFO {  
   DWORD dwExtensionVersion;  
   CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### 参数  
 *dwExtensionVersion*  
 ISA 的版本号。  
  
 *lpszExtensionDesc*  
 ISA 的文本说明。  默认实现提供占位符文本；重写提供说明的 `CHttpServer::GetExtensionVersion` 。  
  
## 要求  
 **头文件：** httpext.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)