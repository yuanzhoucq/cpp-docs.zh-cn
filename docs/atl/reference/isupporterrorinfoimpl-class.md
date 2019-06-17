---
title: ISupportErrorInfoImpl 类
ms.date: 06/13/2019
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: 650d90c9ec98754e11586f63e0871b70ebbe34f3
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141708"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl 类

此类提供的默认实现[ISupportErrorInfo 接口](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)和单个接口在生成对象上的错误时，可以使用。

> [!IMPORTANT]
> 不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>参数

*piid*<br/>
指向支持的接口的 IID [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|指示标识接口是否`riid`支持[IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)接口。|

## <a name="remarks"></a>备注

[ISupportErrorInfo 接口](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)可确保错误信息，可以返回到客户端。 对象使用`IErrorInfo`必须实现`ISupportErrorInfo`。

类`ISupportErrorInfoImpl`提供的默认实现`ISupportErrorInfo`和单个接口在生成对象上的错误时，可以使用。 例如：

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

指示标识接口是否`riid`支持[IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)接口。

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>备注

请参阅[ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) Windows SDK 中。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
