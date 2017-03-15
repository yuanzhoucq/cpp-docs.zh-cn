---
title: "IQuickActivateImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IQuickActivateImpl
- ATL::IQuickActivateImpl<T>
- ATL.IQuickActivateImpl
- ATL.IQuickActivateImpl<T>
- IQuickActivateImpl
dev_langs:
- C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
caps.latest.revision: 20
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4f6b75da64efa12e43fa160c57da4291acae03ca
ms.lasthandoff: 02/24/2017

---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl 类
此类可将合并到一个调用容器的控件初始化。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IQuickActivateImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|检索当前显示为正在运行的控件的大小。|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|执行快速初始化控件正在加载。|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|通知控件容器有分配给它的显示空间。|  
  
## <a name="remarks"></a>备注  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146)界面可帮助避免出现延迟，在通过组合的单个调用中的初始化加载控件时的容器。 `QuickActivate`方法允许将指针传递至容器[QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630)需要的所有接口控件都包含指针的结构。 返回时，该控件将通过返回一个指向[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)包含它自己由容器使用的接口指针的结构。 类`IQuickActivateImpl`提供的默认实现**IQuickActivate**并实现**IUnknown**中调试设备信息发送给转储生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="a-namegetcontentextenta--iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent  
 检索当前显示为正在运行的控件的大小。  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>备注  
 大小是完全呈现控件，以 himetric 为单位指定。  
  
 请参阅[IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namequickactivatea--iquickactivateimplquickactivate"></a><a name="quickactivate"></a>IQuickActivateImpl::QuickActivate  
 执行快速初始化控件正在加载。  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>备注  
 该结构包含该控件和一些环境属性的值所需的接口指针。 返回时，该控件将传递一个指向[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)结构，其中包含指向它自己的容器，它需要的接口和其他状态信息。  
  
 请参阅[IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetcontentextenta--iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent  
 通知控件容器有分配给它的显示空间。  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>备注  
 以 himetric 为单位指定大小。  
  
 请参阅[IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)

