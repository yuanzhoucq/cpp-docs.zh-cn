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
ms.openlocfilehash: 0cd7a0e0ed500ee9394b00e8906640e9f950163b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373737"
---
# <a name="cgdiobject-class"></a>CGdiObject 类

为各种 Windows 图形设备接口 (GDI) 对象（如位图、区域、画笔、笔、调色板和字体）提供基类。

## <a name="syntax"></a>语法

```
class CGdiObject : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CGdiObject：CGdiObject](#cgdiobject)|构造 `CGdiObject` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CGdiObject：：附加](#attach)|将 Windows GDI 对象`CGdiObject`附加到对象。|
|[CGdiObject：：创建股票对象](#createstockobject)|检索对其中一个 Windows 预定义的库存笔、画笔或字体的句柄。|
|[CGdiObject：:DeleteObject](#deleteobject)|通过释放与该对象关联的所有系统存储，`CGdiObject`从内存中删除附加到该对象的 Windows GDI 对象。|
|[CGdiObject：:DeleteTempMap](#deletetempmap)|删除 由`FromHandle``CGdiObject`创建的任何临时对象。|
|[CGdiObject：:D埃塔奇](#detach)|从`CGdiObject`对象分离 Windows GDI 对象，并将句柄返回到 Windows GDI 对象。|
|[CGdiObject：：从手柄](#fromhandle)|返回指向给定 Windows `CGdiObject` GDI 对象的句柄的对象的指针。|
|[CGdiObject：获取对象](#getobject)|使用描述附加到`CGdiObject`对象的 Windows GDI 对象的数据填充缓冲区。|
|[CGdiObject：获取对象类型](#getobjecttype)|检索 GDI 对象的类型。|
|[CGdiObject：获取安全处理](#getsafehandle)|返回`m_hObject`**，除非这是**NULL，在这种情况下返回 NULL。|
|[CGdiObject：未实现对象](#unrealizeobject)|重置画笔的原点或重置逻辑调色板。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CGdiObject：：操作员！*](#operator_neq)|确定两个 GDI 对象在逻辑上是否不相等。|
|[CGdiObject：：运算符 |](#operator_eq_eq)|确定两个 GDI 对象在逻辑上是否相等。|
|[CGdiObject：：操作员HGDIOBJ](#operator_hgdiobj)|检索附加的 Windows GDI 对象的 HANDLE。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CGdiObject：m_hObject](#m_hobject)|包含附加到此对象的 HBITMAP、HPALETTE、HRGN、HBRUSH、HPEN 或 HFONT 的手柄。|

## <a name="remarks"></a>备注

您从不直接创建`CGdiObject`。 相反，您从其派生类之一（如`CPen`或`CBrush`）创建对象。

有关 的详细信息`CGdiObject`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cgdiobjectattach"></a><a name="attach"></a>CGdiObject：：附加

将 Windows GDI 对象`CGdiObject`附加到对象。

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>参数

*hObject*<br/>
Windows GDI 对象的句柄（例如，HPEN 或 HBRUSH）。

### <a name="return-value"></a>返回值

如果附件成功，则非零;否则 0。

## <a name="cgdiobjectcgdiobject"></a><a name="cgdiobject"></a>CGdiObject：CGdiObject

构造 `CGdiObject` 对象。

```
CGdiObject();
```

### <a name="remarks"></a>备注

您从不直接创建`CGdiObject`。 相反，您从其派生类之一（如`CPen`或`Cbrush`）创建对象。

## <a name="cgdiobjectcreatestockobject"></a><a name="createstockobject"></a>CGdiObject：：创建股票对象

检索对预定义的库存 Windows GDI 笔、画笔或字体之一的句柄，并将 GDI 对象附加到`CGdiObject`对象。

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定所需库存对象的类型的常量。 有关适当值的说明，请参阅 Windows SDK 中[GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject)的参数*fnObject。*

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

使用与 Windows GDI 对象类型对应的派生类之一调用此函数，例如`CPen`对于股票笔。

## <a name="cgdiobjectdeleteobject"></a><a name="deleteobject"></a>CGdiObject：:DeleteObject

通过释放与 Windows GDI 对象关联的所有系统存储，从内存中删除附加的 Windows GDI 对象。

```
BOOL DeleteObject();
```

### <a name="return-value"></a>返回值

如果成功删除 GDI 对象，则非零;否则 0。

### <a name="remarks"></a>备注

与`CGdiObject`对象关联的存储不受此调用的影响。 应用程序不应调用`DeleteObject`当前选择到设备`CGdiObject`上下文中的对象。

删除模式画笔时，不会删除与画笔关联的位图。 必须独立删除位图。

## <a name="cgdiobjectdeletetempmap"></a><a name="deletetempmap"></a>CGdiObject：:DeleteTempMap

由`CWinApp`空闲时间处理程序自动调用，`DeleteTempMap`删除 由 创建`CGdiObject``FromHandle`的任何临时对象。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>备注

`DeleteTempMap`在删除`CGdiObject``CGdiObject`对象之前，分离附加到临时对象的 Windows GDI 对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

## <a name="cgdiobjectdetach"></a><a name="detach"></a>CGdiObject：:D埃塔奇

从`CGdiObject`对象分离 Windows GDI 对象，并将句柄返回到 Windows GDI 对象。

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>返回值

A`HANDLE`到 Windows GDI 对象分离;否则 NULL，如果没有附加 GDI 对象。

## <a name="cgdiobjectfromhandle"></a><a name="fromhandle"></a>CGdiObject：：从手柄

返回指向给定 Windows `CGdiObject` GDI 对象的句柄的对象的指针。

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>参数

*hObject*<br/>
Windows GDI 对象的句柄。

### <a name="return-value"></a>返回值

指向`CGdiObject`的指针可能是临时的或永久性的。

### <a name="remarks"></a>备注

如果`CGdiObject`对象尚未附加到 Windows GDI 对象，则创建并附加`CGdiObject`临时对象。

此临时`CGdiObject`对象仅在下次应用程序在其事件循环中有空闲时间之前有效，此时将删除所有临时图形对象。 另一种说法是临时对象仅在处理一个窗口消息期间有效。

## <a name="cgdiobjectgetobject"></a><a name="getobject"></a>CGdiObject：获取对象

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
指向用户提供的缓冲区，该缓冲区用于接收信息。

### <a name="return-value"></a>返回值

检索的字节数;否则 0 如果发生错误。

### <a name="remarks"></a>备注

函数检索其类型取决于图形对象类型的数据结构，如下列表所示：

|对象|缓冲区类型|
|------------|-----------------|
|`CPen`|[洛彭](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[日志笔刷](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[日志](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[位图](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|不支持|

如果对象是`CBitmap`对象，`GetObject`则仅返回位图的宽度、高度和颜色格式信息。 可以使用[CBitmap：：getBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)检索实际位。

如果对象是`CPalette`对象，`GetObject`则检索指定调色板中条目数的 WORD。 函数不检索定义调色板的[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)结构。 应用程序可以通过调用[CPalette：：getPalette 条目](../../mfc/reference/cpalette-class.md#getpaletteentries)来获取有关调色板条目的信息。

## <a name="cgdiobjectgetobjecttype"></a><a name="getobjecttype"></a>CGdiObject：获取对象类型

检索 GDI 对象的类型。

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>返回值

对象的类型（如果成功）;否则 0。 值可以是下列任一值：

- OBJ_BITMAP 位图

- OBJ_BRUSH画笔

- OBJ_FONT字体

- OBJ_PAL调色板

- OBJ_PEN笔

- OBJ_EXTPEN扩展笔

- OBJ_REGION地区

- OBJ_DC设备上下文

- OBJ_MEMDC内存设备上下文

- OBJ_METAFILE元文件

- OBJ_METADC元文件设备上下文

- OBJ_ENHMETAFILE增强的元文件

- OBJ_ENHMETADC增强元文件设备上下文

## <a name="cgdiobjectgetsafehandle"></a><a name="getsafehandle"></a>CGdiObject：获取安全处理

返回`m_hObject`**，除非这是**NULL，在这种情况下返回 NULL。

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>返回值

附加 Windows GDI 对象的句柄;否则 NULL，如果没有附加任何对象。

### <a name="remarks"></a>备注

这是常规句柄接口范例的一部分，当 NULL 是句柄的有效值或特殊值时，这非常有用。

### <a name="example"></a>示例

  请参阅[CWnd 的示例：：正在启用窗口](../../mfc/reference/cwnd-class.md#iswindowenabled)。

## <a name="cgdiobjectm_hobject"></a><a name="m_hobject"></a>CGdiObject：m_hObject

包含附加到此对象的 HBITMAP、HRGN、HBRUSH、HPEN、HPALETTE 或 HFONT 的手柄。

```
HGDIOBJ m_hObject;
```

## <a name="cgdiobjectoperator-"></a><a name="operator_neq"></a>CGdiObject：：操作员！*

确定两个 GDI 对象在逻辑上是否不相等。

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>参数

obj**<br/>
指向现有`CGdiObject`的 指针。

### <a name="remarks"></a>备注

确定左侧的 GDI 对象是否不等于右侧的 GDI 对象。

## <a name="cgdiobjectoperator-"></a><a name="operator_eq_eq"></a>CGdiObject：：运算符 |

确定两个 GDI 对象在逻辑上是否相等。

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>参数

obj**<br/>
对现有 的 引用`CGdiObject`。

### <a name="remarks"></a>备注

确定左侧的 GDI 对象是否等于右侧的 GDI 对象。

## <a name="cgdiobjectoperator-hgdiobj"></a><a name="operator_hgdiobj"></a>CGdiObject：：操作员HGDIOBJ

检索附加 Windows GDI 对象的 HANDLE;否则 NULL，如果没有附加任何对象。

```
operator HGDIOBJ() const;
```

## <a name="cgdiobjectunrealizeobject"></a><a name="unrealizeobject"></a>CGdiObject：未实现对象

重置画笔的原点或重置逻辑调色板。

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

虽然`UnrealizeObject`是`CGdiObject`类的成员函数，但应仅调用 或`CBrush``CPalette`对象。

对于`CBrush`对象，`UnrealizeObject`指示系统在下次选择给定画笔到设备上下文中时重置其原点。 如果对象是`CPalette`对象，则`UnrealizeObject`指示系统实现调色板，就好像它以前尚未实现一样。 下次应用程序调用指定调色板的[CDC：：实现调色板](../../mfc/reference/cdc-class.md#realizepalette)功能时，系统将逻辑调色板完全重新映射到系统调色板。

该`UnrealizeObject`函数不应与库存对象一起使用。 每当`UnrealizeObject`设置新的画笔源时（通过[CDC：：SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg)函数），都必须调用该函数。 不得`UnrealizeObject`为当前选定的画笔或任何显示上下文的当前选定调色板调用该函数。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 类](../../mfc/reference/cbitmap-class.md)<br/>
[画笔类](../../mfc/reference/cbrush-class.md)<br/>
[CFont 类](../../mfc/reference/cfont-class.md)<br/>
[CPalette 类](../../mfc/reference/cpalette-class.md)<br/>
[CPen 类](../../mfc/reference/cpen-class.md)<br/>
[CRgn 类](../../mfc/reference/crgn-class.md)
