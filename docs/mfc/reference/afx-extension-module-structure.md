---
title: "AFX_EXTENSION_MODULE 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4ac896fb16aa3c338cadd6273e226eebe986ae7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE 结构
`AFX_EXTENSION_MODULE` MFC 扩展 Dll 初始化期间中用于保存 MFC 扩展 DLL 模块的状态。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 *bInitialized*  
 **TRUE**如果 DLL 模块已初始化， `AfxInitExtensionModule`。  
  
 `hModule`  
 指定 DLL 模块的句的柄。  
  
 *hResource*  
 指定 DLL 自定义资源模块的句的柄。  
  
 *pFirstSharedClass*  
 指向信息的指针 (`CRuntimeClass`结构) 有关 DLL 模块的第一个运行时类。 用于提供运行时类列表的开头。  
  
 *pFirstSharedFactory*  
 DLL 模块的第一个对象工厂指向的指针 (`COleObjectFactory`对象)。 用于提供类工厂列表的开头。  
  
## <a name="remarks"></a>备注  
 MFC 扩展 Dll 需要执行两项操作在其`DllMain`函数：  
  
-   调用[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)并检查返回的值。  
  
-   创建**CDynLinkLibrary**对象如果 DLL 将导出[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象，或在具有其自己的自定义资源。  
  
 `AFX_EXTENSION_MODULE`结构用来保存一份 MFC 扩展 DLL 的模块状态，包括已通过 MFC 扩展 DLL 初始化为正常的静态对象构造之前执行的一部分运行时类对象的副本`DllMain`是输入。 例如:  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 中存储的模块信息`AFX_EXTENSION_MODULE`结构可以复制到**CDynLinkLibrary**对象。 例如:  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>惠?  
 **标头：** afx.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)   
 [AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)

