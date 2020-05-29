---
title: IPropertyPage2Impl 类
ms.date: 11/04/2016
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
ms.openlocfilehash: d112a2411a9debbf2eb77e6b851f4500e8d32ab8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329591"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl 类

此类实现`IUnknown`并继承[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的默认实现。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IPropertyPage2Impl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IPropertypage2impl：：编辑属性](#editproperty)|指定激活属性页时，哪个属性控件将接收焦点。 ATL 实现返回E_NOTIMPL。|

## <a name="remarks"></a>备注

[IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2)接口通过添加`EditProperty`方法扩展[IPropertyPage。](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) 此方法允许客户端在属性页对象中选择特定属性。

类`IPropertyPage2Impl`只是返回`IPropertyPage2::EditProperty`E_NOTIMPL 。 但是，它继承[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的默认实现，并通过`IUnknown`在调试版本中向转储设备发送信息实现。

创建属性页时，类通常派生自`IPropertyPageImpl`。 要提供`IPropertyPage2`的额外支持，请修改类定义并重写 该方法`EditProperty`。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPropertyPage`

[I属性页页](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="ipropertypage2impleditproperty"></a><a name="editproperty"></a>IPropertypage2impl：：编辑属性

指定激活属性页时，哪个属性控件将接收焦点。

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IPropertyPage2：编辑](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty)Windows SDK 中的属性。

## <a name="see-also"></a>另请参阅

[IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
