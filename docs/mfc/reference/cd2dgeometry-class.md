---
title: CD2DGeometry 类
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
ms.openlocfilehash: 4549b2e7981d5f8493ddf9f24477e75a94ddde8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405724"
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry 类

ID2D1Geometry 包装器。

## <a name="syntax"></a>语法

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|构造一个 CD2DGeometry 对象。|
|[CD2DGeometry::~CD2DGeometry](#_dtorcd2dgeometry)|析构函数。 当 D2D geometry 对象被销毁时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DGeometry::Attach](#attach)|附加现有的资源的对象的接口|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|组合此几何图形与指定几何图形，并将结果存储在 ID2D1SimplifiedGeometrySink。|
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|描述该几何图形与指定的几何图形的交集。 使用指定的容差平展执行比较。|
|[CD2DGeometry::ComputeArea](#computearea)|计算的几何区域后，通过指定矩阵转换并使用指定的容差单一化。|
|[CD2DGeometry::ComputeLength](#computelength)|计算几何的长度，就好像每个段是展开到一行。|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|计算在该几何图形的指定距离处的点和正切向量后，通过指定矩阵转换并使用指定的容差单一化。|
|[CD2DGeometry::Destroy](#destroy)|销毁 CD2DGeometry 对象。 (重写[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|
|[CD2DGeometry::Detach](#detach)|分离对象中的资源接口|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|指示是否填充几何图形的区域将包含指定的点给定指定的平展容差。|
|[CD2DGeometry::Get](#get)|返回 ID2D1Geometry 接口|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|通过指定的笔划宽度和样式扩展并通过指定矩阵转换后获取该几何图形的边界。|
|[CD2DGeometry::IsValid](#isvalid)|检查资源有效性 (重写[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2DGeometry::Outline](#outline)|计算 geometry 的轮廓，并将结果写入 ID2D1SimplifiedGeometrySink。|
|[CD2DGeometry::Simplify](#simplify)|创建仅包含行和 （可选） 三次方贝塞尔曲线并将结果写入到 ID2D1SimplifiedGeometrySink 的几何图形的简化的版本。|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|确定几何图形的笔画是否包含指定的笔画粗细、 样式和转换给定的指定的点。|
|[CD2DGeometry::Tessellate](#tessellate)|创建顺时针方向的三角形覆盖该几何图形后已转换使用指定的矩阵和平展使用指定的容差的集。|
|[CD2DGeometry::Widen](#widen)|可以通过指定的笔划扩大几何图形，并后已将结果写入到 ID2D1SimplifiedGeometrySink 由指定的矩阵来转换和使用指定的容差平展。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DGeometry::operator ID2D1Geometry *](#operator_id2d1geometry_star)|返回 ID2D1Geometry 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|指向 ID2D1Geometry 的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="_dtorcd2dgeometry"></a>  CD2DGeometry:: ~ CD2DGeometry

析构函数。 当 D2D geometry 对象被销毁时调用。

```
virtual ~CD2DGeometry();
```

##  <a name="attach"></a>  CD2DGeometry::Attach

附加现有的资源的对象的接口

```
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>参数

*pResource*<br/>
现有资源的接口。 不能为 NULL

##  <a name="cd2dgeometry"></a>  CD2DGeometry::CD2DGeometry

构造一个 CD2DGeometry 对象。

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*pParentTarget*<br/>
指向该呈现器目标的指针。

*bAutoDestroy*<br/>
指示所有者 (pParentTarget) 将销毁该对象。

##  <a name="combinewithgeometry"></a>  CD2DGeometry::CombineWithGeometry

组合此几何图形与指定几何图形，并将结果存储在 ID2D1SimplifiedGeometrySink。

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*inputGeometry*<br/>
要与此实例组合的几何图形。

*combineMode*<br/>
要执行的合并操作的类型。

*inputGeometryTransform*<br/>
要将应用于 inputGeometry 合并之前的转换。

*geometrySink*<br/>
合并操作的结果。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="comparewithgeometry"></a>  CD2DGeometry::CompareWithGeometry

描述该几何图形与指定的几何图形的交集。 使用指定的容差平展执行比较。

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*inputGeometry*<br/>
要测试的几何图形。

*inputGeometryTransform*<br/>
要将应用于 inputGeometry 的转换。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="computearea"></a>  CD2DGeometry::ComputeArea

计算的几何区域后，通过指定矩阵转换并使用指定的容差单一化。

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*worldTransform*<br/>
要计算其区域之前应用到此几何图形的转换。

*area*<br/>
此方法返回时，包含指向该几何图形的转换后的平展版本的区域。 为此参数，必须分配存储空间。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="computelength"></a>  CD2DGeometry::ComputeLength

计算几何的长度，就好像每个段是展开到一行。

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*worldTransform*<br/>
要计算其长度之前应用于几何图形的转换。

*length*<br/>
此方法返回时，包含指向该几何图形的长度的指针。 对于已关闭的几何图形，长度包括隐式关闭段。 为此参数，必须分配存储空间。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="computepointatlength"></a>  CD2DGeometry::ComputePointAtLength

计算在该几何图形的指定距离处的点和正切向量后，通过指定矩阵转换并使用指定的容差单一化。

```
BOOL ComputePointAtLength(
    FLOAT length,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DPointF& point,
    CD2DPointF& unitTangentVector,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*length*<br/>
若要查找的正切值的点的几何图形的距离。 此距离是否少于 0，此方法计算的几何中的第一个点。 如果此距离大于该几何图形的长度，则此方法计算几何图形中的最后一个点。

*worldTransform*<br/>
要计算指定的点和正切值之前应用于几何图形的转换。

*point*<br/>
在该几何图形的指定距离处位置。 如果几何图形为空，则此点包含 NaN 作为其 x 和 y 值。

*unitTangentVector*<br/>
此方法返回时，包含指向在该几何图形的指定距离处的正切向量。 如果几何图形为空，则此向量包含 NaN 作为其 x 和 y 值。 为此参数，必须分配存储空间。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="destroy"></a>  CD2DGeometry::Destroy

销毁 CD2DGeometry 对象。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DGeometry::Detach

分离对象中的资源接口

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>返回值

指向已分离的资源接口指针。

##  <a name="fillcontainspoint"></a>  CD2DGeometry::FillContainsPoint

指示是否填充几何图形的区域将包含指定的点给定指定的平展容差。

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*point*<br/>
要测试的点。

*worldTransform*<br/>
要应用于在进行包容测试之前该几何图形的转换。

*contains*<br/>
当此方法返回时包含 geometry 填充的区域包含点; 如果为 TRUE 的布尔值否则为 FALSE。 为此参数，必须分配存储空间。

*flatteningTolerance*<br/>
与数值准确性精确几何路径和路径的交点计算。 在仍被视为缺失填充小于容差的点。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="get"></a>  CD2DGeometry::Get

返回 ID2D1Geometry 接口

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>返回值

指向 ID2D1Geometry 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="getbounds"></a>  CD2DGeometry::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>参数

*worldTransform*<br/>
*bounds*

### <a name="return-value"></a>返回值

##  <a name="getwidenedbounds"></a>  CD2DGeometry::GetWidenedBounds

通过指定的笔划宽度和样式扩展并通过指定矩阵转换后获取该几何图形的边界。

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*strokeWidth*<br/>
若要扩展通过描画轮廓的几何图形的量。

*strokeStyle*<br/>
加宽几何图形的笔画的样式。

*worldTransform*<br/>
要将应用到几何图形转换几何图形后并绘制一样几何图形后转换。

*bounds*<br/>
此方法返回时，包含该加宽几何图形的边界。 为此参数，必须分配存储空间。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="isvalid"></a>  CD2DGeometry::IsValid

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源是有效，则为，TRUE否则为 FALSE。

##  <a name="m_pgeometry"></a>  CD2DGeometry::m_pGeometry

指向 ID2D1Geometry 的指针。

```
ID2D1Geometry* m_pGeometry;
```

##  <a name="operator_id2d1geometry_star"></a>  CD2DGeometry::operator ID2D1Geometry *

返回 ID2D1Geometry 接口

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>返回值

指向 ID2D1Geometry 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="outline"></a>  CD2DGeometry::Outline

计算 geometry 的轮廓，并将结果写入 ID2D1SimplifiedGeometrySink。

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*worldTransform*<br/>
要应用到几何图形大纲的转换。

*geometrySink*<br/>
向其中追加几何转换的大纲 ID2D1SimplifiedGeometrySink。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="simplify"></a>  CD2DGeometry::Simplify

创建仅包含行和 （可选） 三次方贝塞尔曲线并将结果写入到 ID2D1SimplifiedGeometrySink 的几何图形的简化的版本。

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*simplificationOption*<br/>
一个值，指定简化的几何图形是否应包含曲线。

*worldTransform*<br/>
要应用于简化几何图形的转换。

*geometrySink*<br/>
向其中追加简化的 geometry ID2D1SimplifiedGeometrySink。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="strokecontainspoint"></a>  CD2DGeometry::StrokeContainsPoint

确定几何图形的笔画是否包含指定的笔画粗细、 样式和转换给定的指定的点。

```
BOOL StrokeContainsPoint(
    CD2DPointF point,
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*point*<br/>
要进行包容测试的点。

*strokeWidth*<br/>
要应用的笔画的粗细。

*strokeStyle*<br/>
要应用的笔画的样式。

*worldTransform*<br/>
要将应用于描边的几何图形的转换。

*contains*<br/>
此方法返回时，包含几何图形的笔画包含指定的点; 如果设置为 TRUE 的布尔值否则为 FALSE。 为此参数，必须分配存储空间。

*flatteningTolerance*<br/>
与数值准确性精确几何路径和路径的交点计算。 在仍被视为缺少小于容差的笔画的点。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="tessellate"></a>  CD2DGeometry::Tessellate

创建顺时针方向的三角形覆盖该几何图形后已转换使用指定的矩阵和平展使用指定的容差的集。

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*worldTransform*<br/>
要应用于此几何形状或为 NULL 的转换。

*tessellationSink*<br/>
分割追加到 ID2D1TessellationSink。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="widen"></a>  CD2DGeometry::Widen

可以通过指定的笔划扩大几何图形，并后已将结果写入到 ID2D1SimplifiedGeometrySink 由指定的矩阵来转换和使用指定的容差平展。

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*strokeWidth*<br/>
若要扩大范围几何图形的量。

*strokeStyle*<br/>
要应用于几何形状，则为 NULL 的笔划的样式。

*worldTransform*<br/>
要扩大它后应用于该几何图形的转换。

*geometrySink*<br/>
向其中追加加宽的 geometry ID2D1SimplifiedGeometrySink。

*flatteningTolerance*<br/>
几何图形的多边形近似中两点间距离上限。 较小值生成更准确的结果，但会导致执行速度变慢。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
