---
title: "CD2DGeometrySink 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b070dce706ab1fa63c71ac84b68f36c596b812d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink 类
ID2D1GeometrySink 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DGeometrySink;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|构造 CD2DGeometrySink 对象从 CD2DPathGeometry 对象。|  
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|析构函数。 当 D2D 几何图形接收器对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DGeometrySink::AddArc](#addarc)|将一段弧添加到路径几何图形|  
|[CD2DGeometrySink::AddBezier](#addbezier)|在当前点和指定的终点之间创建三次贝塞尔曲线。|  
|[CD2DGeometrySink::AddBeziers](#addbeziers)|创建三次方贝塞尔曲线的序列，并将它们添加到几何图形接收器。|  
|[CD2DGeometrySink::AddLine](#addline)|创建当前点和指定的终结点之间的线段并将其添加到几何图形接收器。|  
|[CD2DGeometrySink::AddLines](#addlines)|创建使用指定的点的行的一个序列，并将它们添加到几何图形接收器。|  
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|在当前点和指定的终点之间创建二次贝塞尔曲线。|  
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|将二次贝塞尔线段序列添加为一次调用的数组。|  
|[CD2DGeometrySink::BeginFigure](#beginfigure)|开始指定点处的一个新图形。|  
|[CD2DGeometrySink::Close](#close)|关闭几何图形接收器|  
|[CD2DGeometrySink::EndFigure](#endfigure)|结束当前图;（可选） 将其关闭。|  
|[CD2DGeometrySink::Get](#get)|返回 ID2D1GeometrySink 接口|  
|[CD2DGeometrySink::IsValid](#isvalid)|检查几何图形接收器有效性|  
|[CD2DGeometrySink::SetFillMode](#setfillmode)|指定用来确定哪个都是在此几何图形接收器所描述的几何图形事项，因此这些点之外的方法。|  
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|指定要应用于新段添加到几何图形接收器的笔画和联接选项。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DGeometrySink::operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|返回 ID2D1GeometrySink 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DGeometrySink::m_pSink](#m_psink)|指向 ID2D1GeometrySink 的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CD2DGeometrySink`  
  
## <a name="requirements"></a>要求  
 **标头：** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink:: ~ CD2DGeometrySink  
 析构函数。 当 D2D 几何图形接收器对象被销毁时调用。  
  
```  
virtual ~CD2DGeometrySink();
```  
  
##  <a name="addarc"></a>CD2DGeometrySink::AddArc  
 将一段弧添加到路径几何图形  
  
```  
void AddArc(const D2D1_ARC_SEGMENT& arc);
```  
  
### <a name="parameters"></a>参数  
 `arc`  
 圆弧线段将添加到图  
  
##  <a name="addbezier"></a>CD2DGeometrySink::AddBezier  
 在当前点和指定的终点之间创建三次贝塞尔曲线。  
  
```  
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>参数  
 `bezier`  
 描述的控点和的贝塞尔曲线，若要添加的终结点的结构。  
  
##  <a name="addbeziers"></a>CD2DGeometrySink::AddBeziers  
 创建三次方贝塞尔曲线的序列，并将它们添加到几何图形接收器。  
  
```  
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,  
    D2D1_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>参数  
 `beziers`  
 描述要创建的贝塞尔曲线的贝塞尔曲线段数组。 从几何图形接收器当前点 （绘制的最后一段或由 BeginFigure 指定的位置的终结点） 绘制曲线将指向数组中的第一个贝塞尔段的结束点。 如果数组包含其他贝塞尔段，每个后续的贝塞尔段将使用前面的贝塞尔段的结束点作为其起点。  
  
##  <a name="addline"></a>CD2DGeometrySink::AddLine  
 创建当前点和指定的终结点之间的线段并将其添加到几何图形接收器。  
  
```  
void AddLine(CD2DPointF point);
```  
  
### <a name="parameters"></a>参数  
 `point`  
 要绘制的行的终结点。  
  
##  <a name="addlines"></a>CD2DGeometrySink::AddLines  
 创建使用指定的点的行的一个序列，并将它们添加到几何图形接收器。  
  
```  
void AddLines(
    const CArray<CD2DPointF,  
    CD2DPointF>& points);
```  
  
### <a name="parameters"></a>参数  
 `points`  
 描述要绘制的线条的一个或多个点的数组。 从几何图形接收器当前点 （绘制的最后一段或由 BeginFigure 指定的位置的终结点） 到数组中的第一个点绘制线条。 如果数组包含额外的点，线是从第一个点绘制到数组中从第三个点，依次类推的第二个点的第二个点。 要绘制的线条终结点的序列的数组。  
  
##  <a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier  
 在当前点和指定的终点之间创建二次贝塞尔曲线。  
  
```  
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>参数  
 `bezier`  
 描述控点和二次的贝塞尔曲线，若要添加终结点的结构。  
  
##  <a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers  
 将二次贝塞尔线段序列添加为一次调用的数组。  
  
```  
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,  
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>参数  
 `beziers`  
 二次贝塞尔线段序列的数组。  
  
##  <a name="beginfigure"></a>CD2DGeometrySink::BeginFigure  
 开始指定点处的一个新图形。  
  
```  
void BeginFigure(
    CD2DPointF startPoint,  
    D2D1_FIGURE_BEGIN figureBegin);
```  
  
### <a name="parameters"></a>参数  
 `startPoint`  
 在此处开始新图的点。  
  
 `figureBegin`  
 是否新图应空心或填充。  
  
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
 如果成功，则非零否则为 FALSE。  
  
##  <a name="endfigure"></a>CD2DGeometrySink::EndFigure  
 结束当前图;（可选） 将其关闭。  
  
```  
void EndFigure(D2D1_FIGURE_END figureEnd);
```  
  
### <a name="parameters"></a>参数  
 `figureEnd`  
 一个值，该值指示是否关闭当前的图。 如果已关闭图，当前点和由 BeginFigure 指定的起始点之间绘制线条。  
  
##  <a name="get"></a>CD2DGeometrySink::Get  
 返回 ID2D1GeometrySink 接口  
  
```  
ID2D1GeometrySink* Get();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1GeometrySink 接口或如果尚未初始化对象的 NULL 指针。  
  
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
 指向 ID2D1GeometrySink 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="setfillmode"></a>CD2DGeometrySink::SetFillMode  
 指定用来确定哪个都是在此几何图形接收器所描述的几何图形事项，因此这些点之外的方法。  
  
```  
void SetFillMode(D2D1_FILL_MODE fillMode);
```  
  
### <a name="parameters"></a>参数  
 `fillMode`  
 用于确定给定的点是否为的几何图形的一部分的方法。  
  
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
