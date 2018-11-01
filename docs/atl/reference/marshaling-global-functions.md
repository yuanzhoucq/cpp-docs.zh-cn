---
title: 封送全局函数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: dadaf119f8f1d0aefb4f5b4b740747a2794d271e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554399"
---
# <a name="marshaling-global-functions"></a>封送全局函数

这些函数提供支持封送处理和封送处理的数据转换为接口指针。

> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|释放的封送数据和`IStream`指针。|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|创建新的流对象，并将封送指定的接口指针。|
|[AtlUnmarshalPtr](#atlunmarshalptr)|将接口指针转换为流的封送处理数据。|

## <a name="requirements"></a>要求：

**标头：** atlbase.h

##  <a name="atlfreemarshalstream"></a>  AtlFreeMarshalStream

释放流中的封送数据，然后释放流指针。

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>参数

*pStream*<br/>
[in]一个指向`IStream`用于封送处理的流上的接口。

### <a name="example"></a>示例

有关示例，请参阅[AtlMarshalPtrInProc](#atlmarshalptrinproc)。

##  <a name="atlmarshalptrinproc"></a>  AtlMarshalPtrInProc

创建新的流对象，将代理的 CLSID 写入流，并通过将初始化代理所需的数据写入流来封送指定接口指针。

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
[in]指向要封送的接口的指针。

*iid*<br/>
[in]正在封送的接口的 GUID。

*ppStream*<br/>
[out]一个指向`IStream`上新的流对象用于封送处理的接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

因此可以将指针封送到多个流设置 MSHLFLAGS_TABLESTRONG 标志。 指针也可以取消封送多次。

如果封送处理失败，则释放流指针。

`AtlMarshalPtrInProc` 只能对进程内对象的指针上使用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

##  <a name="atlunmarshalptr"></a>  AtlUnmarshalPtr

将流的封送数据转换为可由客户端使用的接口指针。

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>参数

*pStream*<br/>
[in]指向要取消封送的流的指针。

*iid*<br/>
[in]正在取消封送的接口的 GUID。

*ppUnk*<br/>
[out]指向取消封送的接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="example"></a>示例

有关示例，请参阅[AtlMarshalPtrInProc](#atlmarshalptrinproc)。

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)
