---
title: CRgn 类
ms.date: 11/04/2016
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
ms.openlocfilehash: 66721f34a8ac2b6dac6addcfa04a88b46a37ee60
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916832"
---
# <a name="crgn-class"></a>CRgn 类

封装一个 Windows 图形设备接口 (GDI) 区域。

## <a name="syntax"></a>语法

```
class CRgn : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CRgn:: CRgn](#crgn)|构造 `CRgn` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|设置对象, 使其等效于两个指定`CRgn`的对象的并集。 `CRgn`|
|[CRgn::CopyRgn](#copyrgn)|设置对象, 使其成为指定`CRgn`对象的副本。 `CRgn`|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|使用椭圆形区域初始化对象。`CRgn`|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|使用[矩形](/windows/desktop/api/windef/ns-windef-tagrect)结构定义的椭圆形区域初始化对象。`CRgn`|
|[CRgn::CreateFromData](#createfromdata)|从给定的区域创建区域和转换数据。|
|[CRgn::CreateFromPath](#createfrompath)|从选择到给定设备上下文的路径创建区域。|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|使用多边形区域初始化对象。`CRgn` 系统会根据需要, 通过从最后一个顶点到第一个顶点绘制线条来自动关闭多边形。|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|使用由一系列闭合多边形组成的区域初始化对象。`CRgn` 多边形可能是不相交的, 也可能是重叠的。|
|[CRgn::CreateRectRgn](#createrectrgn)|使用矩形区域初始化对象。`CRgn`|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|使用由[RECT](/windows/desktop/api/windef/ns-windef-tagrect)结构定义的矩形区域初始化对象。`CRgn`|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|使用带有圆角的矩形区域初始化对象。`CRgn`|
|[CRgn::EqualRgn](#equalrgn)|检查两`CRgn`个对象以确定它们是否等效。|
|[CRgn::FromHandle](#fromhandle)|当给定 Windows 区域的`CRgn`句柄时, 返回指向对象的指针。|
|[CRgn::GetRegionData](#getregiondata)|用描述给定区域的数据填充指定的缓冲区。|
|[CRgn::GetRgnBox](#getrgnbox)|检索`CRgn`对象的边框的坐标。|
|[CRgn::OffsetRgn](#offsetrgn)|按指定的偏移量移动对象。`CRgn`|
|[CRgn::PtInRegion](#ptinregion)|确定指定点是否在区域中。|
|[CRgn::RectInRegion](#rectinregion)|确定指定矩形的任何部分是否在区域边界内。|
|[CRgn::SetRectRgn](#setrectrgn)|`CRgn`将对象设置为指定的矩形区域。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CRgn:: operator HRGN](#operator_hrgn)|返回`CRgn`对象中包含的 Windows 句柄。|

## <a name="remarks"></a>备注

区域是窗口中的椭圆形或多边形区域。 若要使用区域, 可以使用类`CRgn`的成员函数, 并将剪切函数定义为类`CDC`的成员。

的`CRgn`成员函数, 用于创建、更改和检索有关其被调用的区域对象的信息。

有关使用`CRgn`的详细信息, 请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="combinergn"></a>CRgn:: CombineRgn

通过合并两个现有区域来创建一个新的 GDI 区域。

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>参数

*pRgn1*<br/>
标识现有区域。

*pRgn2*<br/>
标识现有区域。

*nCombineMode*<br/>
指定合并两个源区域时要执行的操作。 它可以是下列值之一:

- RGN_AND 使用两个区域的重叠区域 (交集)。

- RGN_COPY 创建区域 1 (由*pRgn1*标识) 的副本。

- RGN_DIFF 创建一个区域, 该区域包含区域 1 (由*pRgn1*标识) 的区域, 这些区域不是区域 2 (由*pRgn2*标识) 的一部分。

- RGN_OR 将这两个区域组合在一起。

- RGN_XOR 结合了这两个区域, 但删除了重叠区域。

### <a name="return-value"></a>返回值

指定生成的区域的类型。 它可以是下列值之一:

- COMPLEXREGION 新区域包含重叠的边框。

- 错误: 没有创建新区域。

- NULLREGION 新区域为空。

- SIMPLEREGION 新区域没有重叠的边框。

### <a name="remarks"></a>备注

区域按*nCombineMode*指定的方式进行组合。

两个指定的区域是组合在一起的, 生成的区域句柄`CRgn`存储在对象中。 因此, 在`CRgn`对象中存储的任何区域都将替换为组合区域。

区域大小限制为 32767 x 32767 逻辑单元或64K 内存, 取两者中较小的一个。

使用[CopyRgn](#copyrgn)只需将一个区域复制到另一个区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>CRgn:: CopyRgn

将*pRgnSrc*定义的区域复制到`CRgn`对象中。

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>参数

*pRgnSrc*<br/>
标识现有区域。

### <a name="return-value"></a>返回值

指定生成的区域的类型。 它可以是下列值之一:

- COMPLEXREGION 新区域包含重叠的边框。

- 错误: 没有创建新区域。

- NULLREGION 新区域为空。

- SIMPLEREGION 新区域没有重叠的边框。

### <a name="remarks"></a>备注

新区域替换先前存储在`CRgn`对象中的区域。 此函数是[CombineRgn](#combinergn)成员函数的一种特殊情况。

### <a name="example"></a>示例

  请参阅[CRgn:: CreateEllipticRgn](#createellipticrgn)的示例。

##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn

创建一个椭圆形区域。

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定椭圆的边框的左上角的逻辑 x 坐标。

*y1*<br/>
指定椭圆的边框的左上角的逻辑 y 坐标。

*x2*<br/>
指定椭圆的边框的右下角的逻辑 x 坐标。

*y2*<br/>
指定椭圆的边框的右下角的逻辑 y 坐标。

### <a name="return-value"></a>返回值

如果操作成功, 则为非零;否则为0。

### <a name="remarks"></a>备注

区域由*x1*、 *y1*、 *x2*和*y2*指定的边框定义。 区域存储在`CRgn`对象中。

区域大小限制为 32767 x 32767 逻辑单元或64K 内存, 取两者中较小的一个。

当完成使用通过`CreateEllipticRgn`函数创建的区域时, 应用程序应从设备上下文中选择区域, 并`DeleteObject`使用函数将其删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect

创建一个椭圆形区域。

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向一个`RECT`结构`CRect`或对象, 该对象包含椭圆的边框的左上角和右下角的逻辑坐标。

### <a name="return-value"></a>返回值

如果操作成功, 则为非零;否则为0。

### <a name="remarks"></a>备注

区域由*lpRect*所指向的结构或对象定义, 并存储在`CRgn`对象中。

区域大小限制为 32767 x 32767 逻辑单元或64K 内存, 取两者中较小的一个。

当完成使用通过`CreateEllipticRgnIndirect`函数创建的区域时, 应用程序应从设备上下文中选择区域, 并`DeleteObject`使用函数将其删除。

### <a name="example"></a>示例

  请参阅[CRgn:: CreateRectRgnIndirect](#createrectrgnindirect)的示例。

##  <a name="createfromdata"></a>CRgn:: CreateFromData

从给定的区域创建区域和转换数据。

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>参数

*lpXForm*<br/>
指向[XFORM](/windows/desktop/api/wingdi/ns-wingdi-tagxform)数据结构, 该结构定义要在区域上执行的转换。 如果此指针为 NULL, 则使用标识转换。

*nCount*<br/>
指定*pRgnData*指向的字节数。

*pRgnData*<br/>
指向包含区域数据的[RGNDATA](/windows/desktop/api/wingdi/ns-wingdi-rgndata)数据结构。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

应用程序可以通过调用`CRgn::GetRegionData`函数来检索区域的数据。

##  <a name="createfrompath"></a>CRgn:: CreateFromPath

从选择到给定设备上下文的路径创建区域。

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
标识包含闭合路径的设备上下文。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

*PDC*参数标识的设备上下文必须包含关闭的路径。 将`CreateFromPath`路径转换为区域后, Windows 将从设备上下文中丢弃关闭的路径。

##  <a name="createpolygonrgn"></a>CRgn:: CreatePolygonRgn

创建多边形区域。

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>参数

*lpPoints*<br/>
指向结构的`POINT`数组或`CPoint`对象的数组。 每个结构都指定多边形的一个顶点的 x 坐标和 y 坐标。 `POINT`结构的格式如下:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
指定 lpPoints 所指向`POINT`的数组`CPoint`中结构或对象的数量。

*nMode*<br/>
指定区域的填充模式。 此参数可以是 "替换" 或 "缠绕"。

### <a name="return-value"></a>返回值

如果操作成功, 则为非零;否则为0。

### <a name="remarks"></a>备注

系统会根据需要, 通过从最后一个顶点到第一个顶点绘制线条来自动关闭多边形。 生成的区域存储在`CRgn`对象中。

区域大小限制为 32767 x 32767 逻辑单元或64K 内存, 取两者中较小的一个。

当多边形填充模式为备用模式时, 系统将在每个扫描行上填充奇数个和偶数个多边形边之间的区域。 也就是说, 系统在第三方和第四方之间填充区域, 依此类推。

当缠绕多边形填充模式时, 系统将使用绘制图形的方向来确定是否填充区域。 多边形中的每个线段以顺时针方向或逆时针方向绘制。 每当从封闭区域绘制到图形外的虚线通过顺时针直线段时, 计数就会增加。 当直线经过逆时针线段时, 计数将减少。 如果行到达图形外, 则会填充该区域。

当应用程序使用通过`CreatePolygonRgn`函数创建的区域完成时, 应从设备上下文中选择区域, 并`DeleteObject`使用函数将其删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>CRgn:: CreatePolyPolygonRgn

创建由一系列闭合多边形组成的区域。

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>参数

*lpPoints*<br/>
指向结构的`POINT`数组或定义多边形顶点的`CPoint`对象数组。 每个多边形都必须显式关闭, 因为系统不会自动将其关闭。 多边形是连续指定的。 `POINT`结构的格式如下:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
指向整数数组。 第一个整数指定*lpPoints*数组中第一个多边形的顶点数量, 第二个整数指定第二个多边形的顶点数量, 依此类推。

*nCount*<br/>
指定*lpPolyCounts*数组中整数的总数。

*nPolyFillMode*<br/>
指定多边形填充模式。 此值可以是 "替换" 或 "缠绕"。

### <a name="return-value"></a>返回值

如果操作成功, 则为非零;否则为0。

### <a name="remarks"></a>备注

生成的区域存储在`CRgn`对象中。

多边形可能是不相交的, 也可能是重叠的。

区域大小限制为 32767 x 32767 逻辑单元或64K 内存, 取两者中较小的一个。

当多边形填充模式为备用模式时, 系统将在每个扫描行上填充奇数个和偶数个多边形边之间的区域。 也就是说, 系统在第三方和第四方之间填充区域, 依此类推。

当缠绕多边形填充模式时, 系统将使用绘制图形的方向来确定是否填充区域。 多边形中的每个线段以顺时针方向或逆时针方向绘制。 每当从封闭区域绘制到图形外的虚线通过顺时针直线段时, 计数就会增加。 当直线经过逆时针线段时, 计数将减少。 如果行到达图形外, 则会填充该区域。

当应用程序完成使用通过`CreatePolyPolygonRgn`函数创建的区域时, 它应从设备上下文中选择区域, 并使用[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数将其删除。

##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn

创建存储在`CRgn`对象中的矩形区域。

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定区域左上角的逻辑 x 坐标。

*y1*<br/>
指定区域左上角的逻辑 y 坐标。

*x2*<br/>
指定区域右下角的逻辑 x 坐标。

*y2*<br/>
指定区域右下角的逻辑 y 坐标。

### <a name="return-value"></a>返回值

如果操作成功, 则为非零;否则为0。

### <a name="remarks"></a>备注

区域大小限制为 32767 x 32767 逻辑单元或64K 内存, 取两者中较小的一个。

使用创建`CreateRectRgn`的区域完成后, 应用程序应使用[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数删除该区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

有关其他示例, 请参阅[CRgn:: CombineRgn](#combinergn)。

##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect

创建存储在`CRgn`对象中的矩形区域。

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向一个`RECT`结构或`CRect`对象, 其中包含区域的左上角和右下角的逻辑坐标。 `RECT`结构的格式如下:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>返回值

如果操作成功, 则为非零;否则为0。

### <a name="remarks"></a>备注

区域大小限制为 32767 x 32767 逻辑单元或64K 内存, 取两者中较小的一个。

使用创建`CreateRectRgnIndirect`的区域完成后, 应用程序应使用[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数删除该区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>CRgn:: CreateRoundRectRgn

创建一个具有存储在`CRgn`对象中的圆角的矩形区域。

```
BOOL CreateRoundRectRgn(
    int x1,
    int y1,
    int x2,
    int y2,
    int x3,
    int y3);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定区域左上角的逻辑 x 坐标。

