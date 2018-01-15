---
title: "CD2DGeometry 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3b9d8373bdf1cba1c57936dfb4d98c5401c80476
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|构造 CD2DGeometry 对象。|  
|[CD2DGeometry:: ~ CD2DGeometry](#_dtorcd2dgeometry)|析构函数。 当 D2D 几何对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DGeometry::Attach](#attach)|附加现有的资源的对象的接口|  
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|组合此几何都与指定的几何图形，并将结果存储在 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|描述该几何图形与指定的几何图形的交集。 使用指定的拼合容差进行比较。|  
|[CD2DGeometry::ComputeArea](#computearea)|计算的几何图形区域后，将通过指定矩阵转换和平展使用指定的容差。|  
|[CD2DGeometry::ComputeLength](#computelength)|计算该几何图形的长度，就如同每个段展开到行。|  
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|计算在指定的距离该几何图形处的点和切线向量后，将通过指定矩阵转换和平展使用指定的容差。|  
|[CD2DGeometry::Destroy](#destroy)|销毁 CD2DGeometry 对象。 (重写[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DGeometry::Detach](#detach)|分离资源接口从该对象|  
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|指示是否由该几何图形填充的区域将包含给定指定拼合容差的指定的点。|  
|[CD2DGeometry::Get](#get)|返回 ID2D1Geometry 接口|  
|[CD2DGeometry::GetBounds](#getbounds)||  
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|通过指定描边宽度和样式将加宽并通过指定矩阵转换之后，请获取该几何图形的边界。|  
|[CD2DGeometry::IsValid](#isvalid)|检查资源有效性 (重写[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
|[CD2DGeometry::Outline](#outline)|计算的轮廓的几何图形，并将结果写入 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::Simplify](#simplify)|创建的几何图形，只包含行和 （可选） 三次方贝塞尔曲线并将结果写入到 ID2D1SimplifiedGeometrySink 的简化的版本。|  
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|确定几何图形的笔画是否包含给定指定的笔画粗细、 样式和转换的指定的点。|  
|[CD2DGeometry::Tessellate](#tessellate)|创建一组涵盖几何图形，已转换使用指定的矩阵后，平展使用指定的容差的顺时针旋转缠绕三角形。|  
|[CD2DGeometry::Widen](#widen)|指定笔画加宽几何图形，并将结果写入到 ID2D1SimplifiedGeometrySink 后，将通过指定矩阵转换和平展使用指定的容差。|  
  
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
  
## <a name="requirements"></a>惠?  
 **标头：** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometry"></a>CD2DGeometry:: ~ CD2DGeometry  
 析构函数。 当 D2D 几何对象被销毁时调用。  
  
```  
virtual ~CD2DGeometry();
```  
  
##  <a name="attach"></a>CD2DGeometry::Attach  
 附加现有的资源的对象的接口  
  
```  
void Attach(ID2D1Geometry* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 现有资源接口。 不能为 NULL  
  
##  <a name="cd2dgeometry"></a>CD2DGeometry::CD2DGeometry  
 构造 CD2DGeometry 对象。  
  
```  
CD2DGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pParentTarget`  
 指向该呈现器目标的指针。  
  
 `bAutoDestroy`  
 指示该对象将销毁所有者 (pParentTarget)。  
  
##  <a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry  
 组合此几何都与指定的几何图形，并将结果存储在 ID2D1SimplifiedGeometrySink。  
  
```  
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,  
    D2D1_COMBINE_MODE combineMode,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `inputGeometry`  
 要与此实例合并的几何图形。  
  
 `combineMode`  
 要执行的合并操作的类型。  
  
 `inputGeometryTransform`  
 要应用于 inputGeometry 合并之前的转换。  
  
 `geometrySink`  
 合并操作的结果。  
  
 `flatteningTolerance`  
 中的多边形几何图形的近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="comparewithgeometry"></a>CD2DGeometry::CompareWithGeometry  
 描述该几何图形与指定的几何图形的交集。 使用指定的拼合容差进行比较。  
  
```  
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `inputGeometry`  
 要测试的几何图形。  
  
 `inputGeometryTransform`  
 要应用于 inputGeometry 的转换。  
  
 `flatteningTolerance`  
 中的多边形几何图形的近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="computearea"></a>CD2DGeometry::ComputeArea  
 计算的几何图形区域后，将通过指定矩阵转换和平展使用指定的容差。  
  
```  
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& area,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `worldTransform`  
 要计算其区域之前应用于该几何图形的转换。  
  
 `area`  
 此方法返回时，包含该几何图形的转换后的平展版本的区域的指针。 必须为此参数来分配存储空间。  
  
 `flatteningTolerance`  
 中的几何图形的多边形近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="computelength"></a>CD2DGeometry::ComputeLength  
 计算该几何图形的长度，就如同每个段展开到行。  
  
```  
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& length,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `worldTransform`  
 要计算其长度之前应用于几何图形的转换。  
  
 `length`  
 此方法返回时，包含该几何图形的长度的指针。 对于已关闭的几何图形，长度包括隐式右段。 必须为此参数来分配存储空间。  
  
 `flatteningTolerance`  
 中的几何图形的多边形近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength  
 计算在指定的距离该几何图形处的点和切线向量后，将通过指定矩阵转换和平展使用指定的容差。  
  
```  
BOOL ComputePointAtLength(
    FLOAT length,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DPointF& point,  
    CD2DPointF& unitTangentVector,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `length`  
 点和查找的正切值的几何图形的距离。 如果此距离少于 0，则此方法计算几何图形中的第一个点。 如果此距离大于该几何图形的长度，则此方法计算几何图形中的最后一个点。  
  
 `worldTransform`  
 要计算指定的点和正切值之前应用于几何图形的转换。  
  
 `point`  
 在指定的距离该几何图形的位置。 几何图形是否为空，则此点包含 NaN 作为其 x 和 y 值。  
  
 `unitTangentVector`  
 此方法返回时，包含在指定的距离该几何图形处的切线向量的指针。 如果该几何图形为空，则此向量包含 NaN 作为其 x 和 y 值。 必须为此参数来分配存储空间。  
  
 `flatteningTolerance`  
 中的几何图形的多边形近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="destroy"></a>CD2DGeometry::Destroy  
 销毁 CD2DGeometry 对象。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DGeometry::Detach  
 分离资源接口从该对象  
  
```  
ID2D1Geometry* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向分离的资源接口指针。  
  
##  <a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint  
 指示是否由该几何图形填充的区域将包含给定指定拼合容差的指定的点。  
  
```  
BOOL FillContainsPoint(
    CD2DPointF point,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `point`  
 要测试的点。  
  
 `worldTransform`  
 要应用于之前包含测试几何图形的转换。  
  
 `contains`  
 当此方法返回时，包含由该几何图形填充该区域包含点; 如果为 TRUE 的 bool 值否则为 FALSE。 必须为此参数来分配存储空间。  
  
 `flatteningTolerance`  
 数值的准确性，但其精确几何路径以及路径交集计算。 内仍被视为小于容差缺失填充的点。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="get"></a>CD2DGeometry::Get  
 返回 ID2D1Geometry 接口  
  
```  
ID2D1Geometry* Get();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1Geometry 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="getbounds"></a>CD2DGeometry::GetBounds  
  
```   
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,  
CD2DRectF& bounds) const; 
```  
  
### <a name="parameters"></a>参数  
 `worldTransform`  
 `bounds`  
  
### <a name="return-value"></a>返回值  
  
##  <a name="getwidenedbounds"></a>CD2DGeometry::GetWidenedBounds  
 通过指定描边宽度和样式将加宽并通过指定矩阵转换之后，请获取该几何图形的边界。  
  
```  
BOOL GetWidenedBounds(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DRectF& bounds,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `strokeWidth`  
 扩展方法是通过描边轮廓的几何图形的数量。  
  
 `strokeStyle`  
 扩大几何图形的笔划的样式。  
  
 `worldTransform`  
 要应用于该几何图形，并在描边几何图形之后几何图形转换后的转换。  
  
 `bounds`  
 此方法返回时，包含该扩大几何图形的边界。 必须为此参数来分配存储空间。  
  
 `flatteningTolerance`  
 中的多边形几何图形的近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="isvalid"></a>CD2DGeometry::IsValid  
 检查资源有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果资源是有效，则为，TRUE否则为 FALSE。  
  
##  <a name="m_pgeometry"></a>CD2DGeometry::m_pGeometry  
 指向 ID2D1Geometry 的指针。  
  
```  
ID2D1Geometry* m_pGeometry;  
```  
  
##  <a name="operator_id2d1geometry_star"></a>CD2DGeometry::operator ID2D1Geometry *  
 返回 ID2D1Geometry 接口  
  
```  
operator ID2D1Geometry*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1Geometry 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="outline"></a>CD2DGeometry::Outline  
 计算的轮廓的几何图形，并将结果写入 ID2D1SimplifiedGeometrySink。  
  
```  
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `worldTransform`  
 要应用于该几何图形边框的转换。  
  
 `geometrySink`  
 向其中追加几何转换后的大纲 ID2D1SimplifiedGeometrySink。  
  
 `flatteningTolerance`  
 中的几何图形的多边形近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="simplify"></a>CD2DGeometry::Simplify  
 创建的几何图形，只包含行和 （可选） 三次方贝塞尔曲线并将结果写入到 ID2D1SimplifiedGeometrySink 的简化的版本。  
  
```  
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `simplificationOption`  
 一个值，指定的简化的几何图形是否应包含曲线。  
  
 `worldTransform`  
 要应用于简化几何图形的转换。  
  
 `geometrySink`  
 向其中追加的简化的几何图形 ID2D1SimplifiedGeometrySink。  
  
 `flatteningTolerance`  
 中的几何图形的多边形近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint  
 确定几何图形的笔画是否包含给定指定的笔画粗细、 样式和转换的指定的点。  
  
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
 `point`  
 要测试包含的点。  
  
 `strokeWidth`  
 要应用的笔划的粗细。  
  
 `strokeStyle`  
 要应用的笔划的样式。  
  
 `worldTransform`  
 要应用于绘制几何图形的转换。  
  
 `contains`  
 当此方法返回时，包含几何图形的笔画包含指定的点; 如果设置为 TRUE 的布尔值否则为 FALSE。 必须为此参数来分配存储空间。  
  
 `flatteningTolerance`  
 数值的准确性，但其精确几何路径以及路径交集计算。 内仍被视为小于容差缺失笔画的点。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="tessellate"></a>CD2DGeometry::Tessellate  
 创建一组涵盖几何图形，已转换使用指定的矩阵后，平展使用指定的容差的顺时针旋转缠绕三角形。  
  
```  
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1TessellationSink* tessellationSink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `worldTransform`  
 要应用于此的几何图形或为 NULL 的转换。  
  
 `tessellationSink`  
 分割追加到 ID2D1TessellationSink。  
  
 `flatteningTolerance`  
 中的几何图形的多边形近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="widen"></a>CD2DGeometry::Widen  
 指定笔画加宽几何图形，并将结果写入到 ID2D1SimplifiedGeometrySink 后，将通过指定矩阵转换和平展使用指定的容差。  
  
```  
BOOL Widen(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>参数  
 `strokeWidth`  
 若要扩大范围几何图形依据的数量。  
  
 `strokeStyle`  
 要应用于的几何图形或为 NULL 的笔划的样式。  
  
 `worldTransform`  
 要应用于该几何图形扩大它后的转换。  
  
 `geometrySink`  
 向其中追加扩大的几何图形 ID2D1SimplifiedGeometrySink。  
  
 `flatteningTolerance`  
 中的几何图形的多边形近似的点之间距离上限。 较小值生成更准确的结果，但会使执行速度变慢。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
