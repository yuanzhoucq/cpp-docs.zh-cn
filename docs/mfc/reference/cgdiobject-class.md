---
title: CGdiObject 类
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: 1b2b87173bf504455ba314fdd89ffae298cae6a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181985"
---
# <a name="cgdiobject-class"></a>CGdiObject 类

为各种 Windows 图形设备接口 (GDI) 对象（如位图、区域、画笔、笔、调色板和字体）提供基类。

## <a name="syntax"></a>语法

```
class CGdiObject : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|构造 `CGdiObject` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CGdiObject::Attach](#attach)|将附加到 Windows GDI 对象`CGdiObject`对象。|
|[CGdiObject::CreateStockObject](#createstockobject)|检索 Windows 预定义的股票钢笔、 画笔或字体之一的句柄。|
|[CGdiObject::DeleteObject](#deleteobject)|删除 Windows GDI 对象附加到`CGdiObject`从内存释放与对象关联的所有系统存储对象。|
|[CGdiObject::DeleteTempMap](#deletetempmap)|删除任何临时`CGdiObject`创建的对象`FromHandle`。|
|[CGdiObject::Detach](#detach)|分离中的 Windows GDI 对象`CGdiObject`对象并返回的句柄的 Windows GDI 对象。|
|[CGdiObject::FromHandle](#fromhandle)|返回一个指向`CGdiObject`提供给 Windows GDI 对象的句柄的对象。|
|[CGdiObject::GetObject](#getobject)|填充具有描述 Windows GDI 对象的数据的缓冲区将附加到`CGdiObject`对象。|
|[CGdiObject::GetObjectType](#getobjecttype)|检索的 GDI 对象的类型。|
|[CGdiObject::GetSafeHandle](#getsafehandle)|返回`m_hObject`除非**这**为的 NULL，在其中返回事例的 NULL。|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|重置画笔的原点或重置逻辑调色板。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CGdiObject::operator !=](#operator_neq)|确定两个 GDI 对象是否以逻辑方式不相等。|
|[CGdiObject::operator ==](#operator_eq_eq)|确定两个 GDI 对象是否从逻辑上相等。|
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|检索附加 Windows GDI 对象的句柄。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|包含 HBITMAP、 HPALETTE、 HRGN、 HBRUSH、 HPEN 或 HFONT 句柄附加到此对象。|

## <a name="remarks"></a>备注

永远不会创建`CGdiObject`直接。 而是创建的对象从其派生类，如`CPen`或`CBrush`。

有关详细信息`CGdiObject`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="attach"></a>  CGdiObject::Attach

将附加到 Windows GDI 对象`CGdiObject`对象。

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>参数

*hObject*<br/>
Windows GDI 对象 （例如，HPEN 或 HBRUSH） 的句柄。

### <a name="return-value"></a>返回值

如果附件是成功，则非零值否则为 0。

##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject

构造 `CGdiObject` 对象。

```
CGdiObject();
```

### <a name="remarks"></a>备注

永远不会创建`CGdiObject`直接。 而是创建的对象从其派生类，如`CPen`或`Cbrush`。

##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject

检索的句柄为预定义的常用 Windows GDI 钢笔、 画笔或字体，并附加到的 GDI 对象`CGdiObject`对象。

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个常数，指定所需的常用对象的类型。 请参阅参数*fnObject*有关[GetStockObject](/windows/desktop/api/wingdi/nf-wingdi-getstockobject) Windows SDK 的适当值的说明中。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

调用此函数具有一个将派生的类的对应 Windows GDI 对象类型，如`CPen`为常用的画笔。

##  <a name="deleteobject"></a>  CGdiObject::DeleteObject

通过释放与 Windows GDI 对象相关联的所有系统存储从内存中删除附加的 Windows GDI 对象。

```
BOOL DeleteObject();
```

### <a name="return-value"></a>返回值

已成功删除的 GDI 对象; 如果非零值否则为 0。

### <a name="remarks"></a>备注

与关联的存储`CGdiObject`对象不受此调用。 应用程序不应调用`DeleteObject`上`CGdiObject`当前所选入设备上下文的对象。

删除模式画笔时，不会删除与画笔相关联的位图。 必须单独删除位图。

##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap

自动调用`CWinApp`空闲时间处理程序`DeleteTempMap`删除临时`CGdiObject`创建的对象`FromHandle`。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>备注

`DeleteTempMap` 分离 Windows GDI 对象附加到一个临时`CGdiObject`对象删除之前`CGdiObject`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

##  <a name="detach"></a>  CGdiObject::Detach

分离中的 Windows GDI 对象`CGdiObject`对象并返回的句柄的 Windows GDI 对象。

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>返回值

一个`HANDLE`向 Windows GDI 对象分离; 否则为 NULL 如果连接没有任何 GDI 对象。

##  <a name="fromhandle"></a>  CGdiObject::FromHandle

返回一个指向`CGdiObject`提供给 Windows GDI 对象的句柄的对象。

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>参数

*hObject*<br/>
Windows GDI 对象的句柄。

### <a name="return-value"></a>返回值

一个指向`CGdiObject`这可能是临时的还是永久。

### <a name="remarks"></a>备注

如果`CGdiObject`对象尚未附加到 Windows GDI 对象，临时`CGdiObject`创建并附加对象。

此临时`CGdiObject`对象下一次该应用程序在其事件循环中，此时会删除所有临时图形对象有空闲时间之前才有效。 另一种说法： 这是一个窗口消息处理过程才有效的临时对象。

##  <a name="getobject"></a>  CGdiObject::GetObject

定义指定的对象的数据填充缓冲区。

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>参数

*nCount*<br/>
指定要将复制到的字节数*lpObject*缓冲区。

*lpObject*<br/>
指向接收信息的用户提供缓冲区。

### <a name="return-value"></a>返回值

检索的字节数;否则为 0，如果错误发生。

### <a name="remarks"></a>备注

以下列表所示，该函数将检索其类型取决于图形对象的类型的数据结构：

|对象|缓冲区类型|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/desktop/api/Wingdi/ns-wingdi-taglogpen)|
|`CBrush`|[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)|
|`CFont`|[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)|
|`CBitmap`|[BITMAP](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap)|
|`CPalette`|WORD|
|`CRgn`|不支持|

如果对象是`CBitmap`对象，`GetObject`返回宽度、 高度和颜色位图的格式信息。 可以通过使用来检索实际的位[CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)。

如果对象是`CPalette`对象，`GetObject`检索调色板中指定的条目数的词。 该函数不会检索[LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette)结构，它定义调色板。 应用程序可以通过调用获取调色板条目的信息[CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries)。

##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType

检索的 GDI 对象的类型。

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>返回值

类型的对象，如果成功，则否则为 0。 值可以是下列任一值：

- OBJ_BITMAP Bitmap

- OBJ_BRUSH 画笔

- OBJ_FONT 字体

- OBJ_PAL 调色板

- OBJ_PEN 笔

- OBJ_EXTPEN 扩展笔

- OBJ_REGION 区域

- OBJ_DC 设备上下文

- OBJ_MEMDC 内存设备上下文

- OBJ_METAFILE 图元文件

- OBJ_METADC 图元文件设备上下文

- OBJ_ENHMETAFILE 增强型图元文件

- OBJ_ENHMETADC 增强型图元文件设备上下文

##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle

返回`m_hObject`除非**这**为的 NULL，在其中返回事例的 NULL。

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>返回值

附加的 Windows GDI 对象; 的句柄如果连接没有任何对象，否则为 NULL。

### <a name="remarks"></a>备注

这是常规的句柄界面范例的一部分，NULL 句柄无效，或者特殊值时非常有用。

### <a name="example"></a>示例

  有关示例，请参阅[CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled)。

##  <a name="m_hobject"></a>  CGdiObject::m_hObject

包含 HBITMAP、 HRGN、 HBRUSH、 HPEN、 HPALETTE 或 HFONT 句柄附加到此对象。

```
HGDIOBJ m_hObject;
```

##  <a name="operator_neq"></a>  CGdiObject::operator ！ =

确定两个 GDI 对象是否以逻辑方式不相等。

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>参数

*obj*<br/>
一个指向现有`CGdiObject`。

### <a name="remarks"></a>备注

确定左侧和右侧的 GDI 对象是否不等于右侧的 GDI 对象。

##  <a name="operator_eq_eq"></a>  CGdiObject::operator ==

确定两个 GDI 对象是否从逻辑上相等。

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>参数

*obj*<br/>
向现有的引用`CGdiObject`。

### <a name="remarks"></a>备注

确定左侧和右侧的 GDI 对象是否等于右侧的 GDI 对象。

##  <a name="operator_hgdiobj"></a>  CGdiObject::operator HGDIOBJ

检索的句柄附加的 Windows GDI 对象;如果连接没有任何对象，否则为 NULL。

```
operator HGDIOBJ() const;
```

##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject

重置画笔的原点或重置逻辑调色板。

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

虽然`UnrealizeObject`是的成员函数`CGdiObject`类，它应调用仅`CBrush`或`CPalette`对象。

有关`CBrush`对象，`UnrealizeObject`指示系统在重置给定画笔的原点选入设备上下文的下一个时间。 如果对象是`CPalette`对象，`UnrealizeObject`指示系统在实现调色板，就好像它已不以前已意识到。 下一次应用程序调用[CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)函数为指定的面板中，系统完全重新映射到系统调色板的逻辑调色板。

`UnrealizeObject`函数不应使用与常用的对象。 `UnrealizeObject`必须调用函数，每当设置新的画笔原点 (通过[CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg)函数)。 `UnrealizeObject`必须不为当前选定的画笔或当前所选的任何的调色板显示上下文中调用函数。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 类](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush 类](../../mfc/reference/cbrush-class.md)<br/>
[CFont 类](../../mfc/reference/cfont-class.md)<br/>
[CPalette 类](../../mfc/reference/cpalette-class.md)<br/>
[CPen 类](../../mfc/reference/cpen-class.md)<br/>
[CRgn 类](../../mfc/reference/crgn-class.md)
