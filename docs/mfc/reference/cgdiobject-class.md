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
ms.openlocfilehash: 759b25a8f77bb4e6b372431b637b4a97aca8e149
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212405"
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

|“属性”|描述|
|----------|-----------------|
|[CGdiObject：： Attach](#attach)|将 Windows GDI 对象附加到 `CGdiObject` 对象。|
|[CGdiObject::CreateStockObject](#createstockobject)|检索某个 Windows 预定义的股票笔、画笔或字体的句柄。|
|[CGdiObject：:D eleteObject](#deleteobject)|`CGdiObject`通过释放与对象关联的所有系统存储，从内存中删除附加到对象的 WINDOWS GDI 对象。|
|[CGdiObject：:D eleteTempMap](#deletetempmap)|删除 `CGdiObject` 由创建的任何临时对象 `FromHandle` 。|
|[CGdiObject：:D etach](#detach)|从对象中分离 Windows GDI 对象 `CGdiObject` ，并返回 WINDOWS gdi 对象的句柄。|
|[CGdiObject：： FromHandle](#fromhandle)|返回一个指向对象的指针，该指针指向 `CGdiObject` 给定 WINDOWS GDI 对象的句柄。|
|[CGdiObject：： GetObject](#getobject)|使用描述附加到对象的 Windows GDI 对象的数据填充缓冲区 `CGdiObject` 。|
|[CGdiObject::GetObjectType](#getobjecttype)|检索 GDI 对象的类型。|
|[CGdiObject::GetSafeHandle](#getsafehandle)|`m_hObject`如果 **`this`** 为 null，则返回，在这种情况下返回 null。|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|重置画笔的原点或重置逻辑调色板。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CGdiObject：： operator！ =](#operator_neq)|确定两个 GDI 对象是否逻辑上不相等。|
|[CGdiObject：： operator = =](#operator_eq_eq)|确定两个 GDI 对象是否逻辑上相等。|
|[CGdiObject：： operator HGDIOBJ](#operator_hgdiobj)|检索附加的 Windows GDI 对象的句柄。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CGdiObject：： m_hObject](#m_hobject)|包含附加到此对象的 HBITMAP、HPALETTE、HRGN、HBRUSH、HPEN 或 HFONT 的句柄。|

## <a name="remarks"></a>备注

永远不会 `CGdiObject` 直接创建。 相反，您可以从其派生类之一（如或）创建对象 `CPen` `CBrush` 。

有关的详细信息 `CGdiObject` ，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cgdiobjectattach"></a><a name="attach"></a>CGdiObject：： Attach

将 Windows GDI 对象附加到 `CGdiObject` 对象。

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>参数

*hObject*<br/>
Windows GDI 对象的句柄（例如，HPEN 或 HBRUSH）。

### <a name="return-value"></a>返回值

如果附件成功，则为非零值;否则为0。

## <a name="cgdiobjectcgdiobject"></a><a name="cgdiobject"></a>CGdiObject::CGdiObject

构造 `CGdiObject` 对象。

```
CGdiObject();
```

### <a name="remarks"></a>备注

永远不会 `CGdiObject` 直接创建。 相反，您可以从其派生类之一（如或）创建对象 `CPen` `Cbrush` 。

## <a name="cgdiobjectcreatestockobject"></a><a name="createstockobject"></a>CGdiObject::CreateStockObject

检索预定义的 stock Windows GDI 笔、画笔或字体之一的句柄，并将 GDI 对象附加到 `CGdiObject` 对象。

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个常数，它指定所需的 stock 对象的类型。 有关适当的值的说明，请参阅 Windows SDK 中[GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject)的参数*fnObject* 。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

使用对应于 Windows GDI 对象类型的派生类之一（如用于股票笔尖）调用此函数 `CPen` 。

## <a name="cgdiobjectdeleteobject"></a><a name="deleteobject"></a>CGdiObject：:D eleteObject

通过释放与 Windows GDI 对象关联的所有系统存储，从内存中删除附加的 Windows GDI 对象。

```
BOOL DeleteObject();
```

### <a name="return-value"></a>返回值

如果已成功删除 GDI 对象，则为非零值;否则为0。

### <a name="remarks"></a>备注

与对象关联的存储 `CGdiObject` 不受此调用的影响。 应用程序不应调用 `DeleteObject` `CGdiObject` 当前选定到设备上下文中的对象。

删除模式画笔后，不会删除与该画笔关联的位图。 必须独立删除位图。

## <a name="cgdiobjectdeletetempmap"></a><a name="deletetempmap"></a>CGdiObject：:D eleteTempMap

由 `CWinApp` 空闲时间处理程序自动调用，将 `DeleteTempMap` 删除 `CGdiObject` 由创建的任何临时对象 `FromHandle` 。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>备注

`DeleteTempMap``CGdiObject`在删除对象之前，分离附加到临时对象的 WINDOWS GDI 对象 `CGdiObject` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

## <a name="cgdiobjectdetach"></a><a name="detach"></a>CGdiObject：:D etach

从对象中分离 Windows GDI 对象 `CGdiObject` ，并返回 WINDOWS gdi 对象的句柄。

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>返回值

已 `HANDLE` 分离的 WINDOWS GDI 对象的; 否则为 NULL。

## <a name="cgdiobjectfromhandle"></a><a name="fromhandle"></a>CGdiObject：： FromHandle

返回一个指向对象的指针，该指针指向 `CGdiObject` 给定 WINDOWS GDI 对象的句柄。

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>参数

*hObject*<br/>
Windows GDI 对象的句柄。

### <a name="return-value"></a>返回值

指向 `CGdiObject` 的指针，它可以是临时的或永久的。

### <a name="remarks"></a>备注

如果 `CGdiObject` 对象尚未附加到 WINDOWS GDI 对象， `CGdiObject` 则会创建并附加一个临时对象。

此临时 `CGdiObject` 对象只有在下一次应用程序的事件循环中有空闲时间时才有效，在这种情况下，将删除所有临时图形对象。 指出这一点的另一种方法是：只有在处理一条窗口消息的过程中，临时对象才有效。

## <a name="cgdiobjectgetobject"></a><a name="getobject"></a>CGdiObject：： GetObject

用定义指定对象的数据填充缓冲区。

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>参数

*nCount*<br/>
指定要复制到*lpObject*缓冲区的字节数。

*lpObject*<br/>
指向用户提供的用于接收信息的缓冲区。

### <a name="return-value"></a>返回值

检索到的字节数;如果发生错误，则为 0; 否则为0。

### <a name="remarks"></a>备注

函数检索其类型依赖于图形对象类型的数据结构，如以下列表所示：

|Object|缓冲区类型|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[图](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|不支持|

如果对象是一个 `CBitmap` 对象，则 `GetObject` 仅返回位图的宽度、高度和颜色格式信息。 可以使用[CBitmap：： GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)检索实际位。

如果对象是一个 `CPalette` 对象，则 `GetObject` 将检索指定调色板中的条目数的单词。 函数不会检索定义调色板的[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)结构。 应用程序可以通过调用[CPalette：： GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries)获取有关调色板项的信息。

## <a name="cgdiobjectgetobjecttype"></a><a name="getobjecttype"></a>CGdiObject::GetObjectType

检索 GDI 对象的类型。

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>返回值

如果成功，则为对象的类型;否则为0。 值可以是下列任一值：

- OBJ_BITMAP 位图

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

## <a name="cgdiobjectgetsafehandle"></a><a name="getsafehandle"></a>CGdiObject::GetSafeHandle

`m_hObject`如果 **`this`** 为 null，则返回，在这种情况下返回 null。

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>返回值

附加的 Windows GDI 对象的句柄;否则为 NULL。

### <a name="remarks"></a>备注

这是常规的句柄接口范例的一部分，当 NULL 是句柄的有效或特殊值时，此方法非常有用。

### <a name="example"></a>示例

  请参阅[CWnd：： IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled)的示例。

## <a name="cgdiobjectm_hobject"></a><a name="m_hobject"></a>CGdiObject：： m_hObject

包含附加到此对象的 HBITMAP、HRGN、HBRUSH、HPEN、HPALETTE 或 HFONT 的句柄。

```
HGDIOBJ m_hObject;
```

## <a name="cgdiobjectoperator-"></a><a name="operator_neq"></a>CGdiObject：： operator！ =

确定两个 GDI 对象是否逻辑上不相等。

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>参数

*obj*<br/>
指向现有的的指针 `CGdiObject` 。

### <a name="remarks"></a>备注

确定左侧的 GDI 对象是否不等于右侧的 GDI 对象。

## <a name="cgdiobjectoperator-"></a><a name="operator_eq_eq"></a>CGdiObject：： operator = =

确定两个 GDI 对象是否逻辑上相等。

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>参数

*obj*<br/>
对现有的的引用 `CGdiObject` 。

### <a name="remarks"></a>备注

确定左侧的 GDI 对象是否等于右侧的 GDI 对象。

## <a name="cgdiobjectoperator-hgdiobj"></a><a name="operator_hgdiobj"></a>CGdiObject：： operator HGDIOBJ

检索附加的 Windows GDI 对象的句柄;否则为 NULL。

```
operator HGDIOBJ() const;
```

## <a name="cgdiobjectunrealizeobject"></a><a name="unrealizeobject"></a>CGdiObject::UnrealizeObject

重置画笔的原点或重置逻辑调色板。

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

虽然 `UnrealizeObject` 是类的成员函数 `CGdiObject` ，但它只应在 `CBrush` 或对象上调用 `CPalette` 。

对于 `CBrush` 对象， `UnrealizeObject` 指示系统在下一次将给定画笔选择到设备上下文时，重置该画笔的原点。 如果对象是一个 `CPalette` 对象，则 `UnrealizeObject` 指示系统实现调色板，就好像它以前没有实现。 下次应用程序为指定调色板调用[CDC：： RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)函数时，系统会将逻辑调色板完全重新映射到系统调色板。

该 `UnrealizeObject` 函数不应与 stock 对象一起使用。 `UnrealizeObject`只要设置了新的画笔来源（通过[CDC：： SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg)函数），就必须调用函数。 `UnrealizeObject`对于当前选定的画笔或当前选择的任何显示上下文调色板，不能调用函数。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 类](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush 类](../../mfc/reference/cbrush-class.md)<br/>
[CFont 类](../../mfc/reference/cfont-class.md)<br/>
[CPalette 类](../../mfc/reference/cpalette-class.md)<br/>
[CPen 类](../../mfc/reference/cpen-class.md)<br/>
[CRgn 类](../../mfc/reference/crgn-class.md)
