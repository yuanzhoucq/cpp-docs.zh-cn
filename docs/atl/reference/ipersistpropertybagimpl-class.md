---
title: IPersistPropertyBagImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f214a112c1baedd507a9eeeca02e955aeceedd3e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879210"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl 类
此类实现`IUnknown`和允许对象将其属性保存到客户端提供的属性包。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自`IPersistPropertyBagImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|检索对象的 CLSID。|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|初始化新创建的对象。 ATL 实现返回 S_OK。|  
|[IPersistPropertyBagImpl::Load](#load)|从客户端提供的属性包加载对象的属性。|  
|[IPersistPropertyBagImpl::Save](#save)|将对象的属性保存到客户端提供的属性包。|  
  
## <a name="remarks"></a>备注  
 [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx)接口允许对象将其属性保存到客户端提供的属性包。 类`IPersistPropertyBagImpl`提供默认实现此接口并实现`IUnknown`信息发送给转储调试中的设备生成。  
  
 `IPersistPropertyBag` 结合工作[IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx)并[IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx)。 这后一种两个接口必须由客户端实现。 通过`IPropertyBag`，客户端将保存并加载该对象的各个属性。 通过`IErrorLog`，该对象和客户端可以报告遇到的任何错误。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="getclassid"></a>  IPersistPropertyBagImpl::GetClassID  
 检索对象的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) Windows SDK 中。  
  
##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew  
 初始化新创建的对象。  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>返回值  
 返回 S_OK。  
  
### <a name="remarks"></a>备注  
 请参阅[IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx) Windows SDK 中。  
  
##  <a name="load"></a>  IPersistPropertyBagImpl::Load  
 从客户端提供的属性包加载对象的属性。  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来检索此信息。  
  
 请参阅[IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx) Windows SDK 中。  
  
##  <a name="save"></a>  IPersistPropertyBagImpl::Save  
 将对象的属性保存到客户端提供的属性包。  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来存储此信息。 默认情况下，此方法将保存所有属性，而不考虑的值*fSaveAllProperties*。  
  
 请参阅[IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
 [类概述](../../atl/atl-class-overview.md)
