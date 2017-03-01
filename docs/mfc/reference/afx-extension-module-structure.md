---
title: "AFX_EXTENSION_MODULE 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: f2699316266e9cc061fa898c4176e36ae8323b33
ms.lasthandoff: 02/24/2017

---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE 结构
`AFX_EXTENSION_MODULE` MFC 扩展 Dll 的初始化过程中用来保存扩展 DLL 模块的状态。  
  
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
 **TRUE** DLL 模块已初始化，如果`AfxInitExtensionModule`。  
  
 `hModule`  
 指定 DLL 模块的句柄。  
  
 *hResource*  
 指定 DLL 的自定义资源模块的句柄。  
  
 *pFirstSharedClass*  
 指向信息的指针 (`CRuntimeClass`结构) 有关 DLL 模块的第一个运行时类。 用于提供运行时类列表的开头。  
  
 *pFirstSharedFactory*  
 DLL 模块的第一个对象工厂的指针 (`COleObjectFactory`对象)。 用于提供类工厂列表的开头。  
  
## <a name="remarks"></a>备注  
 MFC 扩展 Dll 需要做两件事中的其`DllMain`函数︰  
  
-   调用[AfxInitExtensionModule](http://msdn.microsoft.com/library/15f0c820-ff34-4da6-8077-79afbbb8dac1)并检查返回的值。  
  
-   创建**CDynLinkLibrary**对象 DLL 将会导出[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象，或在具有其自己的自定义资源。  
  
 `AFX_EXTENSION_MODULE`结构用来保存一份扩展 DLL 的模块状态，包括通过扩展 DLL 初始化之前执行的普通静态对象构造过程中的运行时类对象的副本`DllMain`输入。 例如:   
  
 [!code-cpp[NVC_MFC_DLL&#2;](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 模块信息存储在`AFX_EXTENSION_MODULE`结构可以复制到**CDynLinkLibrary**对象。 例如:   
  
 [!code-cpp[NVC_MFC_DLL&#5;](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](http://msdn.microsoft.com/library/15f0c820-ff34-4da6-8077-79afbbb8dac1)   
 [AfxTermExtensionModule](http://msdn.microsoft.com/library/b64de402-f1e3-4c26-9823-08c07876aaaa)


