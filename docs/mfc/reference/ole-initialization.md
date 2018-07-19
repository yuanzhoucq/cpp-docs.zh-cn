---
title: OLE 初始化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
dev_langs:
- C++
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 330701c4fcc75d40e782d25baa55044b88852f50
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337787"
---
# <a name="ole-initialization"></a>OLE 初始化
必须先初始化 OLE 系统并验证 DLL 是否是正确版本，然后应用程序才能使用 OLE 系统服务。 `AfxOleInit`函数将初始化 OLE 系统 Dll。  
  
### <a name="ole-initialization"></a>OLE 初始化  
  
|||  
|-|-|  
|[AfxOleInit](#afxoleinit)|初始化 OLE 库。| 
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|在应用程序对象的 `InitInstance` 函数中调用此函数以启用对包含 OLE 控件的支持。| 


## <a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer
在应用程序对象的 `InitInstance` 函数中调用此函数以启用对包含 OLE 控件的支持。  
   
### <a name="syntax"></a>语法    
```
void AfxEnableControlContainer( );  
```  
   
### <a name="remarks"></a>备注  
 有关 OLE 控件 （现在称为 ActiveX 控件） 的详细信息，请参阅[ActiveX 控件主题](../mfc-activex-controls.md)。  
   
### <a name="requirements"></a>要求  
 **标头：** afxdisp.h  

  
##  <a name="afxoleinit"></a>  AfxOleInit  
 初始化 OLE 应用程序的支持。  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值如果初始化失败，可能是因为安装了不正确版本的 OLE 系统 Dll，则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数以初始化 OLE 支持 MFC 应用程序。 当调用此函数时，将执行以下操作：  
  
-   初始化 COM 库调用的应用程序的当前单元上。 有关详细信息，请参阅[OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134)。  
  
-   创建消息筛选器对象，实现[IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740)接口。 此消息筛选器可以访问通过调用[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)。  
  
> [!NOTE]
>  如果**AfxOleInit**调用从非 MFC DLL，则调用将失败。 出现故障，因为该函数假定，如果调用从 DLL 时，OLE 系统之前已初始化的调用应用程序。  
  
> [!NOTE]
>  MFC 应用程序必须初始化为单线程单元 (STA)。 如果您调用[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)在你`InitInstance`重写中，指定 COINIT_APARTMENTTHREADED （而非 COINIT_MULTITHREADED）。 有关详细信息，请参阅 PRB: MFC 应用程序停止响应时初始化为多线程单元 （828643） 在应用程序[ http://support.microsoft.com/default.aspxscid=kb; en-我们; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)。  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h

## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
