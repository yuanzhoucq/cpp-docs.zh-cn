---
title: 连接点类
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
ms.openlocfilehash: ce72c156ab31b742a42d2960923fc56afff656c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369431"
---
# <a name="cconnectionpoint-class"></a>连接点类

定义用于与其他 OLE 对象通信的接口（称为“连接点”）的特殊类型。

## <a name="syntax"></a>语法

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[连接点：C连接点](#cconnectionpoint)|构造 `CConnectionPoint` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C连接点：获取连接](#getconnections)|检索连接映射中的所有连接点。|
|[C连接点：获取容器](#getcontainer)|检索拥有连接映射的控件的容器。|
|[连接点：获取 IID](#getiid)|检索连接点的接口 ID。|
|[连接点：：获取最大连接](#getmaxconnections)|检索控件支持的最大连接点数。|
|[C连接点：：获取下一个连接](#getnextconnection)|检索指向*pos*处的连接元素的指针。|
|[连接点：：获取起始位置](#getstartposition)|通过返回可以传递给`GetNextConnection`调用的定位值来启动映射迭代。|
|[连接点：：上建议](#onadvise)|建立或断开连接时由框架调用。|
|[连接点：：查询Sink接口](#querysinkinterface)|检索指向请求的接收器接口的指针。|

## <a name="remarks"></a>备注

与用于实现和公开 OLE 控件功能的正常 OLE 接口不同，连接点实现了一个传出接口，该接口能够对其他对象（如触发事件和更改通知）启动操作。

连接由两部分组成：调用接口的对象称为"源"，实现接口的对象称为"接收器"。 通过公开连接点，源允许接收器建立与自身的连接。 通过连接点机制，源对象获取指向接收器实现一组成员函数的指针。 例如，要触发由接收器实现的事件，源可以调用接收器实现的适当方法。

默认情况下，`COleControl`派生类实现两个连接点：一个用于事件，一个用于属性更改通知。 这些连接分别用于事件触发和属性值更改时通知接收器（例如控件的容器）。 还支持 OLE 控件实现其他连接点。 对于在控制类中实现的每个附加连接点，必须声明实现连接点的"连接部件"。 如果实现一个或多个连接点，还需要在控制类中声明单个"连接映射"。

下面的示例演示了`Sample`OLE 控件的简单连接映射和一个连接点，由两个代码片段组成：第一部分声明连接映射和点;第二部分声明连接映射和点;第二部分声明连接映射和点。第二个实现此映射和点。 第一个片段插入到控制类的声明中，在**受保护的**部分下：

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

BEGIN_CONNECTION_PART宏和END_CONNECTION_PART宏声明实现此特定连接点的`XSampleConnPt`嵌入式类（`CConnectionPoint`派生自 ）。 如果要重写任何`CConnectionPoint`成员函数，或添加您自己的成员函数，请在这两个宏之间声明它们。 例如，CONNECTION_IID宏在这两个宏之间`CConnectionPoint::GetIID`放置时将覆盖成员函数。

第二个代码片段插入到实现文件 （。控制类的 CPP）。 此代码实现连接映射，其中包括其他连接点： `SampleConnPt`

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

插入这些代码片段后，示例 OLE 控件将公开接口的连接`ISampleSink`点。

通常，连接点支持"多播"，即广播到连接到同一接口的多个接收器的能力。 以下代码片段演示如何通过连接点上的每个接收器迭代来实现多播：

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

本示例检索`SampleConnPt`连接点上的当前连接集，并调用`CConnectionPoint::GetConnections`。 然后，它通过连接进行遍接，并调用`ISampleSink::SinkFunc`每个活动连接。

有关 使用`CConnectionPoint`的详细信息，请参阅文章[连接点](../../mfc/connection-points.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>连接点：C连接点

构造 `CConnectionPoint` 对象。

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>C连接点：获取连接

调用此函数以检索连接点的所有活动连接。

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>返回值

指向活动连接（接收器）数组的指针。 数组中的某些指针可能为 NULL。 此数组中的每个非 NULL 指针都可以使用强制转换运算符安全地转换为到接收器接口的指针。

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>C连接点：获取容器

由框架调用以检索`IConnectionPointContainer`连接点。

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>返回值

如果成功，则指向容器的指针;否则 NULL。

### <a name="remarks"></a>备注

此函数通常由BEGIN_CONNECTION_PART宏实现。

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>连接点：获取 IID

由框架调用以检索连接点的接口 ID。

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>返回值

对连接点接口 ID 的引用。

### <a name="remarks"></a>备注

重写此函数以返回此连接点的接口 ID。

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>连接点：：获取最大连接

由框架调用以检索连接点支持的最大连接数。

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>返回值

控件支持的最大连接数，如果没有限制，则为 -1。

### <a name="remarks"></a>备注

默认实现返回 -1，表示没有限制。

如果要限制可连接到控件的接收器数，请覆盖此函数。

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>C连接点：：获取下一个连接

检索指向*pos*处的连接元素的指针。

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>参数

*Pos*<br/>
指定对上一次`GetNextConnection`或[GetStart定位](#getstartposition)调用返回的定位值的引用。

### <a name="return-value"></a>返回值

指向*pos*指定的连接元素的指针 ， 或 NULL。

### <a name="remarks"></a>备注

此功能对于迭代连接映射中的所有元素最有用。 迭代时，跳过从此功能返回的任何 NUL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>连接点：：获取起始位置

通过返回可以传递到[GetNextConnect](#getnextconnection)调用的定位值来启动地图迭代。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>返回值

指示迭代地图的起始位置的定位值;如果地图为空，则为 NULL。

### <a name="remarks"></a>备注

迭代序列是不可预测的;因此，"地图中的第一个元素"没有特殊的意义。

### <a name="example"></a>示例

  请参阅[CConnectionPoint 的示例：获取Next连接](#getnextconnection)。

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>连接点：：上建议

当建立或断开连接时由框架调用。

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>参数

*b 建议*<br/>
TRUE，如果正在建立连接;否则 FALSE。

### <a name="remarks"></a>备注

默认实现不执行任何操作。

如果要在接收器连接到连接点或断开连接点时发出通知，请覆盖此函数。

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>连接点：：查询Sink接口

检索指向请求的接收器接口的指针。

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>参数

*pUnkSink*<br/>
要请求的接收器接口的标识符。

*ppInterface*<br/>
指向*pUnkSink*标识的接口指针的指针。 如果对象不支持此接口，\**则 ppInterface*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="see-also"></a>另请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