*y1*<br/>
指定区域左上角的逻辑 y 坐标。

*x2*<br/>
指定区域右下角的逻辑 x 坐标。

*y2*<br/>
指定区域右下角的逻辑 y 坐标。

*x3*<br/>
指定用于创建圆角的椭圆的宽度。

*y3*<br/>
指定用于创建圆角的椭圆的高度。

### <a name="return-value"></a>返回值

如果操作成功, 则为非零;否则为0。

### <a name="remarks"></a>备注

区域大小限制为 32767 x 32767 逻辑单元或64K 内存, 取两者中较小的一个。

当应用程序完成使用通过`CreateRoundRectRgn`函数创建的区域时, 它应从设备上下文中选择区域, 并使用[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数将其删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>CRgn:: CRgn

构造 `CRgn` 对象。

```
CRgn();
```

### <a name="remarks"></a>备注

在`m_hObject`使用一个或多个其他`CRgn`成员函数初始化对象之前, 数据成员不包含有效的 Windows GDI 区域。

### <a name="example"></a>示例

  请参阅[CRgn:: CreateRoundRectRgn](#createroundrectrgn)的示例。

##  <a name="equalrgn"></a>CRgn:: EqualRgn

确定给定区域是否等效于`CRgn`对象中存储的区域。

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>参数

*pRgn*<br/>
标识区域。

### <a name="return-value"></a>返回值

如果两个区域等效, 则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>CRgn:: FromHandle

当给定 Windows 区域的`CRgn`句柄时, 返回指向对象的指针。

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>参数

*hRgn*<br/>
指定 Windows 区域的句柄。

### <a name="return-value"></a>返回值

指向 `CRgn` 对象的指针。 如果该函数不成功, 则返回值为 NULL。

### <a name="remarks"></a>备注

如果对象尚未附加到句柄, 则会创建并附加`CRgn`一个临时对象。 `CRgn` 此临时`CRgn`对象仅在下一次应用程序的事件循环中有空闲时间时才有效, 此时所有临时图形对象都会被删除。 指出这一点的另一种方法是: 只有在处理一条窗口消息的过程中, 临时对象才有效。

##  <a name="getregiondata"></a>CRgn:: GetRegionData

用描述区域的数据填充指定的缓冲区。

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>参数

*lpRgnData*<br/>
指向接收信息的[RGNDATA](/windows/desktop/api/wingdi/ns-wingdi-rgndata)数据结构。 如果此参数为 NULL, 则返回值包含区域数据所需的字节数。

*nCount*<br/>
指定*lpRgnData*缓冲区的大小 (以字节为单位)。

### <a name="return-value"></a>返回值

如果函数成功并且*nCount*指定了足够的字节数, 则返回值始终为*nCount*。 如果函数失败, 或*nCount*指定的字节数少于适当值, 则返回值为 0 (错误)。

### <a name="remarks"></a>备注

此数据包括组成区域的矩形的尺寸。 此函数与`CRgn::CreateFromData`函数结合使用。

##  <a name="getrgnbox"></a>CRgn:: GetRgnBox

检索`CRgn`对象的边框的坐标。

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向一个`RECT`结构或`CRect`对象, 用于接收边框的坐标。 `RECT`结构的格式如下:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>返回值

指定区域的类型。 可以是下列值之一:

- COMPLEXREGION 区域包含重叠边界。

- NULLREGION 区域为空。

- 错误`CRgn`对象未指定有效的区域。

- SIMPLEREGION 区域没有重叠的边框。

### <a name="example"></a>示例

  请参阅[CRgn:: CreatePolygonRgn](#createpolygonrgn)的示例。

##  <a name="offsetrgn"></a>  CRgn::OffsetRgn

按指定的偏移量移动`CRgn`对象中存储的区域。

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>参数

*x*<br/>
指定向左或向右移动的单位数。

*y*<br/>
指定要上移或下移的单位数。

*point*<br/>
*点*的 x 坐标指定向左或向右移动的单位数。 *点*的 y 坐标指定了要上移或下移的单位数。 *Point*参数可以`POINT`是结构, 也`CPoint`可以是对象。

### <a name="return-value"></a>返回值

新区域的类型。 它可以是下列值之一:

- COMPLEXREGION 区域包含重叠边界。

- 错误区域句柄无效。

- NULLREGION 区域为空。

- SIMPLEREGION 区域没有重叠的边框。

### <a name="remarks"></a>备注

函数沿 x 轴和 y 轴沿 y 轴移动区域*x*单位。

区域的坐标值必须小于或等于32767且大于或等于-32768。 必须仔细选择*x*和*y*参数, 以防止无效的区域坐标。

### <a name="example"></a>示例

  请参阅[CRgn:: CreateEllipticRgn](#createellipticrgn)的示例。

##  <a name="operator_hrgn"></a>CRgn:: operator HRGN

使用此运算符可获取`CRgn`对象的附加 Windows GDI 句柄。

```
operator HRGN() const;
```

### <a name="return-value"></a>返回值

如果成功, 则为`CRgn`对象表示的 Windows GDI 对象的句柄; 否则为 NULL。

### <a name="remarks"></a>备注

此运算符是支持直接使用 HRGN 对象的强制转换运算符。

有关使用图形对象的详细信息, 请参阅文章 Windows SDK 中的[图形对象](/windows/desktop/gdi/graphic-objects)。

##  <a name="ptinregion"></a>CRgn::P tInRegion

检查*x*和*y*给定的点是否位于`CRgn`对象中存储的区域内。

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>参数

*x*<br/>
指定要测试的点的逻辑 x 坐标。

*y*<br/>
指定要测试的点的逻辑 y 坐标。

*point*<br/>
*点*的 x 和 y 坐标指定了测试值的点的 x 和 y 坐标。 *Point*参数可以是`POINT`结构, 也`CPoint`可以是对象。

### <a name="return-value"></a>返回值

如果点在区域中, 则为非零值;否则为0。

##  <a name="rectinregion"></a>  CRgn::RectInRegion

确定*lpRect*指定的矩形的任何部分是否在`CRgn`对象中存储的区域的边界内。

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向结构或`CRect`对象。 `RECT` `RECT`结构的格式如下:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>返回值

如果指定矩形的任何部分位于区域边界内, 则为非零值;否则为0。

##  <a name="setrectrgn"></a>  CRgn::SetRectRgn

创建一个矩形区域。

```
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定矩形区域左上角的 x 坐标。

*y1*<br/>
指定矩形区域左上角的 y 坐标。

*x2*<br/>
指定矩形区域右下角的 x 坐标。

*y2*<br/>
指定矩形区域右下角的 y 坐标。

*lpRect*<br/>
指定矩形区域。 可以是指向`RECT`结构`CRect`或对象的指针。

### <a name="remarks"></a>备注

但与[CreateRectRgn](#createrectrgn)不同, 它不会从本地 Windows 应用程序堆分配任何其他内存。 而是使用为存储在`CRgn`对象中的区域分配的空间。 这意味着, `CRgn`在调用`SetRectRgn`之前, 对象必须已使用有效的 Windows 区域进行了初始化。 *X1*, *y1*, *x2*, *y2*给定的点指定所分配空间的最小大小。

使用此函数 (而不`CreateRectRgn`是成员函数) 来避免调用本地内存管理器。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
