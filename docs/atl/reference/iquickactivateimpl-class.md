---
title: IQuickActivateImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
dev_langs:
- C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9131a1cc1f8d0c66f2eb3616f4903db74ea4bdf0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881368"
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl 类
此类将合并到一个调用容器的控件初始化。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自`IQuickActivateImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|检索当前正在运行的控件的显示大小。|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|执行快速加载的控件的初始化。|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|通知控件容器有分配给它的显示空间。|  
  
## <a name="remarks"></a>备注  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146)界面可帮助避免延迟加载控件通过组合的单个调用中初始化时的容器。 `QuickActivate`方法，传递一个指向容器[QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630)结构，它包含所有的接口指针控件需要。 返回时，该控件将通过返回一个指向[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)包含它自己的容器使用的接口指针的结构。 类`IQuickActivateImpl`提供的默认实现`IQuickActivate`并实现`IUnknown`信息发送给转储调试中的设备生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent  
 检索当前正在运行的控件的显示大小。  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>备注  
 大小用于完全呈现控件，以 HIMETRIC 为单位指定。  
  
 请参阅[IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) Windows SDK 中。  
  
##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate  
 执行快速加载的控件的初始化。  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>备注  
 该结构包含控件和一些环境属性的值所需的接口的指针。 在返回时，控制权将传递一个指向[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)结构，其中包含指向容器要求，其自身接口和其他状态信息的指针。  
  
 请参阅[IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) Windows SDK 中。  
  
##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent  
 通知控件容器有分配给它的显示空间。  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>备注  
 以 HIMETRIC 为单位指定大小。  
  
 请参阅[IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)
