---
title: "AFX_EXTENSION_MODULE 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AFX_EXTENSION_MODULE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFX_EXTENSION_MODULE 结构"
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AFX_EXTENSION_MODULE 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 `AFX_EXTENSION_MODULE` MFC 扩展时使用的 DLL 初始化包含扩展 DLL 的模块状态。  
  
## 语法  
  
```  
  
      struct AFX_EXTENSION_MODULE  
{  
   BOOL bInitialized;  
   HMODULE hModule;  
   HMODULE hResource;  
   CRuntimeClass* pFirstSharedClass;  
   COleObjectFactory* pFirstSharedFactory;  
};  
```  
  
#### 参数  
 *bInitialized*  
 **TRUE**，则 DLL 初始化模块使用 `AfxInitExtensionModule`。  
  
 `hModule`  
 指定 DLL 的模块的句柄。  
  
 *hResource*  
 指定 DLL 自定义资源模块的句柄。  
  
 *pFirstSharedClass*  
 为信息 \( `CRuntimeClass` 结构\) 的指针。有关 DLL 模块的第一个运行时类。  用于提供运行时类表的开始。  
  
 *pFirstSharedFactory*  
 对 DLL 模块的指针。首先对象工厂 \( `COleObjectFactory` 对象\)。  用于提供类工厂列表的开头。  
  
## 备注  
 MFC 扩展 DLL 需要在其 `DllMain` 内容的两个函数：  
  
-   调用 [AfxInitExtensionModule](../Topic/AfxInitExtensionModule.md) 并检查返回值。  
  
-   创建 **CDynLinkLibrary** 对象的导出 DLL 是否 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象或有自己的自定义资源。  
  
 `AFX_EXTENSION_MODULE` 结构来容纳扩展 DLL 模块状态的副本，包括由扩展 DLL 初始化作为执行一般的静态对象构造的一部分运行时类对象的副本，在 `DllMain` 中输入之前。  例如：  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/CPP/afx-extension-module-structure_1.cpp)]  
  
 在 `AFX_EXTENSION_MODULE` 结构存储信息的模块可以复制到 **CDynLinkLibrary** 对象。  例如：  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/CPP/afx-extension-module-structure_2.cpp)]  
  
## 要求  
 **页眉：** afx.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](../Topic/AfxInitExtensionModule.md)   
 [AfxTermExtensionModule](../Topic/AfxTermExtensionModule.md)