---
title: IPropertyPage2Impl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf5cf9438d2fcecb434802dc99aaa5c692ba108f
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882892"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl 类
此类实现`IUnknown`和继承的默认实现[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自`IPropertyPage2Impl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IPropertyPage2Impl::EditProperty](#editproperty)|指定哪些属性控件接收焦点时激活的属性页。 ATL 实现返回 E_NOTIMPL。|  
  
## <a name="remarks"></a>备注  
 [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996)接口扩展[IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246)通过添加`EditProperty`方法。 此方法允许客户端在属性页对象中选择的特定属性。  
  
 类`IPropertyPage2Impl`只返回 E_NOTIMPL 为`IPropertyPage2::EditProperty`。 但是，它将继承的默认实现[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)并实现`IUnknown`信息发送给转储调试中的设备生成。  
  
 当你创建的属性页时，您的类通常派生自`IPropertyPageImpl`。 若要提供的额外支持`IPropertyPage2`、 修改其中的类定义和重写`EditProperty`方法。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPropertyPage`  
  
 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty  
 指定哪些属性控件接收焦点时激活的属性页。  
  
```
HRESULT EditProperty(DISPID dispID);
```  
  
### <a name="return-value"></a>返回值  
 返回 E_NOTIMPL。  
  
### <a name="remarks"></a>备注  
 请参阅[IPropertyPage2::EditProperty](http://msdn.microsoft.com/library/windows/desktop/ms690353) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)
