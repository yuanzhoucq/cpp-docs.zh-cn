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
ms.openlocfilehash: 3f5db65d1c318677a630307f44533e51d63ec44d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197414"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl 类

此类实现`IUnknown`，并提供的默认实现[ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages)接口。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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

|名称|描述|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|填充值的计数的 UUID 的数组。 每个 UUID 对应于一个可以显示对象的属性表中的属性页的 CLSID。|

## <a name="remarks"></a>备注

[ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages)接口允许客户端获取支持的对象的属性页的 Clsid 的列表。 类`ISpecifyPropertyPagesImpl`提供默认实现此接口并实现`IUnknown`信息发送给转储调试中的设备生成。

> [!NOTE]
>  不会公开`ISpecifyPropertyPages`接口如果您的对象不支持属性页。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages

填充数组[CAUUID](/windows/desktop/api/ocidl/ns-ocidl-tagcauuid)结构可以显示对象的属性表中的属性页的 Clsid。

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射来检索每个 CLSID。

请参阅[ISpecifyPropertyPages::GetPages](/windows/desktop/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) Windows SDK 中。

## <a name="see-also"></a>请参阅

[IPropertyPageImpl 类](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
