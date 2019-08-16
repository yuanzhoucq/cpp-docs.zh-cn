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
ms.openlocfilehash: d5e7f087f6646940777ae8b2d2a4ea888fdd3593
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495367"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl 类

此类提供[ISupportErrorInfo 接口](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)的默认实现, 并且仅当一个接口在某个对象上生成错误时才可使用。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>参数

*piid*<br/>
一个指针, 指向支持[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)的接口的 IID。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|指示由`riid`标识的接口是否支持[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)接口。|

## <a name="remarks"></a>备注

[ISupportErrorInfo 接口](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)确保可将错误信息返回到客户端。 使用`IErrorInfo`的对象必须实现`ISupportErrorInfo`。

类`ISupportErrorInfoImpl`提供的`ISupportErrorInfo`默认实现, 当只有单个接口在对象上生成错误时, 可以使用该类。 例如：

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

指示由`riid`标识的接口是否支持[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)接口。

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[ISupportErrorInfo:: InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) 。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
