---
title: ISpecifyPropertyPagesImpl 类
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
ms.openlocfilehash: 06b6b60227a659bd35e042952c7464971fc40bdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326403"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl 类

此类实现`IUnknown`并提供[ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)接口的默认实现。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`ISpecifyPropertyPagesImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I 指定属性页页：获取页面](#getpages)|填充 UUID 值的计数数组。 每个 UUID 对应于可在对象的属性表中显示的属性页之一的 CLSID。|

## <a name="remarks"></a>备注

[ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)接口允许客户端获取对象支持的属性页的 CLSID 的列表。 类`ISpecifyPropertyPagesImpl`通过在调试生成中向转储设备发送`IUnknown`信息来提供此接口的默认实现和实现。

> [!NOTE]
> 如果对象不支持属性`ISpecifyPropertyPages`页，则不要公开接口。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ispecifypropertypagesimplgetpages"></a><a name="getpages"></a>I 指定属性页页：获取页面

使用可在对象的属性表中显示的属性页的 CLSID 填充[CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid)结构中的数组。

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射检索每个 CLSID。

请参阅[I 指定属性页：获取](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages)Windows SDK 中的页面。

## <a name="see-also"></a>另请参阅

[IPropertyPageImpl 类](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
