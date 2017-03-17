---
title: "IPropertyPageImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
caps.latest.revision: 21
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
ms.openlocfilehash: 1179e13eb33f09a363c7a3f4425a9ebf13c73b91
ms.lasthandoff: 02/24/2017

---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl 类
此类实现**IUnknown** ，并提供的默认实现[IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246)接口。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class IPropertyPageImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IPropertyPageImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IPropertyPageImpl::Activate](#activate)|创建对话框窗口的属性页。|  
|[IPropertyPageImpl::Apply](#apply)|适用于通过指定的基础对象的属性页的当前值`SetObjects`。 ATL 实现返回`S_OK`。|  
|[IPropertyPageImpl::Deactivate](#deactivate)|销毁窗口创建**激活**。|  
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|检索有关属性页上的信息。|  
|[IPropertyPageImpl::Help](#help)|调用属性页上的 Windows 的帮助。|  
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|指示是否已更改属性页上，因为它已激活。|  
|[IPropertyPageImpl::Move](#move)|定位并调整其大小属性页对话框。|  
|[IPropertyPageImpl::SetDirty](#setdirty)|标记为已更改或未更改的属性页的状态。|  
|[IPropertyPageImpl::SetObjects](#setobjects)|提供了一系列**IUnknown**与属性页关联的对象的指针。 这些对象会收到通过调用当前的属性页值**应用**。|  
|[IPropertyPageImpl::SetPageSite](#setpagesite)|提供与属性页`IPropertyPageSite`指针，通过该属性页上的通信是属性框架。|  
|[IPropertyPageImpl::Show](#show)|使属性页对话框中可见或不可见。|  
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|处理指定的键击。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|指定是否已更改属性页的状态。|  
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|将存储与描述属性页上的文本字符串关联的资源标识符。|  
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|将存储与属性页关联的帮助主题的上下文标识符。|  
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|将存储与描述属性页上的帮助文件的名称相关联的资源标识符。|  
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|将存储在属性页上的选项卡中显示的文本字符串与关联的资源标识符。|  
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|存储属性页上与关联的对象的数。|  
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|指向`IPropertyPageSite`通过其属性页上与属性框架进行通信的接口。|  
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|指向数组的**IUnknown**与属性页关联的对象的指针。|  
|[IPropertyPageImpl::m_size](#m_size)|存储的高度和宽度属性页对话框中，以像素为单位。|  
  
## <a name="remarks"></a>备注  
 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246)接口允许对象来管理在属性表中的特定属性页。 类`IPropertyPageImpl`提供此接口的默认实现，并实现**IUnknown**中调试设备信息发送给转储生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="activate"></a>IPropertyPageImpl::Activate  
 创建对话框窗口的属性页。  
  
```
HRESULT Activate(  
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```  
  
### <a name="remarks"></a>备注  
 默认情况下，对话框中始终是无模式，而不考虑值*bModal*参数。  
  
 请参阅[IPropertyPage::Activate](http://msdn.microsoft.com/library/windows/desktop/ms682250)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="apply"></a>IPropertyPageImpl::Apply  
 适用于通过指定的基础对象的属性页的当前值`SetObjects`。  
  
```
HRESULT Apply();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IPropertyPage::Apply](http://msdn.microsoft.com/library/windows/desktop/ms691284)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="deactivate"></a>IPropertyPageImpl::Deactivate  
 销毁对话框窗口使用创建[激活](#activate)。  
  
```
HRESULT Deactivate();
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPropertyPage::Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms682504)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo  
 填充*pPageInfo*结构的数据成员中包含的信息。  
  
```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>备注  
 `GetPageInfo`加载与关联的字符串资源[m_dwDocString](#m_dwdocstring)， [m_dwHelpFile](#m_dwhelpfile)，和[m_dwTitle](#m_dwtitle)。  
  
 请参阅[IPropertyPage::GetPageInfo](http://msdn.microsoft.com/library/windows/desktop/ms680714)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="help"></a>IPropertyPageImpl::Help  
 调用属性页上的 Windows 的帮助。  
  
```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPropertyPage::Help](http://msdn.microsoft.com/library/windows/desktop/ms691504)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl  
 构造函数。  
  
```
IPropertyPageImpl();
```  
  
### <a name="remarks"></a>备注  
 所有数据成员都初始化。  
  
##  <a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty  
 指示是否已更改属性页上，因为它已激活。  
  
```
HRESULT IsPageDirty(void);
```  
  
### <a name="remarks"></a>备注  
 `IsPageDirty`返回`S_OK`如果页已更改，因为它已激活。  
  
##  <a name="m_bdirty"></a>IPropertyPageImpl::m_bDirty  
 指定是否已更改属性页的状态。  
  
```
BOOL m_bDirty;
```  
  
##  <a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects  
 存储属性页上与关联的对象的数。  
  
```
ULONG m_nObjects;
```  
  
##  <a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext  
 将存储与属性页关联的帮助主题的上下文标识符。  
  
```
DWORD m_dwHelpContext;
```  
  
##  <a name="m_dwdocstring"></a>IPropertyPageImpl::m_dwDocString  
 将存储与描述属性页上的文本字符串关联的资源标识符。  
  
```
UINT m_dwDocString;
```  
  
##  <a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile  
 将存储与描述属性页上的帮助文件的名称相关联的资源标识符。  
  
```
UINT m_dwHelpFile;
```  
  
##  <a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle  
 将存储在属性页上的选项卡中显示的文本字符串与关联的资源标识符。  
  
```
UINT m_dwTitle;
```  
  
##  <a name="m_ppagesite"></a>IPropertyPageImpl::m_pPageSite  
 指向[IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583)通过其属性页上与属性框架进行通信的接口。  
  
```
IPropertyPageSite* m_pPageSite;
```  
  
##  <a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk  
 指向数组的**IUnknown**与属性页关联的对象的指针。  
  
```
IUnknown** m_ppUnk;
```  
  
##  <a name="m_size"></a>IPropertyPageImpl::m_size  
 存储的高度和宽度属性页对话框中，以像素为单位。  
  
```
SIZE m_size;
```  
  
##  <a name="move"></a>IPropertyPageImpl::Move  
 定位并调整其大小属性页对话框。  
  
```
HRESULT Move(LPCRECT pRect);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPropertyPage::Move](http://msdn.microsoft.com/library/windows/desktop/ms680118)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setdirty"></a>IPropertyPageImpl::SetDirty  
 标记为已更改或不变，具体取决于值的属性页的状态`bDirty`。  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>参数  
 `bDirty`  
 [in]如果**TRUE**，属性页的状态标记为已更改。 否则，它被标记为不变。  
  
### <a name="remarks"></a>备注  
 如有必要，`SetDirty`通知已更改属性页上的帧。  
  
##  <a name="setobjects"></a>IPropertyPageImpl::SetObjects  
 提供了一系列**IUnknown**与属性页关联的对象的指针。  
  
```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPropertyPage::SetObjects](http://msdn.microsoft.com/library/windows/desktop/ms678529)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setpagesite"></a>IPropertyPageImpl::SetPageSite  
 提供与属性页[IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583)指针，通过该属性页上的通信是属性框架。  
  
```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPropertyPage::SetPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690413)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="show"></a>IPropertyPageImpl::Show  
 使属性页对话框中可见或不可见。  
  
```
HRESULT Show(UINT nCmdShow);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPropertyPage::Show](http://msdn.microsoft.com/library/windows/desktop/ms694467)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator  
 处理中指定的击键`pMsg`。  
  
```
HRESULT TranslateAccelerator(MSG* pMsg);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPropertyPage::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms686603)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [IPropertyPage2Impl 类](../../atl/reference/ipropertypage2impl-class.md)   
 [IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)

