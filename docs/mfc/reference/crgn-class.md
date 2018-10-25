---
title: CRgn 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f6ed7b94509c5dafd868680254c5f48f0066b7f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054223"
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
|[CRgn::CRgn](#crgn)|构造 `CRgn` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|集`CRgn`对象，以便它相当于两个指定的联合`CRgn`对象。|
|[CRgn::CopyRgn](#copyrgn)|集`CRgn`对象，以便它是一份指定的`CRgn`对象。|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|初始化`CRgn`具有椭圆区域的对象。|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|初始化`CRgn`对象具有定义的椭圆区域[RECT](../../mfc/reference/rect-structure1.md)结构。|
|[CRgn::CreateFromData](#createfromdata)|从给定的区域和转换数据创建一个区域。|
|[CRgn::CreateFromPath](#createfrompath)|从给定的设备上下文中所选的路径创建一个区域。|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|初始化`CRgn`与多边形区域的对象。 系统多边形会自动关闭，如有必要，通过绘制一条从最后一个顶点与第一个。|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|初始化`CRgn`对象已关闭的多边形的一系列组成的区域。 多边形可能是连续的也可能会重叠。|
|[CRgn::CreateRectRgn](#createrectrgn)|初始化`CRgn`对象的矩形区域。|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|初始化`CRgn`对象定义的矩形区域[RECT](../../mfc/reference/rect-structure1.md)结构。|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|初始化`CRgn`具有圆角的矩形区域的对象。|
|[CRgn::EqualRgn](#equalrgn)|检查两个`CRgn`对象以确定它们是否等效。|
|[CRgn::FromHandle](#fromhandle)|返回一个指向`CRgn`对象时提供给 Windows 区域的句柄。|
|[CRgn::GetRegionData](#getregiondata)|描述给定的区域的数据填充指定的缓冲区。|
|[CRgn::GetRgnBox](#getrgnbox)|检索矩形的边框的坐标`CRgn`对象。|
|[CRgn::OffsetRgn](#offsetrgn)|将移动`CRgn`对象指定的偏移量。|
|[CRgn::PtInRegion](#ptinregion)|确定指定的点是否在区域中。|
|[CRgn::RectInRegion](#rectinregion)|确定指定的任何的矩形部分是否为区域的边界内。|
|[CRgn::SetRectRgn](#setrectrgn)|集`CRgn`对象与指定的矩形区域。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CRgn::operator HRGN](#operator_hrgn)|返回中包含的 Windows 句柄`CRgn`对象。|

## <a name="remarks"></a>备注

区域是一个窗口内的一个椭圆或多边形区域。 若要使用的区域，应使用类的成员函数`CRgn`这两个剪辑函数定义为类的成员`CDC`。

成员函数的`CRgn`创建、 更改和检索有关调用它们的区域对象的信息。

有关使用的详细信息`CRgn`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="combinergn"></a>  CRgn::CombineRgn

通过组合两个现有区域来创建新的 GDI 区域。

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
指定要合并两个源区域时执行的操作。 它可以是以下值之一：

- RGN_AND 使用重叠的这两个区域 （交集） 的区域。

- RGN_COPY 创建区域 1 的副本 (由标识*pRgn1*)。

- RGN_DIFF 创建包含区域 1 的区域的区域 (由标识*pRgn1*) 的不是区域 2 的一部分 (由标识*pRgn2*)。

- RGN_OR 结合了这两个区域中整个 （联合）。

- RGN_XOR 结合了这两个区域，但删除重叠区域。

### <a name="return-value"></a>返回值

指定所生成的区域的类型。 它可以是下列值之一：

- COMPLEXREGION 新的区域有重叠的边框。

- 创建任何新区域时出错。

- NULLREGION 新的区域为空。

- SIMPLEREGION 新区域具有不重叠的边框。

### <a name="remarks"></a>备注

区域组合所指定的*nCombineMode*。

两个指定的区域组合，并生成区域句柄存储在`CRgn`对象。 因此，任何区域存储在`CRgn`对象被替换的组合的区域。

区域的大小限制为 32,767 的 32767 的逻辑单元或 64k 的内存，两者中较小。

使用[CopyRgn](#copyrgn)只需将一个区域复制到另一个区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>  CRgn::CopyRgn

将复制由定义的区域*pRgnSrc*到`CRgn`对象。

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>参数

*pRgnSrc*<br/>
标识现有区域。

### <a name="return-value"></a>返回值

指定所生成的区域的类型。 它可以是下列值之一：

- COMPLEXREGION 新的区域有重叠的边框。

- 创建任何新区域时出错。

- NULLREGION 新的区域为空。

- SIMPLEREGION 新区域具有不重叠的边框。

### <a name="remarks"></a>备注

新区域将替换以前存储在区域`CRgn`对象。 此函数是一种特殊的情况[CombineRgn](#combinergn)成员函数。

### <a name="example"></a>示例

  有关示例，请参阅[CRgn::CreateEllipticRgn](#createellipticrgn)。

##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn

创建椭圆的区域。

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定的椭圆的边框的左上角的逻辑 x 坐标。

*y1*<br/>
指定的椭圆的边框的左上角的逻辑 y 坐标。

*x2*<br/>
指定的椭圆的边框右下角的逻辑 x 坐标。

*y2*<br/>
指定的椭圆的边框右下角的逻辑 y 坐标。

### <a name="return-value"></a>返回值

如果操作成功，则非零值否则为 0。

### <a name="remarks"></a>备注

在区域定义的由指定的边界矩形*x1*， *y1*， *x2*，以及*y2*。 在区域存储在`CRgn`对象。

区域的大小限制为 32,767 的 32767 的逻辑单元或 64k 的内存，两者中较小。

是否已完成使用与创建的区域`CreateEllipticRgn`函数，应用程序应选择的设备上下文和使用的区域出`DeleteObject`函数以将其删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect

创建椭圆的区域。

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`结构或`CRect`对象，其中包含椭圆的边框的左上角和右下角中的逻辑坐标。

### <a name="return-value"></a>返回值

如果操作成功，则非零值否则为 0。

### <a name="remarks"></a>备注

在区域定义的结构或指向的对象*lpRect*并存储在`CRgn`对象。

区域的大小限制为 32,767 的 32767 的逻辑单元或 64k 的内存，两者中较小。

是否已完成使用与创建的区域`CreateEllipticRgnIndirect`函数，应用程序应选择的设备上下文和使用的区域出`DeleteObject`函数以将其删除。

### <a name="example"></a>示例

  有关示例，请参阅[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)。

##  <a name="createfromdata"></a>  CRgn::CreateFromData

从给定的区域和转换数据创建一个区域。

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>参数

*lpXForm*<br/>
指向[XFORM](../../mfc/reference/xform-structure.md)数据结构，它定义要在区域上执行的转换。 如果该指针为 NULL，则使用恒等转换。

*nCount*<br/>
指定指向的字节数*pRgnData*。

*pRgnData*<br/>
指向[RGNDATA](../../mfc/reference/rgndata-structure.md)数据结构，其中包含区域数据。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

应用程序可以通过调用来检索区域的数据`CRgn::GetRegionData`函数。

##  <a name="createfrompath"></a>  CRgn::CreateFromPath

从给定的设备上下文中所选的路径创建一个区域。

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
标识包含封闭的路径的设备上下文。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

通过标识的设备上下文*pDC*参数必须包含封闭的路径。 之后`CreateFromPath`将某个区域，Windows 路径转换丢弃从设备上下文已关闭的路径。

##  <a name="createpolygonrgn"></a>  CRgn::CreatePolygonRgn

创建一个多边形的区域。

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>参数

*lpPoints*<br/>
指向数组`POINT`结构或一组`CPoint`对象。 每个结构指定的 x 坐标和 y 坐标的多边形的一个顶点。 `POINT`结构具有以下形式：

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
指定的数量`POINT`结构或`CPoint`指向数组中的对象*lpPoints*。

*nMode*<br/>
指定区域的填充模式。 此参数可以为备用或缠绕。

### <a name="return-value"></a>返回值

如果操作成功，则非零值否则为 0。

### <a name="remarks"></a>备注

系统多边形会自动关闭，如有必要，通过绘制一条从最后一个顶点与第一个。 所生成的区域存储在`CRgn`对象。

区域的大小限制为 32,767 的 32767 的逻辑单元或 64k 的内存，两者中较小。

备用的多边形填充模式时，系统将填充每个扫描行上的奇数和偶数多边形边之间的区域。 它是系统填充区域的第一个和第二个端之间、 之间的第三个和第四个端，依此类推。

绕组多边形填充模式下，系统会将在其中绘制图来确定是否填充区域的方向。 顺时针或逆时针方向绘制多边形内的每个直线线段。 每当从封闭区域到图的外面绘制的虚线通过顺时针线段，计数将递增。 行在经过一开始沿逆时针方向条线段，计数将减少。 如果在行达到图外部时，计数为非零值，填充区域。

当应用程序使用完与创建的区域`CreatePolygonRgn`函数，它应选择的设备上下文和使用的区域出`DeleteObject`函数以将其删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn

创建包含的一系列的闭合的多边形的区域。

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>参数

*lpPoints*<br/>
指向数组`POINT`结构或一组`CPoint`定义多边形顶点的对象。 必须显式关闭每个多边形，因为系统不会自动关闭它们。 多边形指定连续。 `POINT`结构具有以下形式：

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
指向整数的数组。 第一个整数中的第一个多边形中指定的顶点数*lpPoints*数组，第二个整数指定的顶点数中的第二个多边形，依此类推。

*nCount*<br/>
指定在整数的总数*lpPolyCounts*数组。

*nPolyFillMode*<br/>
指定的多边形填充模式。 此值可能为备用或缠绕。

### <a name="return-value"></a>返回值

如果操作成功，则非零值否则为 0。

### <a name="remarks"></a>备注

所生成的区域存储在`CRgn`对象。

多边形可能是连续的也可能会重叠。

区域的大小限制为 32,767 的 32767 的逻辑单元或 64k 的内存，两者中较小。

备用的多边形填充模式时，系统将填充每个扫描行上的奇数和偶数多边形边之间的区域。 它是系统填充区域的第一个和第二个端之间、 之间的第三个和第四个端，依此类推。

绕组多边形填充模式下，系统会将在其中绘制图来确定是否填充区域的方向。 顺时针或逆时针方向绘制多边形内的每个直线线段。 每当从封闭区域到图的外面绘制的虚线通过顺时针线段，计数将递增。 行在经过一开始沿逆时针方向条线段，计数将减少。 如果在行达到图外部时，计数为非零值，填充区域。

当应用程序使用完与创建的区域`CreatePolyPolygonRgn`函数，它应选择的设备上下文和使用的区域出[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数以将其删除。

##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn

创建存储中的矩形区域`CRgn`对象。

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>参数

*x1*<br/>
指定区域的左上角的逻辑 x 坐标。

*y1*<br/>
指定区域的左上角的逻辑 y 坐标。

*x2*<br/>
指定区域的右下角的逻辑 x 坐标。

*y2*<br/>
指定区域的右下角的逻辑 y 坐标。

### <a name="return-value"></a>返回值

如果操作成功，则非零值否则为 0。

### <a name="remarks"></a>备注

区域的大小限制为 32,767 的 32767 的逻辑单元或 64k 的内存，两者中较小。

是否已完成使用创建的区域`CreateRectRgn`，应用程序应使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数，若要删除区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

有关其他示例，请参阅[CRgn::CombineRgn](#combinergn)。

##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect

创建存储中的矩形区域`CRgn`对象。

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`结构或`CRect`对象，其中包含区域的左上角和右下角中的逻辑坐标。 `RECT`结构具有以下形式：

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>返回值

如果操作成功，则非零值否则为 0。

### <a name="remarks"></a>备注

区域的大小限制为 32,767 的 32767 的逻辑单元或 64k 的内存，两者中较小。

是否已完成使用创建的区域`CreateRectRgnIndirect`，应用程序应使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数，若要删除区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>  CRgn::CreateRoundRectRgn

创建包含存储中的圆角矩形区域`CRgn`对象。

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
指定区域的左上角的逻辑 x 坐标。

*y1*<br/>
指定区域的左上角的逻辑 y 坐标。

*x2*<br/>
指定区域的右下角的逻辑 x 坐标。

*y2*<br/>
指定区域的右下角的逻辑 y 坐标。

*x3*<br/>
指定用于创建圆的角的椭圆宽度。

*y3*<br/>
指定用于创建圆的角的椭圆的高度。

### <a name="return-value"></a>返回值

如果操作成功，则非零值否则为 0。

### <a name="remarks"></a>备注

区域的大小限制为 32,767 的 32767 的逻辑单元或 64k 的内存，两者中较小。

当应用程序使用完与创建的区域`CreateRoundRectRgn`函数，它应选择的设备上下文和使用的区域出[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数以将其删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>  CRgn::CRgn

构造 `CRgn` 对象。

```
CRgn();
```

### <a name="remarks"></a>备注

`m_hObject`数据成员不包含有效的 Windows GDI 区域之前初始化对象，一个或多个其他`CRgn`成员函数。

### <a name="example"></a>示例

  有关示例，请参阅[CRgn::CreateRoundRectRgn](#createroundrectrgn)。

##  <a name="equalrgn"></a>  CRgn::EqualRgn

确定给定的区域是否等效于存储在区域`CRgn`对象。

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>参数

*pRgn*<br/>
标识的区域。

### <a name="return-value"></a>返回值

如果两个区域相等，则非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>  CRgn::FromHandle

返回一个指向`CRgn`对象时提供给 Windows 区域的句柄。

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>参数

*hRgn*<br/>
指定的句柄的 Windows 区域。

### <a name="return-value"></a>返回值

指向 `CRgn` 对象的指针。 如果该函数不成功，返回值为 NULL。

### <a name="remarks"></a>备注

如果`CRgn`对象尚未附加到句柄，临时`CRgn`创建并附加对象。 此临时`CRgn`对象仅用于有效直到下一次应用程序在其事件循环内有空闲时间，在该时间所有临时图形对象会被删除。 另一种说法： 这是一个窗口消息处理过程才有效的临时对象。

##  <a name="getregiondata"></a>  CRgn::GetRegionData

用以将区域的数据填充指定的缓冲区。

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>参数

*lpRgnData*<br/>
指向[RGNDATA](../../mfc/reference/rgndata-structure.md)数据结构，它接收的信息。 如果此参数为 NULL，返回值将包含所需的区域数据的字节数。

*nCount*<br/>
指定的大小，以字节为单位， *lpRgnData*缓冲区。

### <a name="return-value"></a>返回值

如果函数成功并*nCount*指定足够数目的字节数，返回值也始终*nCount*。 如果函数失败，或如果*nCount*指定小于比足够数量的字节数，返回值为 0 （错误）。

### <a name="remarks"></a>备注

此数据包括组成区域的矩形的尺寸。 结合使用此函数`CRgn::CreateFromData`函数。

##  <a name="getrgnbox"></a>  CRgn::GetRgnBox

检索矩形的边框的坐标`CRgn`对象。

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`结构或`CRect`对象以接收的边框的坐标。 `RECT`结构具有以下形式：

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>返回值

指定区域的类型。 它可以是以下值之一：

- COMPLEXREGION 区域有重叠的边框。

- NULLREGION 区域为空。

- 错误`CRgn`对象未指定有效的区域。

- SIMPLEREGION 区域具有不重叠的边框。

### <a name="example"></a>示例

  有关示例，请参阅[CRgn::CreatePolygonRgn](#createpolygonrgn)。

##  <a name="offsetrgn"></a>  CRgn::OffsetRgn

将存储在区域`CRgn`对象指定的偏移量。

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>参数

*x*<br/>
指定要向左移动或向右的单位数。

*y*<br/>
指定要上移或下移的单位数。

*点*<br/>
X 坐标*点*指定要向左移动或向右的单元数。 Y 坐标*点*指定要上移或下移的单位数。 *点*参数可以是`POINT`结构或`CPoint`对象。

### <a name="return-value"></a>返回值

新区域的类型。 它可以是以下值之一：

- COMPLEXREGION 区域有重叠的边框。

- 错误区域句柄无效。

- NULLREGION 区域为空。

- SIMPLEREGION 区域具有不重叠的边框。

### <a name="remarks"></a>备注

该函数将在区域*x*沿 x 轴单位并*y*沿 y 轴的单位。

区域的坐标值必须小于或等于 32,767 且大于或等于-32,768。 *X*并*y*参数必须精心挑选，用于防止无效的区域坐标。

### <a name="example"></a>示例

  有关示例，请参阅[CRgn::CreateEllipticRgn](#createellipticrgn)。

##  <a name="operator_hrgn"></a>  CRgn::operator HRGN

此运算符用于获取附加的 Windows GDI 句柄的`CRgn`对象。

```
operator HRGN() const;
```

### <a name="return-value"></a>返回值

如果成功，Windows GDI 对象的句柄由`CRgn`对象; 否则为 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，它支持 HRGN 对象的直接使用。

有关使用图形对象的详细信息，请参阅文章[图形对象](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

##  <a name="ptinregion"></a>  CRgn::PtInRegion

检查是否提供的点*x*并*y*存储在区域中`CRgn`对象。

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

*点*<br/>
X 和 y 坐标*点*指定要测试的值的点 x 和 y 坐标。 *点*参数可以是`POINT`结构或`CPoint`对象。

### <a name="return-value"></a>返回值

非零，如果该点位于区域;否则为 0。

##  <a name="rectinregion"></a>  CRgn::RectInRegion

确定指定的矩形的任何部分*lpRect*中存储的区域的边界内`CRgn`对象。

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`结构或`CRect`对象。 `RECT`结构具有以下形式：

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>返回值

如果指定任何的矩形部分的区域边界内，非零值否则为 0。

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
指定的矩形区域左上角的 x 坐标。

*y1*<br/>
指定的矩形区域左上角的 y 坐标。

*x2*<br/>
指定的矩形区域右下角的 x 坐标。

*y2*<br/>
指定的矩形区域右下角的 y 坐标。

*lpRect*<br/>
指定的矩形区域。 可以是到指针`RECT`结构或`CRect`对象。

### <a name="remarks"></a>备注

与不同[CreateRectRgn](#createrectrgn)，但是，它不会分配任何额外的内存从本地 Windows 应用程序堆。 相反，它使用的空间分配区域存储在`CRgn`对象。 这意味着`CRgn`对象必须具有已初始化与之前调用有效的 Windows 区域`SetRectRgn`。 通过给定的点*x1*， *y1*， *x2*，以及*y2*指定已分配空间的最小大小。

使用此函数，而不是`CreateRectRgn`成员函数以避免对本地内存管理器的调用。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

