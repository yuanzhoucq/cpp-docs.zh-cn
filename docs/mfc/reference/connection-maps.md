---
title: 连接映射
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 388b3d1961f9c7cf3598db08a986c2205ac34bc5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624804"
---
# <a name="connection-maps"></a>连接映射

OLE 控件是可以公开接口向其他应用程序。 这些接口只向该控件允许从容器的访问。 如果 OLE 控件想要访问的其他 OLE 对象的外部接口，必须建立一个连接点。 此连接点允许传出外部调度映射，如事件映射或通知函数的访问控制。

Microsoft 基础类库提供了支持连接点的编程模型。 在此模型中，"连接映射"用于指定接口或 OLE 控件的连接点。 连接映射包含每个连接点的一个宏。 连接映射的详细信息，请参阅[CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md)类。

通常情况下，控件将支持仅使用两个连接点： 一个用于处理事件和一个用于属性通知。 这些功能通过实现`COleControl`基类和需要控制编写器的任何额外工作。 必须手动添加你想要在类中实现的任何其他连接点。 若要支持连接映射和点，MFC 提供了以下宏：

### <a name="connection-map-declaration-and-demarcation"></a>连接映射声明和划分

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|声明嵌入的类实现 （必须在类声明中使用） 的其他连接点。|
|[END_CONNECTION_PART](#end_connection_part)|结束连接点 （必须在类声明中使用） 的声明。|
|[CONNECTION_IID](#connection_iid)|指定控件的连接点的接口 ID。|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|声明 （必须在类声明中使用） 的类，将用于连接映射。|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|开始连接映射 （必须在类实现中使用） 的定义。|
|[END_CONNECTION_MAP](#end_connection_map)|结束连接映射 （必须在类实现中使用） 的定义。|
|[CONNECTION_PART](#connection_part)|控件的连接映射中指定的连接点。|

以下函数帮助建立和断开连接使用连接点接收器：

### <a name="initializationtermination-of-connection-points"></a>初始化/终止的连接点

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|建立源和接收器之间的连接。|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|在源和接收器之间的连接将中断。|

##  <a name="begin_connection_part"></a>  BEGIN_CONNECTION_PART

BEGIN_CONNECTION_PART 宏用于开始事件和属性通知连接点之外的其他连接点的定义。

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>参数

*类*<br/>
指定它的连接点这控件类的名称。

*localClass*<br/>
指定实现连接点的局部类的名称。

### <a name="remarks"></a>备注

在定义您的类的成员函数声明 (.h) 文件中，连接点开始 BEGIN_CONNECTION_PART 宏，则添加 CONNECTION_IID 宏和想要实现，任何其他成员函数并在完成连接点与 END_CONNECTION_PART 宏保持一致的映射。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="end_connection_part"></a>  END_CONNECTION_PART

结束连接点的声明。

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>参数

*localClass*<br/>
指定实现连接点的局部类的名称。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="connection_iid"></a>  CONNECTION_IID

使用之间的 BEGIN_CONNECTION_PART 和 END_CONNECTION_PART 宏来定义 OLE 控件支持的连接点的接口 ID。

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>参数

*iid*<br/>
接口的接口 ID 由连接点调用。

### <a name="remarks"></a>备注

*Iid*参数是用于标识连接点将在其连接的接收器调用的接口 ID 的接口。 例如：

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

指定调用 `ISinkInterface` 接口的连接点。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="declare_connection_map"></a>  DECLARE_CONNECTION_MAP

程序中的每个 `COleControl` 派生类可提供一个连接映射来指定控件支持的额外的连接点。

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>备注

如果控件支持额外的点，请在类声明的末尾使用 DECLARE_CONNECTION_MAP 宏。 然后，在.cpp 文件中定义类的成员函数，使用 BEGIN_CONNECTION_MAP 宏、 CONNECTION_PART 宏的每个控件的连接点和 END_CONNECTION_MAP 宏声明连接映射的结尾。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="begin_connection_map"></a>  BEGIN_CONNECTION_MAP

程序中的每个 `COleControl` 派生类均可提供连接映射来指定控件将支持的连接点。

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>参数

*类*<br/>
指定连接映射所属的控件类的名称。

*theBase*<br/>
指定的类的基类名称*类*。

### <a name="remarks"></a>备注

在实现 (。CPP) 文件，用于定义该成员函数为您的类，与 BEGIN_CONNECTION_MAP 宏启动连接映射然后为每个你使用的连接点添加宏条目[CONNECTION_PART](#connection_part)宏。 最后，完成与连接映射[END_CONNECTION_MAP](#end_connection_map)宏。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="end_connection_map"></a>  END_CONNECTION_MAP

结束连接映射的定义。

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="connection_part"></a>  CONNECTION_PART

将 OLE 控件的连接点映射到特定的接口 id。

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>参数

*类*<br/>
指定它的连接点这控件类的名称。

*iid*<br/>
接口的接口 ID 由连接点调用。

*localClass*<br/>
指定实现连接点的局部类的名称。

### <a name="remarks"></a>备注

例如：

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

实现了一个连接映射，与连接点，调用`IID_ISinkInterface`接口。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="afxconnectionadvise"></a>  AfxConnectionAdvise

调用此函数可指定源之间建立连接*pUnkSrc*，并通过指定接收器*pUnkSink*。

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>参数

*pUnkSrc*<br/>
指向调用接口的对象的指针。

*pUnkSink*<br/>
指向实现接口的对象的指针。

*iid*<br/>
连接的接口 ID。

*bRefCount*<br/>
TRUE 指示创建的连接应导致的引用计数*pUnkSink*增加。 FALSE 表示不应递增引用计数。

*pdwCookie*<br/>
指向一个 dword 值，其中返回的连接标识符的指针。 此值应作为传递*dwCookie*参数`AfxConnectionUnadvise`时断开连接。

### <a name="return-value"></a>返回值

如果已建立连接; 非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>要求

**标头：** afxctl.h

##  <a name="afxconnectionunadvise"></a>  AfxConnectionUnadvise

调用此函数可指定源之间的连接断开的连接*pUnkSrc*，并通过指定接收器*pUnkSink*。

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>参数

*pUnkSrc*<br/>
指向调用接口的对象的指针。

*pUnkSink*<br/>
指向实现接口的对象的指针。

*iid*<br/>
连接点接口的接口 ID。

*bRefCount*<br/>
TRUE 指示断开连接应导致的引用计数*pUnkSink*要递减。 FALSE 表示不应减少引用计数。

*dwCookie*<br/>
返回的连接标识符`AfxConnectionAdvise`。

### <a name="return-value"></a>返回值

非零，如果连接已断开连接;否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>要求

**标头：** afxctl.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
