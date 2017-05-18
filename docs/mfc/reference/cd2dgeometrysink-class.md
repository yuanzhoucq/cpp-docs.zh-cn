---
title: "CD2DGeometrySink 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometrySink class
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8a51d9475437ae460340d419a88bc46effa81f5f
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink 类
ID2D1GeometrySink 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DGeometrySink;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|构造 CD2DGeometrySink 对象从 CD2DPathGeometry 对象。|  
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|析构函数。 当 D2D 几何图形接收器对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DGeometrySink::AddArc](#addarc)|将一个圆弧添加到路径几何图形|  
|[CD2DGeometrySink::AddBezier](#addbezier)|创建当前点和指定的终结点之间的三次方贝塞尔曲线。|  
|[CD2DGeometrySink::AddBeziers](#addbeziers)|创建三次方贝塞尔曲线的序列，并将它们添加到几何图形接收器。|  
|[CD2DGeometrySink::AddLine](#addline)|创建当前点和指定的终结点之间的线段并将其添加到几何图形接收器。|  
|[CD2DGeometrySink::AddLines](#addlines)|创建使用指定的点线的一个序列，并将它们添加到几何图形接收器。|  
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|创建当前点和指定的终结点之间二次贝塞尔曲线。|  
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|作为单个调用中的一个数组中添加一系列的二次贝赛尔曲线段。|  
|[CD2DGeometrySink::BeginFigure](#beginfigure)|开始指定点处的一个新图形。|  
|[CD2DGeometrySink::Close](#close)|关闭几何图形接收器|  
|[CD2DGeometrySink::EndFigure](#endfigure)|结束当前图;（可选） 将其关闭。|  
|[CD2DGeometrySink::Get](#get)|返回 ID2D1GeometrySink 接口|  
|[CD2DGeometrySink::IsValid](#isvalid)|检查几何图形接收器有效性|  
|[CD2DGeometrySink::SetFillMode](#setfillmode)|指定用于确定的那些点描述此几何图形接收器的几何图形内部和外部的点的方法。|  
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|指定要应用于新段添加到几何图形接收器的笔画和联接选项。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DGeometrySink::operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|返回 ID2D1GeometrySink 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DGeometrySink::m_pSink](#m_psink)|指向 ID2D1GeometrySink 的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CD2DGeometrySink`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink:: ~ CD2DGeometrySink  
 析构函数。 当 D2D 几何图形接收器对象被销毁时调用。  
  
```  
virtual ~CD2DGeometrySink();
```  
  
##  <a name="addarc"></a>CD2DGeometrySink::AddArc  
 将一个圆弧添加到路径几何图形  
  
```  
void AddArc(const D2D1_ARC_SEGMENT& arc);
```  
  
### <a name="parameters"></a>参数  
 `arc`  
 若要添加到该图形圆弧线段  
  
##  <a name="addbezier"></a>CD2DGeometrySink::AddBezier  
 创建当前点和指定的终结点之间的三次方贝塞尔曲线。  
  
```  
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>参数  
 `bezier`  
 描述控点和终点的贝塞尔曲线，若要添加的结构。  
  
##  <a name="addbeziers"></a>CD2DGeometrySink::AddBeziers  
 创建三次方贝塞尔曲线的序列，并将它们添加到几何图形接收器。  
  
```  
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,  
    D2D1_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>参数  
 `beziers`  
 描述要创建的贝塞尔曲线的贝塞尔曲线段数组。 一条曲线是从几何图形接收器当前点 （绘制的最后一段或由 BeginFigure 指定位置的终结点） 绘制到数组中的第一个贝塞尔曲线段的结束点。 如果数组包含其他贝赛尔曲线段，每个后续的贝塞尔曲线段将使用前面的贝塞尔曲线段的结束点作为其起点。  
  
##  <a name="addline"></a>CD2DGeometrySink::AddLine  
 创建当前点和指定的终结点之间的线段并将其添加到几何图形接收器。  
  
```  
void AddLine(CD2DPointF point);
```  
  
### <a name="parameters"></a>参数  
 `point`  
 绘制直线终点。  
  
##  <a name="addlines"></a>CD2DGeometrySink::AddLines  
 创建使用指定的点线的一个序列，并将它们添加到几何图形接收器。  
  
```  
void AddLines(
    const CArray<CD2DPointF,  
    CD2DPointF>& points);
```  
  
### <a name="parameters"></a>参数  
 `points`  
 描述要绘制的线条的一个或多个点的数组。 从几何图形接收器当前点 （绘制的最后一段或由 BeginFigure 指定位置的终结点） 到数组中的第一个点绘制线条。 如果数组包含额外的点，一条线是从第一个点到第二个点绘制在数组中，从第二个点到第三个点，依次类推。 要绘制的线条终结点的一系列的数组。  
  
##  <a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier  
 创建当前点和指定的终结点之间二次贝塞尔曲线。  
  
```  
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>参数  
 `bezier`  
 描述控点和终点的二次贝塞尔曲线，若要添加的结构。  
  
##  <a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers  
 作为单个调用中的一个数组中添加一系列的二次贝赛尔曲线段。  
  
```  
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,  
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>参数  
 `beziers`  
 二次贝赛尔曲线段系列的数组。  
  
##  <a name="beginfigure"></a>CD2DGeometrySink::BeginFigure  
 开始指定点处的一个新图形。  
  
```  
void BeginFigure(
    CD2DPointF startPoint,  
    D2D1_FIGURE_BEGIN figureBegin);
```  
  
### <a name="parameters"></a>参数  
 `startPoint`  
 从此处开始新的图形点。  
  
 `figureBegin`  
 是否新图形应该是空心或填充。  
  
##  <a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink  
 构造 CD2DGeometrySink 对象从 CD2DPathGeometry 对象。  
  
```  
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```  
  
### <a name="parameters"></a>参数  
 `pathGeometry`  
 现有 CD2DPathGeometry 对象。  
  
##  <a name="close"></a>CD2DGeometrySink::Close  
 关闭几何图形接收器  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 FALSE。  
  
##  <a name="endfigure"></a>CD2DGeometrySink::EndFigure  
 结束当前图;（可选） 将其关闭。  
  
```  
void EndFigure(D2D1_FIGURE_END figureEnd);
```  
  
### <a name="parameters"></a>参数  
 `figureEnd`  
 一个值，该值指示是否关闭当前图形。 如果关闭该图中，当前的点和由 BeginFigure 指定的起始点之间绘制线条。  
  
##  <a name="get"></a>CD2DGeometrySink::Get  
 返回 ID2D1GeometrySink 接口  
  
```  
ID2D1GeometrySink* Get();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1GeometrySink 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="isvalid"></a>CD2DGeometrySink::IsValid  
 检查几何图形接收器有效性  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果几何图形接收器是否有效，则为，TRUE否则为 FALSE。  
  
##  <a name="m_psink"></a>CD2DGeometrySink::m_pSink  
 指向 ID2D1GeometrySink 的指针。  
  
```  
ID2D1GeometrySink* m_pSink;  
```  
  
##  <a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::operator ID2D1GeometrySink *  
 返回 ID2D1GeometrySink 接口  
  
```  
operator ID2D1GeometrySink*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1GeometrySink 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="setfillmode"></a>CD2DGeometrySink::SetFillMode  
 指定用于确定的那些点描述此几何图形接收器的几何图形内部和外部的点的方法。  
  
```  
void SetFillMode(D2D1_FILL_MODE fillMode);
```  
  
### <a name="parameters"></a>参数  
 `fillMode`  
 用来确定给定的点是否为几何图形的标识符的一部分的方法。  
  
##  <a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags  
 指定要应用于新段添加到几何图形接收器的笔画和联接选项。  
  
```  
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```  
  
### <a name="parameters"></a>参数  
 `vertexFlags`  
 要应用于新段添加到几何图形接收器的笔画和联接选项。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

