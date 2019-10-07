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
ms.openlocfilehash: 5ec6cb2f4fc6931a1bec429068b558bf7ac1906e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495597"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl 类

此类实现`IUnknown`并继承[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的默认实现。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IPropertyPage2Impl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|指定激活属性页时哪个属性控件将接收焦点。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

[IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2)接口`EditProperty`通过添加方法来扩展[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) 。 此方法允许客户端选择属性页对象中的特定属性。

类`IPropertyPage2Impl`只是返回`IPropertyPage2::EditProperty`E_NOTIMPL。 但是, 它继承了[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的默认实现, 并`IUnknown`通过在调试版本中将信息发送到转储设备来实现。

创建属性页时, 类通常是从派生的`IPropertyPageImpl`。 若要提供的额外支持`IPropertyPage2`, 请修改你的类定义并重`EditProperty`写方法。

**相关文章**[Atl 教程](../../atl/active-template-library-atl-tutorial.md),[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>要求

**标头:** atlctl

##  <a name="editproperty"></a>IPropertyPage2Impl::EditProperty

指定激活属性页时哪个属性控件将接收焦点。

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IPropertyPage2:: EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) 。

## <a name="see-also"></a>请参阅

[IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
