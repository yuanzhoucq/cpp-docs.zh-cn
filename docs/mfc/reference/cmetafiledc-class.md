---
title: CMetaFileDC 类
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 0919dacfd758df39064c5381690e9e23a029fcd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369946"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC 类

实现一个 Windows 图元文件，此文件包含一系列图形设备接口 (GDI) 命令，你可以重播此命令来创建所需图像或文本。

## <a name="syntax"></a>语法

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMetaFileDC：CMetaFileDC](#cmetafiledc)|构造 `CMetaFileDC` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMetaFileDC：关闭](#close)|关闭设备上下文并创建元文件句柄。|
|[CMetaFileDC：关闭增强](#closeenhanced)|关闭增强元文件设备上下文并创建增强元文件句柄。|
|[CMetaFileDC：创建](#create)|创建 Windows 元文件设备上下文并将其附加到`CMetaFileDC`对象。|
|[CMetaFileDC：创建增强](#createenhanced)|为增强格式的元文件创建元文件设备上下文。|

## <a name="remarks"></a>备注

要实现 Windows 元文件，请先`CMetaFileDC`创建一个对象。 调用`CMetaFileDC`构造函数，然后调用[Create](#create)成员函数，该函数创建 Windows 元文件设备上下文并将其附加到`CMetaFileDC`对象。

接下来，将`CMetaFileDC`对象发送您打算重播的 CDC GDI 命令的顺序。 只能使用创建输出的 GDI 命令，`MoveTo`如`LineTo`和 。

将所需命令发送到元文件后，调用`Close`成员函数，该函数将关闭元文件设备上下文并返回元文件句柄。 然后释放对象`CMetaFileDC`。

[然后，CDC：:PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)可以使用元文件句柄反复播放元文件。 元文件也可以由 Windows 函数（如[CopyMetaFile）](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)进行操作，这些函数将元文件复制到磁盘。

当不再需要元文件时，使用[DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows 功能将其从内存中删除。

您还可以实现该`CMetaFileDC`对象，以便它可以同时处理输出调用和属性 GDI 调用（如`GetTextExtent`）。 这种元文件更灵活，可以更轻松地重用常规 GDI 代码，该代码通常由输出和属性调用的组合组成。 类`CMetaFileDC`继承两个设备上下文，`m_hDC`并从`m_hAttribDC`CDC 继承 和 。 设备上下文处理所有[CDC](../../mfc/reference/cdc-class.md) GDI 输出调用`m_hAttribDC`，设备上下文处理所有 CDC GDI 属性调用。 `m_hDC` 通常，这两个设备上下文引用同一设备。 在 的情况下`CMetaFileDC`，默认情况下，属性 DC 设置为 NULL。

创建指向屏幕、打印机或元文件以外的设备的第二个设备上下文，然后调用`SetAttribDC`成员函数将新设备上下文与`m_hAttribDC`关联。 GDI要求的信息现在将定向到新的`m_hAttribDC`。 输出 GDI 调用将`m_hDC`转到 ，这表示元文件。

有关 的详细信息`CMetaFileDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="cmetafiledcclose"></a><a name="close"></a>CMetaFileDC：关闭

关闭元文件设备上下文并创建一个 Windows 元文件句柄，该句柄可用于使用[CDC：:PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)成员函数播放元文件。

```
HMETAFILE Close();
```

### <a name="return-value"></a>返回值

如果函数成功，则为有效的 HMETAFILE;否则 NULL。

### <a name="remarks"></a>备注

Windows 元文件句柄还可用于使用 Windows 函数（如[CopyMetaFile）](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)操作元文件。

使用后通过调用 Windows [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile)功能删除元文件。

## <a name="cmetafiledccloseenhanced"></a><a name="closeenhanced"></a>CMetaFileDC：关闭增强

关闭增强元文件设备上下文并返回标识增强格式元文件的句柄。

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>返回值

增强元文件的句柄（如果成功）;否则 NULL。

### <a name="remarks"></a>备注

应用程序可以使用此函数返回的增强元文件句柄执行以下任务：

- 显示存储在增强元文件中的图片

- 创建增强的元文件的副本

- 枚举、编辑或复制增强的元文件中的单个记录

- 从增强元文件标题检索元文件内容的可选说明

- 检索增强元文件标头的副本

- 检索增强的元文件的二进制副本

- 枚举可选调色板中的颜色

- 将增强格式的元文件转换为 Windows 格式的元文件

当应用程序不再需要增强的元文件句柄时，它应该通过调用 Win32`DeleteEnhMetaFile`函数来释放句柄。

## <a name="cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a>CMetaFileDC：CMetaFileDC

分两`CMetaFileDC`步构造对象。

```
CMetaFileDC();
```

### <a name="remarks"></a>备注

首先，调用`CMetaFileDC`，然后`Create`调用 ，这将创建 Windows 元文件设备上下文并将其附加到`CMetaFileDC`对象。

## <a name="cmetafiledccreate"></a><a name="create"></a>CMetaFileDC：创建

分两`CMetaFileDC`步构造对象。

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>参数

*lpszFile名称*<br/>
指向 null 终止的字符串。 指定要创建的元文件的文件名。 如果*lpszFile 名*为 NULL，则创建新的内存中元文件。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

首先调用构造函数`CMetaFileDC`，然后调用`Create`，这将创建 Windows 元文件设备上下文并将其附加到`CMetaFileDC`对象。

## <a name="cmetafiledccreateenhanced"></a><a name="createenhanced"></a>CMetaFileDC：创建增强

为增强格式的元文件创建设备上下文。

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>参数

*pDCRef*<br/>
标识增强的元文件的参考设备。

*lpszFile名称*<br/>
指向 null 终止的字符串。 指定要创建的增强元文件的文件名。 如果此参数为 NULL，则增强的元文件基于内存，当对象被销毁或调用 Win32`DeleteEnhMetaFile`函数时，其内容将丢失。

*lpBounds*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)数据结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，该对象以 HIMETRIC 单位（以 .01 毫米的增量）指定要存储在增强的元文件中的图片的尺寸。

*lpsz描述*<br/>
指向一个零端接字符串，该字符串指定创建图片的应用程序的名称以及图片的标题。

### <a name="return-value"></a>返回值

增强元文件的设备上下文的句柄（如果成功）;否则 NULL。

### <a name="remarks"></a>备注

此 DC 可用于存储与设备无关的图片。

Windows 使用*pDCRef*参数标识的参考设备来记录最初显示图片的设备的分辨率和单位。 如果*pDCRef*参数为 NULL，则使用当前显示设备进行参考。

`RECT` *lpBounds*参数指向的数据结构的左侧和顶部成员必须分别小于右侧和底部成员。 沿矩形边缘的点包含在图片中。 如果*lpBounds*为 NULL，则图形设备接口 （GDI） 计算最小矩形的尺寸，该矩形可以包含应用程序绘制的图片。 应尽可能提供*lpBounds*参数。

*lpsz描述*参数指向的字符串必须在应用程序名称和图片名称之间包含一个空字符，并且必须用两个空字符终止-例如，"XYZ 图形编辑器\0Bald Eagle_0_0"，其中 |0 表示空字符。 如果*lpsz 描述*为 NULL，则增强元文件标头中没有相应的条目。

应用程序使用此函数创建的 DC 将图形图片存储在增强的元文件中。 标识此 DC 的句柄可以传递给任何 GDI 函数。

应用程序将图片存储在增强的元文件中后，可以通过调用函数在任何`CDC::PlayMetaFile`输出设备上显示图片。 显示图片时，Windows 使用*lpBounds*参数指向的矩形和参考设备的分辨率数据来定位和缩放图片。 此函数返回的设备上下文包含与任何新 DC 关联的相同默认属性。

应用程序必须使用 Win32`GetWinMetaFileBits`函数将增强的元文件转换为较旧的 Windows 元文件格式。

增强的元文件的文件名应使用 。EMF 扩展。

## <a name="see-also"></a>另请参阅

[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
