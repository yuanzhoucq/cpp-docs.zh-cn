---
title: "OLE 初始化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
caps.latest.revision: 13
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 5c2d8a1552b8cd546b7e22683fe9f73bbc54df5c
ms.lasthandoff: 02/24/2017

---
# <a name="ole-initialization"></a>OLE 初始化
必须先初始化 OLE 系统并验证 DLL 是否是正确版本，然后应用程序才能使用 OLE 系统服务。 **AfxOleInit**函数将初始化 OLE 系统 Dll。  
  
### <a name="ole-initialization"></a>OLE 初始化  
  
|||  
|-|-|  
|[AfxOleInit](#afxoleinit)|初始化 OLE 库。|  
  
##  <a name="a-nameafxoleinita--afxoleinit"></a><a name="afxoleinit"></a>AfxOleInit  
 初始化 OLE 对应用程序的支持。  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值如果初始化失败，可能是由于安装了不正确版本的 OLE 系统动态链接库，则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数用于初始化 OLE 支持的 MFC 应用程序。 当调用此函数时，将发生以下操作︰  
  
-   初始化 COM 库调用的应用程序的当前单元上。 有关详细信息，请参阅[OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134)。  
  
-   创建消息筛选器对象，实现[IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740)接口。 此消息筛选器可以访问通过调用[AfxOleGetMessageFilter](http://msdn.microsoft.com/library/36cca011-4775-4086-b471-5557a87b266c)。  
  
> [!NOTE]
>  如果**AfxOleInit**称为从 MFC DLL，则呼叫将失败。 因为此函数假设，如果从 DLL 调用它时，OLE 系统以前初始化由调用应用程序出现故障。  
  
> [!NOTE]
>  MFC 应用程序必须初始化为单线程单元 (STA)。 如果调用[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)中您`InitInstance`重写中，指定`COINIT_APARTMENTTHREADED`(而不是`COINIT_MULTITHREADED`)。 有关详细信息，请参阅 PRB: MFC 应用程序停止响应时初始化该应用程序进行多线程单元 （828643） 在[http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)。  

### <a name="requirements"></a>要求  
 **标头：** afxdisp.h

## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

