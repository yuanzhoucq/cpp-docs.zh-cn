---
title: "OLE 初始化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
dev_langs: C++
helpviewer_keywords: OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 014d0679be8a03b60c2e759b36c056b35784be78
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ole-initialization"></a>OLE 初始化
必须先初始化 OLE 系统并验证 DLL 是否是正确版本，然后应用程序才能使用 OLE 系统服务。 **AfxOleInit**函数初始化 OLE 系统 Dll。  
  
### <a name="ole-initialization"></a>OLE 初始化  
  
|||  
|-|-|  
|[AfxOleInit](#afxoleinit)|初始化 OLE 库。| 
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|在应用程序对象的 `InitInstance` 函数中调用此函数以启用对包含 OLE 控件的支持。| 


## <a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer
在应用程序对象的 `InitInstance` 函数中调用此函数以启用对包含 OLE 控件的支持。  
   
### <a name="syntax"></a>语法    
```
void AfxEnableControlContainer( );  
```  
   
### <a name="remarks"></a>备注  
 有关 OLE 控件 （现在称为 ActiveX 控件） 的详细信息，请参阅[ActiveX 控件主题](../mfc-activex-controls.md)。  
   
### <a name="requirements"></a>惠?  
 **标头：** afxdisp.h  

  
##  <a name="afxoleinit"></a>AfxOleInit  
 初始化 OLE 应用程序的支持。  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零如果初始化失败，可能是因为安装了不正确版本的 OLE 系统 Dll，则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数用于初始化 OLE 支持为 MFC 应用程序。 当调用此函数时，会执行下列操作：  
  
-   初始化 COM 库调用应用程序的当前单元上。 有关详细信息，请参阅[OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134)。  
  
-   创建消息筛选器对象，实现[IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740)接口。 此消息筛选器可以访问通过调用[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)。  
  
> [!NOTE]
>  如果**AfxOleInit**称为从 MFC DLL，则调用将失败。 出现故障，因为此函数假设，如果从 DLL 调用它时，OLE 系统以前初始化由调用应用程序。  
  
> [!NOTE]
>  MFC 应用程序必须初始化为单线程单元 (STA)。 如果调用[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)中你`InitInstance`重写时，请指定`COINIT_APARTMENTTHREADED`(而非`COINIT_MULTITHREADED`)。 有关详细信息，请参阅 PRB: MFC 应用程序停止响应时初始化为多线程单元 （828643） 在应用程序[http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)。  

### <a name="requirements"></a>惠?  
 **标头：** afxdisp.h

## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
