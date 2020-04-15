---
title: 封送全局函数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: b839e93b6251a09ce79df60a49b4054d1af76cc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326267"
---
# <a name="marshaling-global-functions"></a>封送全局函数

这些函数支持将封送数据进行封送和转换到接口指针中。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|释放封送数据和`IStream`指针。|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|创建新的流对象并封送指定的接口指针。|
|[AtlUnmarshalPtr](#atlunmarshalptr)|将流的封送数据转换为接口指针。|

## <a name="requirements"></a>要求：

**标题：** atlbase.h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream

释放流中的封送数据，然后释放流指针。

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>参数

*pStream*<br/>
[在]指向用于封送`IStream`的流上的接口的指针。

### <a name="example"></a>示例

请参阅[AtlMarshalPtrInProc](#atlmarshalptrinproc)的示例。

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrinProc

创建新的流对象，将代理的 CLSID 写入流，并通过将初始化代理所需的数据写入流来封送指定接口指针。

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>参数

*朋 克*<br/>
[在]指向要封送的接口的指针。

*Iid*<br/>
[在]正在封送的接口的 GUID。

*ppStream*<br/>
[出]指向用于封送`IStream`的新流对象上的接口的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

设置MSHLFLAGS_TABLESTRONG标志，以便可以将指针封送到多个流。 指针也可以多次取消封解。

如果封送失败，将释放流指针。

`AtlMarshalPtrInProc`只能在指向进程内对象的指针上使用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr

将流的封送数据转换为可由客户端使用的接口指针。

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>参数

*pStream*<br/>
[在]指向未封解的流的指针。

*Iid*<br/>
[在]未封送接口的 GUID。

*普恩克*<br/>
[出]指向未封解接口的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="example"></a>示例

请参阅[AtlMarshalPtrInProc](#atlmarshalptrinproc)的示例。

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)
