---
title: ISupportErrorInfoimpl 课程
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
ms.openlocfilehash: 4c60b58ba697f00b146077a2cdecd727fe2cac02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326369"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoimpl 课程

此类提供[ISupportErrorInfo 接口](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)的默认实现，当只有一个接口在对象上生成错误时，可以使用。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>参数

*皮伊德*<br/>
指向支持[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)的接口的 IID 的指针。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[ISupportErrorinfoimpl：：界面支持错误信息](#interfacesupportserrorinfo)|指示由`riid`[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)接口标识的接口是否支持。|

## <a name="remarks"></a>备注

[ISupportErrorInfo 界面](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)可确保可以将错误信息返回到客户端。 使用`IErrorInfo`的对象必须实现`ISupportErrorInfo`。

类`ISupportErrorInfoImpl`提供 的`ISupportErrorInfo`默认实现，当只有一个接口在对象上生成错误时可以使用 。 例如：

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="isupporterrorinfoimplinterfacesupportserrorinfo"></a><a name="interfacesupportserrorinfo"></a>ISupportErrorinfoimpl：：界面支持错误信息

指示由`riid`[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)接口标识的接口是否支持。

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>备注

请参阅[ISupportErrorInfo：界面支持 Windows](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) SDK 中的错误信息。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
