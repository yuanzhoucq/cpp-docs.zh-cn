---
title: 连接映射
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 947cd09023ef4028a32db8e2e4e8b33f7e04e0dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374807"
---
# <a name="connection-maps"></a>连接映射

OLE 控件能够将接口公开给其他应用程序。 这些接口只允许从容器访问该控件。 如果 OLE 控件想要访问其他 OLE 对象的外部接口，则必须建立连接点。 此连接点允许控件向外访问外部调度映射，如事件映射或通知函数。

Microsoft 基础类库提供了支持连接点的编程模型。 在此模型中，"连接映射"用于为 OLE 控件指定接口或连接点。 连接映射包含每个连接点的一个宏。 有关连接映射的详细信息，请参阅[CConnectPoint](../../mfc/reference/cconnectionpoint-class.md)类。

通常，控件仅支持两个连接点：一个用于事件，一个用于属性通知。 这些由基类实现`COleControl`，不需要控件编写器的额外工作。 必须在类中实现任何其他连接点都必须手动添加。 为了支持连接映射和点，MFC 提供以下宏：

### <a name="connection-map-declaration-and-demarcation"></a>连接映射声明和标界

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|声明实现附加连接点的嵌入类（必须在类声明中使用）。|
|[END_CONNECTION_PART](#end_connection_part)|结束连接点的声明（必须在类声明中使用）。|
|[CONNECTION_IID](#connection_iid)|指定控件连接点的接口 ID。|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|声明连接映射将在类中使用（必须在类声明中使用）。|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|开始定义连接映射（必须在类实现中使用）。|
|[END_CONNECTION_MAP](#end_connection_map)|结束连接映射的定义（必须在类实现中使用）。|
|[CONNECTION_PART](#connection_part)|在控件的连接映射中指定连接点。|

以下功能可帮助接收器使用连接点建立和断开连接：

### <a name="initializationtermination-of-connection-points"></a>连接点的初始化/终止

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|在源和接收器之间建立连接。|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|断开源和接收器之间的连接。|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a>BEGIN_CONNECTION_PART

使用BEGIN_CONNECTION_PART宏开始定义事件和属性通知连接点以外的其他连接点。

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>参数

*类*<br/>
指定连接点为该连接点的控件类的名称。

*localClass*<br/>
指定实现连接点的局部类的名称。

### <a name="remarks"></a>备注

在定义类成员函数的声明 （.h） 文件中，使用BEGIN_CONNECTION_PART宏启动连接点，然后添加 CONNECTION_IID宏和要实现的任何其他成员函数，然后使用END_CONNECTION_PART宏完成连接点映射。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="end_connection_part"></a><a name="end_connection_part"></a>END_CONNECTION_PART

结束连接点的声明。

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>参数

*localClass*<br/>
指定实现连接点的局部类的名称。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="connection_iid"></a><a name="connection_iid"></a>CONNECTION_IID

在BEGIN_CONNECTION_PART和END_CONNECTION_PART宏之间使用为 OLE 控件支持的连接点定义接口 ID。

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>参数

*Iid*<br/>
接口的接口 ID 由连接点调用。

### <a name="remarks"></a>备注

*iid*参数是一个接口 ID，用于标识连接点将在其连接的接收器上调用的接口。 例如：

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

指定调用 `ISinkInterface` 接口的连接点。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP

程序中的每个 `COleControl` 派生类可提供一个连接映射来指定控件支持的额外的连接点。

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>备注

如果控件支持其他点，请使用类声明末尾的DECLARE_CONNECTION_MAP宏。 然后，在定义类成员函数的 .cpp 文件中，使用BEGIN_CONNECTION_MAP宏，CONNECTION_PART每个控件的连接点CONNECTION_PART宏，END_CONNECTION_MAP宏来声明连接映射的结束。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP

程序中的每个 `COleControl` 派生类均可提供连接映射来指定控件将支持的连接点。

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>参数

*类*<br/>
指定连接映射所属的控件类的名称。

*theBase*<br/>
指定*类*的基类的名称。

### <a name="remarks"></a>备注

在实现中 （.CPP） 文件，用于定义类的成员函数，使用BEGIN_CONNECTION_MAP宏启动连接映射，然后使用[CONNECTION_PART](#connection_part)宏为每个连接点添加宏条目。 最后，使用[END_CONNECTION_MAP](#end_connection_map)宏完成连接映射。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="end_connection_map"></a><a name="end_connection_map"></a>END_CONNECTION_MAP

结束连接映射的定义。

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="connection_part"></a><a name="connection_part"></a>CONNECTION_PART

将 OLE 控件的连接点映射到特定的接口 ID。

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>参数

*类*<br/>
指定连接点为该连接点的控件类的名称。

*Iid*<br/>
接口的接口 ID 由连接点调用。

*localClass*<br/>
指定实现连接点的局部类的名称。

### <a name="remarks"></a>备注

例如：

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

实现连接映射，带连接点，调用`IID_ISinkInterface`接口 。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a>AfxConnection 建议

调用此函数以建立由*pUnkSrc*指定的源和*pUnkSink*指定的接收器之间的连接。

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>参数

*普恩克斯克*<br/>
指向调用接口的对象的指针。

*pUnkSink*<br/>
指向实现接口的对象的指针。

*Iid*<br/>
连接的接口 ID。

*bRefCount*<br/>
TRUE 表示创建连接应导致*pUnkSink*的引用计数增加。 FALSE 表示不应增加引用计数。

*pdwCookie*<br/>
指向返回连接标识符的 DWORD 的指针。 断开连接时，此值应作为*dwCookie* `AfxConnectionUnadvise`参数传递给。

### <a name="return-value"></a>返回值

建立连接时非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>要求

**标题：** afxctl.h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a>AfxConnectionUn建议

调用此函数以断开由*pUnkSrc*指定的源和*pUnkSink*指定的接收器之间的连接。

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>参数

*普恩克斯克*<br/>
指向调用接口的对象的指针。

*pUnkSink*<br/>
指向实现接口的对象的指针。

*Iid*<br/>
连接点接口的接口 ID。

*bRefCount*<br/>
TRUE 表示断开连接应会导致*pUnkSink*的引用计数被递减。 FALSE 表示不应减少引用计数。

*dwCookie*<br/>
返回`AfxConnectionAdvise`的连接标识符。

### <a name="return-value"></a>返回值

如果连接断开，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>要求

**标题：** afxctl.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
