---
title: CD2DGeometrySink 类
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
ms.openlocfilehash: cb51c7b11f75debece61105bf20a201b6eab80a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369238"
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink 类

ID2D1 几何基克的包装器。

## <a name="syntax"></a>语法

```
class CD2DGeometrySink;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D几何结构：：CD2D几何基克](#cd2dgeometrysink)|从 CD2DPath几何对象构造 CD2D几何基克对象。|
|[CD2D几何基克：*CD2D几何](#_dtorcd2dgeometrysink)|析构函数。 销毁 D2D 几何接收器对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2D几何结构：：添加弧](#addarc)|向路径几何体添加单个圆弧|
|[CD2D几何Sink：：AddBezier](#addbezier)|在当前点和指定的终点之间创建三次贝塞尔曲线。|
|[CD2D几何结构：：添加贝塞尔](#addbeziers)|创建立方贝塞尔曲线序列，并将它们添加到几何接收器。|
|[CD2D几何结构：：添加线](#addline)|在当前点和指定端点之间创建线段，并将其添加到几何接收器。|
|[CD2D几何结构：：添加线](#addlines)|使用指定的点创建一系列线，并将它们添加到几何接收器。|
|[CD2D几何结构：：添加四面体贝塞尔](#addquadraticbezier)|在当前点和指定的终点之间创建二次贝塞尔曲线。|
|[CD2D几何结构：：添加四面体贝塞尔](#addquadraticbeziers)|在单个调用中添加二次贝塞尔段序列作为数组。|
|[CD2D几何结构：：开始图](#beginfigure)|在指定点启动新图形。|
|[CD2D几何结构：关闭](#close)|关闭几何接收器|
|[CD2D几何结构：：结束图](#endfigure)|结束当前数字;可以选择关闭它。|
|[CD2D几何结构：获取](#get)|返回 ID2D1 几何基克接口|
|[CD2D几何结构：：有效](#isvalid)|检查几何接收器的有效性|
|[CD2D几何结构：：设置填充模式](#setfillmode)|指定用于确定哪些点位于此几何接收器描述的几何体内部以及外部点的方法。|
|[CD2D几何结构：：设置分段标志](#setsegmentflags)|指定要应用于添加到几何接收器的新线段的描边和联接选项。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2D几何基克：：操作员 ID2D1 几何基克*](#operator_id2d1geometrysink_star)|返回 ID2D1 几何基克接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2D几何：m_pSink](#m_psink)|指向 ID2D1 几何基克的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`CD2DGeometrySink`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a>CD2D几何基克：*CD2D几何

析构函数。 销毁 D2D 几何接收器对象时调用。

```
virtual ~CD2DGeometrySink();
```

## <a name="cd2dgeometrysinkaddarc"></a><a name="addarc"></a>CD2D几何结构：：添加弧

向路径几何体添加单个圆弧

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>参数

*弧*<br/>
要添加到图形中的弧段

## <a name="cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a>CD2D几何Sink：：AddBezier

在当前点和指定的终点之间创建三次贝塞尔曲线。

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>参数

*贝塞尔*<br/>
描述要添加的贝塞尔曲线的控制点和终点的结构。

## <a name="cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a>CD2D几何结构：：添加贝塞尔

创建立方贝塞尔曲线序列，并将它们添加到几何接收器。

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>参数

*贝塞尔斯*<br/>
描述要创建的贝塞尔曲线的贝塞尔段数组。 曲线从几何汇的当前点（绘制的最后一个线点的终点或 BeginFigure 指定的位置）绘制到阵列中第一个贝塞尔段的终点。 如果数组包含其他贝塞尔段，则每个后续贝塞尔段使用前一个贝塞尔段的端点作为其起始点。

## <a name="cd2dgeometrysinkaddline"></a><a name="addline"></a>CD2D几何结构：：添加线

在当前点和指定端点之间创建线段，并将其添加到几何接收器。

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>参数

*点*<br/>
要绘制的线的终点。

## <a name="cd2dgeometrysinkaddlines"></a><a name="addlines"></a>CD2D几何结构：：添加线

使用指定的点创建一系列线，并将它们添加到几何接收器。

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>参数

*点*<br/>
描述要绘制的线条的一个或多个点的数组。 线从几何汇的当前点（绘制的最后一个线点的终点或 BeginFigure 指定的位置）绘制到数组中的第一个点。 如果数组包含其他点，则从数组中的第一个点绘制一条线到数组中的第二个点，从第二个点到第三个点，等等。 要绘制的线端点的序列的数组。

## <a name="cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a>CD2D几何结构：：添加四面体贝塞尔

在当前点和指定的终点之间创建二次贝塞尔曲线。

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>参数

*贝塞尔*<br/>
描述要添加的控制点和二次贝塞尔曲线的端点的结构。

## <a name="cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a>CD2D几何结构：：添加四面体贝塞尔

在单个调用中添加二次贝塞尔段序列作为数组。

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>参数

*贝塞尔斯*<br/>
二次贝塞尔段序列的数组。

## <a name="cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a>CD2D几何结构：：开始图

在指定点启动新图形。

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>参数

*startPoint*<br/>
开始新数字的点。

*图*<br/>
新图形是空心的还是填充的。

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a>CD2D几何结构：：CD2D几何基克

从 CD2DPath几何对象构造 CD2D几何基克对象。

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>参数

*路径几何*<br/>
现有的 CD2DPath 几何对象。

## <a name="cd2dgeometrysinkclose"></a><a name="close"></a>CD2D几何结构：关闭

关闭几何接收器

```
BOOL Close();
```

### <a name="return-value"></a>返回值

如果成功，则非零;否则 FALSE。

## <a name="cd2dgeometrysinkendfigure"></a><a name="endfigure"></a>CD2D几何结构：：结束图

结束当前数字;可以选择关闭它。

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>参数

*图结束*<br/>
指示当前图形是否关闭的值。 如果图形闭合，则在当前点和 BeginFigure 指定的起始点之间绘制一条线。

## <a name="cd2dgeometrysinkget"></a><a name="get"></a>CD2D几何结构：获取

返回 ID2D1 几何基克接口

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1GeometrySink 接口或 NULL 的指针。

## <a name="cd2dgeometrysinkisvalid"></a><a name="isvalid"></a>CD2D几何结构：：有效

检查几何接收器的有效性

```
BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果几何接收器有效，则为 TRUE;如果几何接收器有效，则为 TRUE。否则 FALSE。

## <a name="cd2dgeometrysinkm_psink"></a><a name="m_psink"></a>CD2D几何：m_pSink

指向 ID2D1 几何基克的指针。

```
ID2D1GeometrySink* m_pSink;
```

## <a name="cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a>CD2D几何基克：：操作员 ID2D1 几何基克*

返回 ID2D1 几何基克接口

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1GeometrySink 接口或 NULL 的指针。

## <a name="cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a>CD2D几何结构：：设置填充模式

指定用于确定哪些点位于此几何接收器描述的几何体内部以及外部点的方法。

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>参数

*填充模式*<br/>
用于确定给定点是否为几何体的一部分的方法。

## <a name="cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a>CD2D几何结构：：设置分段标志

指定要应用于添加到几何接收器的新线段的描边和联接选项。

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>参数

*顶点标志*<br/>
要应用于添加到几何接收器的新线段的描边和联接选项。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
