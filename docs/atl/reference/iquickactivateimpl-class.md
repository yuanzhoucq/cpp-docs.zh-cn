---
title: "IQuickActivateImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
dev_langs: C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c11185314c06e0e576d1832cef62899dd2151538
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl 类
此类将合并到一个调用容器的控件初始化。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IQuickActivateImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|检索当前正在运行的控件的显示大小。|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|执行快速初始化的控件正在加载。|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|通知控件容器有分配给它的显示空间量。|  
  
## <a name="remarks"></a>备注  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146)接口可帮助避免的延迟加载通过组合的单次调用中初始化的控件时的容器。 `QuickActivate`方法允许容器传递到一个指针[QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630)需要的所有接口控件都包含指针的结构。 返回时，该控件将通过返回一个指向[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)包含它自己由容器使用的接口指针的结构。 类`IQuickActivateImpl`提供的默认实现**IQuickActivate**并实现**IUnknown**信息发送给转储设备在调试生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent  
 检索当前正在运行的控件的显示大小。  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>备注  
 大小为完整呈现控件，并以 himetric 为单位指定。  
  
 请参阅[IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) Windows SDK 中。  
  
##  <a name="quickactivate"></a>IQuickActivateImpl::QuickActivate  
 执行快速初始化的控件正在加载。  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>备注  
 该结构包含指向接口所需的控件和一些环境属性的值。 返回时，该控件将传递指向的指针[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)包含指向容器要求，其自身接口和其他状态信息的结构。  
  
 请参阅[IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) Windows SDK 中。  
  
##  <a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent  
 通知控件容器有分配给它的显示空间量。  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>备注  
 该大小以 himetric 为单位指定。  
  
 请参阅[IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) Windows SDK 中。  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)
