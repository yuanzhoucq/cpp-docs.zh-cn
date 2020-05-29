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
ms.openlocfilehash: 4727f7b1799604001134ee2f4d2d2e1ce6db87fa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754784"
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry 类

ID2D1 几何体的包装器。

## <a name="syntax"></a>语法

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D 几何：CD2D几何](#cd2dgeometry)|构造 CD2D 几何对象。|
|[CD2D几何：*CD2D几何](#_dtorcd2dgeometry)|析构函数。 销毁 D2D 几何对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2D 几何：附加](#attach)|将现有资源接口附加到对象|
|[CD2D几何：：与几何体结合](#combinewithgeometry)|将此几何体与指定的几何体相结合，并将结果存储在 ID2D1 简化几何结构中。|
|[CD2D几何：：与几何体比较](#comparewithgeometry)|描述此几何体和指定几何体之间的交集。 比较使用指定的展平容差执行。|
|[CD2D 几何：计算区域](#computearea)|计算几何体的面积后，它已被指定的矩阵转换，并使用指定的容差拼平。|
|[CD2D 几何：计算长度](#computelength)|计算几何的长度，就像每个线段都展开成一条线一样。|
|[CD2D 几何：：计算点长度](#computepointatlength)|计算沿几何体的指定距离的点和切线矢量，然后由指定的矩阵转换并使用指定的容差进行拼合。|
|[CD2D 几何：:D](#destroy)|销毁 CD2D 几何对象。 （覆盖[CD2D 资源：:D）](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2D 几何：:D](#detach)|从对象分离资源接口|
|[CD2D 几何：：填充包含点](#fillcontainspoint)|指示几何图形填充的区域是否包含给定指定平整容差的指定点。|
|[CD2D 几何：获取](#get)|返回 ID2D1 几何接口|
|[CD2D 几何：获取绑定](#getbounds)||
|[CD2D 几何：：获取加束](#getwidenedbounds)|在几何体被指定的描边宽度和样式加宽并由指定的矩阵转换后获取几何体的边界。|
|[CD2D 几何：有效](#isvalid)|检查资源有效性（覆盖[CD2D 资源：：有效](../../mfc/reference/cd2dresource-class.md#isvalid)。）|
|[CD2D 几何：大纲](#outline)|计算几何体的轮廓并将结果写入 ID2D1 简化几何结构。|
|[CD2D 几何：简化](#simplify)|创建仅包含线条和（可选）立方贝塞尔曲线的几何图形的简化版本，并将结果写入 ID2D1 简化几何结构。|
|[CD2D 几何：：笔画包含点](#strokecontainspoint)|确定几何体的描边是否包含指定描边厚度、样式和变换的指定点。|
|[CD2D 几何：：底纹](#tessellate)|在使用指定的矩形转换和使用指定的容差平展几何图形后，创建一组覆盖该几何图形的顺时针方向的三角形。|
|[CD2D 几何：宽宽](#widen)|通过指定的描边加宽几何体，并将结果写入 ID2D1SimplifiedGeometrySink 后，该结果被指定的矩阵转换并使用指定的容差进行拼合。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2D几何：：操作员 ID2D1 几何*](#operator_id2d1geometry_star)|返回 ID2D1 几何接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2D 几何：：m_pGeometry](#m_pgeometry)|指向 ID2D1 几何体的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dgeometrycd2dgeometry"></a><a name="_dtorcd2dgeometry"></a>CD2D几何：*CD2D几何

析构函数。 销毁 D2D 几何对象时调用。

```
virtual ~CD2DGeometry();
```

## <a name="cd2dgeometryattach"></a><a name="attach"></a>CD2D 几何：附加

将现有资源接口附加到对象

```cpp
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL

## <a name="cd2dgeometrycd2dgeometry"></a><a name="cd2dgeometry"></a>CD2D 几何：CD2D几何

构造 CD2D 几何对象。

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dgeometrycombinewithgeometry"></a><a name="combinewithgeometry"></a>CD2D几何：：与几何体结合

将此几何体与指定的几何体相结合，并将结果存储在 ID2D1 简化几何结构中。

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*输入几何学*<br/>
要与此实例组合的几何体。

*组合模式*<br/>
要执行的组合操作的类型。

*输入几何转换*<br/>
要应用于输入几何的转换，然后再合并。

*几何结构*<br/>
合并操作的结果。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometrycomparewithgeometry"></a><a name="comparewithgeometry"></a>CD2D几何：：与几何体比较

描述此几何体和指定几何体之间的交集。 比较使用指定的展平容差执行。

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*输入几何学*<br/>
要测试的几何体。

*输入几何转换*<br/>
应用于输入几何的转换。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometrycomputearea"></a><a name="computearea"></a>CD2D 几何：计算区域

计算几何体的面积后，它已被指定的矩阵转换，并使用指定的容差拼平。

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*世界转型*<br/>
在计算其面积之前应用于此几何体的转换。

*地区*<br/>
当此方法返回时，包含指向此几何体的转换的拼合版本的区域的指针。 您必须为此参数分配存储。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometrycomputelength"></a><a name="computelength"></a>CD2D 几何：计算长度

计算几何的长度，就像每个线段都展开成一条线一样。

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*世界转型*<br/>
在计算几何体的长度之前应用于几何体的变换。

*length*<br/>
当此方法返回时，包含指向几何长度的指针。 对于闭合几何体，长度包括隐式闭合段。 您必须为此参数分配存储。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometrycomputepointatlength"></a><a name="computepointatlength"></a>CD2D 几何：：计算点长度

计算沿几何体的指定距离的点和切线矢量，然后由指定的矩阵转换并使用指定的容差进行拼合。

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
沿点的几何体和要查找的切线的距离。 如果此距离小于 0，则此方法计算几何体中的第一个点。 如果此距离大于几何的长度，则此方法计算几何体中的最后一个点。

*世界转型*<br/>
在计算指定点和切线之前应用于几何体的变换。

*点*<br/>
沿几何图形指定距离的位置。 如果几何体为空，则此点包含 NaN 作为其 x 和 y 值。

*单位唐特矢量*<br/>
当此方法返回时，包含指向沿几何体指定距离的切线矢量的指针。 如果几何体为空，则此矢量包含 NaN 作为其 x 和 y 值。 您必须为此参数分配存储。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometrydestroy"></a><a name="destroy"></a>CD2D 几何：:D

销毁 CD2D 几何对象。

```
virtual void Destroy();
```

## <a name="cd2dgeometrydetach"></a><a name="detach"></a>CD2D 几何：:D

从对象分离资源接口

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dgeometryfillcontainspoint"></a><a name="fillcontainspoint"></a>CD2D 几何：：填充包含点

指示几何图形填充的区域是否包含给定指定平整容差的指定点。

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*点*<br/>
要测试的点。

*世界转型*<br/>
在测试包含之前应用于几何体的转换。

*包含*<br/>
当此方法返回时，如果几何图形填充的区域包含点，则包含为 TRUE 的 bool 值;否则，FALSE。 您必须为此参数分配存储。

*扁平公差*<br/>
计算精确几何路径和路径交集的数字精度。 内仍考虑缺少小于容差的填充点。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometryget"></a><a name="get"></a>CD2D 几何：获取

返回 ID2D1 几何接口

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1 几何接口或 NULL 的指针。

## <a name="cd2dgeometrygetbounds"></a><a name="getbounds"></a>CD2D 几何：获取绑定

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>参数

*世界转型*<br/>
*边界*

### <a name="return-value"></a>返回值

## <a name="cd2dgeometrygetwidenedbounds"></a><a name="getwidenedbounds"></a>CD2D 几何：：获取加束

在几何体被指定的描边宽度和样式加宽并由指定的矩阵转换后获取几何体的边界。

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*笔画宽度*<br/>
通过抚摸几何轮廓来扩大几何体的数量。

*笔画样式*<br/>
宽大几何形状的描边样式。

*世界转型*<br/>
转换几何体后和几何图形描边后应用于几何图形的变换。

*边界*<br/>
当此方法返回时，包含加宽几何体的边界。 您必须为此参数分配存储。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometryisvalid"></a><a name="isvalid"></a>CD2D 几何：有效

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源有效，则为 TRUE;否则 FALSE。

## <a name="cd2dgeometrym_pgeometry"></a><a name="m_pgeometry"></a>CD2D 几何：：m_pGeometry

指向 ID2D1 几何体的指针。

```
ID2D1Geometry* m_pGeometry;
```

## <a name="cd2dgeometryoperator-id2d1geometry"></a><a name="operator_id2d1geometry_star"></a>CD2D几何：：操作员 ID2D1 几何*

返回 ID2D1 几何接口

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1 几何接口或 NULL 的指针。

## <a name="cd2dgeometryoutline"></a><a name="outline"></a>CD2D 几何：大纲

计算几何体的轮廓并将结果写入 ID2D1 简化几何结构。

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*世界转型*<br/>
要应用于几何轮廓的变换。

*几何结构*<br/>
附加几何体变换轮廓的 ID2D1 简化几何图形。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometrysimplify"></a><a name="simplify"></a>CD2D 几何：简化

创建仅包含线条和（可选）立方贝塞尔曲线的几何图形的简化版本，并将结果写入 ID2D1 简化几何结构。

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*简化选项*<br/>
指定简化几何图形是否应包含曲线的值。

*世界转型*<br/>
要应用于简化几何体的变换。

*几何结构*<br/>
附加简化几何图形的 ID2D1 简化几何图形。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometrystrokecontainspoint"></a><a name="strokecontainspoint"></a>CD2D 几何：：笔画包含点

确定几何体的描边是否包含指定描边厚度、样式和变换的指定点。

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

*点*<br/>
要进行包容测试的点。

*笔画宽度*<br/>
要应用的描边的厚度。

*笔画样式*<br/>
要应用的笔画样式。

*世界转型*<br/>
要应用于描边几何的变换。

*包含*<br/>
当此方法返回时，如果几何体的描边包含指定的点，则包含设置为 TRUE 的布尔值;否则，FALSE。 您必须为此参数分配存储。

*扁平公差*<br/>
计算精确几何路径和路径交集的数字精度。 内仍考虑以小于容差的笔画点。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometrytessellate"></a><a name="tessellate"></a>CD2D 几何：：底纹

在使用指定的矩形转换和使用指定的容差平展几何图形后，创建一组覆盖该几何图形的顺时针方向的三角形。

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*世界转型*<br/>
要应用于此几何体或 NULL 的变换。

*镶嵌*<br/>
附加镶嵌的 ID2D1Tesssink。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cd2dgeometrywiden"></a><a name="widen"></a>CD2D 几何：宽宽

通过指定的描边加宽几何体，并将结果写入 ID2D1SimplifiedGeometrySink 后，该结果被指定的矩阵转换并使用指定的容差进行拼合。

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>参数

*笔画宽度*<br/>
加宽几何体的数量。

*笔画样式*<br/>
要应用于几何体或 NULL 的描边样式。

*世界转型*<br/>
在加宽几何体后应用于几何体的变换。

*几何结构*<br/>
附加加宽几何图形的 ID2D1 简化几何图形。

*扁平公差*<br/>
几何图形的多边形近似中两点间距离的上限。 值越小，生成的结果就越准确，但执行速度会变慢。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
