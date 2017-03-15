---
title: "IPersistPropertyBagImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistPropertyBagImpl
- ATL.IPersistPropertyBagImpl<T>
- ATL::IPersistPropertyBagImpl
- ATL::IPersistPropertyBagImpl<T>
- ATL.IPersistPropertyBagImpl
dev_langs:
- C++
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 901a6a6bf4097b6aa78a898254766f122bb2f959
ms.lasthandoff: 02/24/2017

---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl 类
此类实现**IUnknown** ，并允许将其属性保存到客户端提供的属性包的对象。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IPersistPropertyBagImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|检索对象的 CLSID。|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|初始化新创建的对象。 ATL 实现返回`S_OK`。|  
|[IPersistPropertyBagImpl::Load](#load)|从客户端提供的属性包加载对象的属性。|  
|[IPersistPropertyBagImpl::Save](#save)|将对象的属性保存到客户端提供的属性包。|  
  
## <a name="remarks"></a>备注  
 [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx)接口允许对象到客户端提供的属性包中保存它的属性。 类`IPersistPropertyBagImpl`提供此接口的默认实现，并实现**IUnknown**中调试设备信息发送给转储生成。  
  
 **IPersistPropertyBag**配合使用[IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx)和[IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx)。 这后一种两个接口必须由客户端实现。 通过`IPropertyBag`，客户端保存和加载对象的各个属性。 通过**IErrorLog**，该对象和客户端可以报告遇到的任何错误。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-namegetclassida--ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID  
 检索对象的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinitnewa--ipersistpropertybagimplinitnew"></a><a name="initnew"></a>IPersistPropertyBagImpl::InitNew  
 初始化新创建的对象。  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameloada--ipersistpropertybagimplload"></a><a name="load"></a>IPersistPropertyBagImpl::Load  
 从客户端提供的属性包加载对象的属性。  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来检索此信息。  
  
 请参阅[IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesavea--ipersistpropertybagimplsave"></a><a name="save"></a>IPersistPropertyBagImpl::Save  
 将对象的属性保存到客户端提供的属性包。  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来存储此信息。 默认情况下，此方法将保存所有属性，而不考虑值*fSaveAllProperties*。  
  
 请参阅[IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [BEGIN_PROP_MAP](http://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427)   
 [类概述](../../atl/atl-class-overview.md)

