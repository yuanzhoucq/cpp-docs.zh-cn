---
title: CConnectionPoint 类
ms.date: 11/04/2016
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
ms.openlocfilehash: f428ec597e0e4a56788fae2455eff80b286fda39
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183079"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint 类

定义用于与其他 OLE 对象通信的接口（称为“连接点”）的特殊类型。

## <a name="syntax"></a>语法

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|构造 `CConnectionPoint` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CConnectionPoint::GetConnections](#getconnections)|检索连接映射中的所有连接点。|
|[CConnectionPoint::GetContainer](#getcontainer)|检索拥有连接映射的控件的容器。|
|[CConnectionPoint::GetIID](#getiid)|检索连接点的接口 ID。|
|[CConnectionPoint：： GetMaxConnections](#getmaxconnections)|检索控件支持的最大连接点数。|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|检索指向位于*pos*的连接元素的指针。|
|[CConnectionPoint::GetStartPosition](#getstartposition)|通过返回可传递给调用的位置值来启动映射迭代 `GetNextConnection` 。|
|[CConnectionPoint::OnAdvise](#onadvise)|建立或断开连接时由框架调用。|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|检索指向所请求接收器接口的指针。|

## <a name="remarks"></a>备注

与用于实现和公开 OLE 控件功能的普通 OLE 接口不同，连接点实现了一个传出接口，该接口可对其他对象（如触发事件和更改通知）启动操作。

连接由两个部分组成：调用接口的对象（称为 "源"）和实现接口的对象（称为 "sink"）。 通过公开连接点，源允许接收器建立与自身的连接。 源对象通过连接点机制获取一个指针，该指针指向一组成员函数的接收器实现。 例如，若要激发由接收器实现的事件，源可以调用接收器实现的适当方法。

默认情况下， `COleControl` 派生类实现两个连接点：一个用于事件，另一个用于属性更改通知。 当属性值发生更改时，将分别使用这些连接来触发事件，并通知接收器（例如控件的容器）。 还为 OLE 控件提供了支持以实现其他连接点。 对于在控件类中实现的每个附加连接点，必须声明实现连接点的 "连接部分"。 如果实现一个或多个连接点，则还需要在控件类中声明单个 "连接映射"。

下面的示例演示了一个简单的连接映射和一个 `Sample` OLE 控件连接点，其中包含两个代码段：第一部分声明连接映射和点; 第二个部分实现此映射和点。 第一个片段插入到 control 类的声明中， **`protected`** 如下所示：

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

BEGIN_CONNECTION_PART 和 END_CONNECTION_PART 宏声明 `XSampleConnPt` `CConnectionPoint` 实现此特定连接点的嵌入类（派生自）。 如果要重写任何 `CConnectionPoint` 成员函数或添加自己的成员函数，请在这两个宏之间进行声明。 例如， `CConnectionPoint::GetIID` 当在两个宏之间放置成员函数时，CONNECTION_IID 宏会重写该成员函数。

第二个代码段插入到实现文件（。CPP）。 此代码实现连接映射，其中包括附加连接点 `SampleConnPt` ：

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

插入这些代码片段后，示例 OLE 控件将公开该接口的连接点 `ISampleSink` 。

通常，连接点支持 "多播"，这是指广播到连接到同一接口的多个接收器的能力。 下面的代码段演示如何通过循环访问连接点上的每个接收器来完成多播：

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

此示例 `SampleConnPt` 通过调用来检索连接点上的当前连接集 `CConnectionPoint::GetConnections` 。 然后，它会遍历连接，并对 `ISampleSink::SinkFunc` 每个活动的连接调用。

有关使用的详细信息 `CConnectionPoint` ，请参阅文章[连接点](../../mfc/connection-points.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint

构造 `CConnectionPoint` 对象。

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint::GetConnections

调用此函数可检索连接点的所有活动连接。

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>返回值

指向活动连接（接收器）的数组的指针。 数组中的某些指针可能为 NULL。 使用强制转换运算符，可以安全地将此数组中的每个非 NULL 指针转换为指向接收器接口的指针。

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint::GetContainer

由框架调用以检索 `IConnectionPointContainer` 连接点的。

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>返回值

如果成功，则为指向容器的指针;否则为 NULL。

### <a name="remarks"></a>备注

此函数通常由 BEGIN_CONNECTION_PART 宏实现。

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint::GetIID

由框架调用以检索连接点的接口 ID。

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>返回值

对连接点的接口 ID 的引用。

### <a name="remarks"></a>备注

重写此函数以返回此连接点的接口 ID。

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint：： GetMaxConnections

由框架调用以检索连接点支持的最大连接数。

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>返回值

控件支持的最大连接数; 如果没有限制，则为-1。

### <a name="remarks"></a>备注

默认实现返回-1，表示没有限制。

如果要限制可连接到控件的接收器数量，请重写此函数。

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint::GetNextConnection

检索指向位于*pos*的连接元素的指针。

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>参数

*位置*<br/>
指定对由 previous `GetNextConnection` 或[GetStartPosition](#getstartposition)调用返回的位置值的引用。

### <a name="return-value"></a>返回值

指向由*pos*指定的连接元素的指针，或为 NULL。

### <a name="remarks"></a>备注

此函数最适用于遍历连接映射中的所有元素。 循环访问时，跳过此函数返回的任何 Null 值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition

通过返回可传递给[GetNextConnection](#getnextconnection)调用的位置值来启动映射迭代。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>返回值

一个位置值，该值指示循环访问映射的起始位置;如果映射为空，则为 NULL。

### <a name="remarks"></a>备注

迭代顺序不可预测;因此，"映射中的第一个元素" 没有特别的意义。

### <a name="example"></a>示例

  请参阅[CConnectionPoint：： GetNextConnection](#getnextconnection)的示例。

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint::OnAdvise

当建立连接或断开连接时由框架调用。

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>参数

*bAdvise*<br/>
如果正在建立连接，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

默认实现不执行任何操作。

如果希望在接收器连接到连接点或断开连接时发出通知，请重写此函数。

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface

检索指向所请求接收器接口的指针。

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>参数

*pUnkSink*<br/>
请求的接收器接口的标识符。

*ppInterface*<br/>
指向由*pUnkSink*标识的接口指针的指针。 如果对象不支持此接口， \* 则将*ppInterface*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

## <a name="see-also"></a>另请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
