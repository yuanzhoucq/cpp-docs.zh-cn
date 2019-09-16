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
ms.openlocfilehash: 61e8442c085a5be0a7266409daf973bf63f52a7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505503"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC 类

实现一个 Windows 图元文件，此文件包含一系列图形设备接口 (GDI) 命令，你可以重播此命令来创建所需图像或文本。

## <a name="syntax"></a>语法

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|构造 `CMetaFileDC` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMetaFileDC::Close](#close)|关闭设备上下文并创建图元文件句柄。|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|关闭增强型图元文件设备上下文，并创建一个增强型图元文件。|
|[CMetaFileDC::Create](#create)|创建 Windows 图元文件设备上下文，并将其`CMetaFileDC`附加到对象。|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|为增强型格式图元文件创建图元文件设备上下文。|

## <a name="remarks"></a>备注

若要实现 Windows 图元文件，请`CMetaFileDC`首先创建一个对象。 调用`CMetaFileDC`构造函数，然后调用 [Create](#create) 成员函数，该函数会创建一个 Windows 图元文件设备上下文，并将其附加到`CMetaFileDC`对象。

接下来， `CMetaFileDC`向该对象发送一个要用于重播的 CDC GDI 命令序列。 仅可使用那些创建输出的 GDI 命令， `MoveTo`如`LineTo`和。

将所需命令发送到图元文件后，调用`Close`成员函数，该函数将关闭图元文件设备上下文并返回一个图元文件句柄。 然后释放`CMetaFileDC`对象。

[CDC：:P laymetafile](../../mfc/reference/cdc-class.md#playmetafile)可以使用图元文件句柄重复播放图元文件。 还可以通过 Windows 函数（如[CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)）操作图元文件，这会将图元文件复制到磁盘。

如果不再需要该图元文件，请将其从内存中删除[DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows 函数。

您还可以实现`CMetaFileDC`对象，以便它可以处理两个输出调用和属性 GDI 调用（如）。 `GetTextExtent` 此类图元文件更灵活，并且可以更轻松地重复使用常规 GDI 代码，这通常由输出和属性调用的混合组成。 类从 CDC 继承两个设备`m_hDC`上下文`m_hAttribDC`和。 `CMetaFileDC` 设备上下文处理所有[cdc](../../mfc/reference/cdc-class.md) gdi `m_hAttribDC`输出调用，设备上下文处理所有 cdc gdi 属性调用。 `m_hDC` 通常，这两个设备上下文引用相同的设备。 对于`CMetaFileDC`，默认情况下，属性 DC 设置为 NULL。

创建指向屏幕、打印机或设备而不是图元文件的第二个设备上下文，然后调用`SetAttribDC`成员函数以将新的设备上下文与`m_hAttribDC`相关联。 此时，对信息的 GDI 调用将定向到新`m_hAttribDC`的。 输出 GDI 调用将转入`m_hDC`，后者表示图元文件。

有关的详细信息`CMetaFileDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>要求

**标头：** afxext。h

##  <a name="close"></a>  CMetaFileDC::Close

关闭图元文件设备上下文，并创建一个 Windows 图元文件句柄，该句柄可用于通过使用[CDC：:P laymetafile](../../mfc/reference/cdc-class.md#playmetafile)成员函数播放图元文件。

```
HMETAFILE Close();
```

### <a name="return-value"></a>返回值

如果函数成功，则为有效的 HMETAFILE;否则为 NULL。

### <a name="remarks"></a>备注

Windows 图元文件句柄还可用于通过 Windows 函数（如[CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)）操作图元文件。

通过调用 Windows [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile)函数，在使用后删除图元文件。

##  <a name="closeenhanced"></a>CMetaFileDC：： CloseEnhanced

关闭增强型图元文件设备上下文，并返回标识增强型图元文件的句柄。

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>返回值

增强型图元文件的句柄（如果成功）;否则为 NULL。

### <a name="remarks"></a>备注

应用程序可以使用此函数返回的增强型图元文件句柄来执行以下任务：

- 显示存储在增强型图元文件中的图片

- 创建增强型图元文件的副本

- 枚举、编辑或复制增强型图元文件中的单个记录

- 检索增强型图元文件头的图元文件内容的可选说明

- 检索增强型图元文件头的副本

- 检索增强型图元文件的二进制副本

- 枚举可选调色板中的颜色

- 将增强型格式图元文件转换为 Windows 格式图元文件

当应用程序不再需要增强型图元文件句柄时，应通过调用 Win32 `DeleteEnhMetaFile`函数来释放该句柄。

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

按两个步骤构造对象。`CMetaFileDC`

```
CMetaFileDC();
```

### <a name="remarks"></a>备注

首先，调用`CMetaFileDC`，然后调用`Create`，它会创建 Windows 图元文件设备上下文`CMetaFileDC`并将其附加到对象。

##  <a name="create"></a>  CMetaFileDC::Create

按两个步骤构造对象。`CMetaFileDC`

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>参数

*lpszFilename*<br/>
指向以 null 值结束的字符串。 指定要创建的图元文件的文件名。 如果*lpszFilename*为 NULL，则将创建一个新的内存中图元文件。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

首先，调用构造函数`CMetaFileDC`，然后调用`Create`，这将创建 Windows 图元文件设备上下文`CMetaFileDC`并将其附加到对象。

##  <a name="createenhanced"></a>CMetaFileDC：： CreateEnhanced

创建增强型图元文件的设备上下文。

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>参数

*pDCRef*<br/>
标识增强型图元文件的参考设备。

*lpszFileName*<br/>
指向以 null 值结束的字符串。 指定要创建的增强型图元文件的文件名。 如果此参数为 NULL，则增强型图元文件将基于内存，当对象被销毁或调用 Win32 `DeleteEnhMetaFile`函数时，它的内容将丢失。

*lpBounds*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)数据结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定要存储在增强型图元文件中的图片的 HIMETRIC 单位（以 .01-毫米增量表示）的尺寸。

*lpszDescription*<br/>
指向以零结尾的字符串，该字符串指定创建图片的应用程序的名称以及图片的标题。

### <a name="return-value"></a>返回值

增强型图元文件的设备上下文的句柄（如果成功）;否则为 NULL。

### <a name="remarks"></a>备注

此 DC 可用于存储与设备无关的图片。

Windows 使用由*pDCRef*参数标识的引用设备记录最初显示图片的设备的分辨率和单位。 如果*pDCRef*参数为 NULL，它将使用当前显示设备进行引用。

`RECT` *LpBounds*参数指向的数据结构的左侧成员和顶级成员必须分别小于右成员和下成员。 沿矩形边缘的点包括在图片中。 如果*lpBounds*为 NULL，图形设备接口（GDI）将计算可包含应用程序绘制的图片的最小矩形的尺寸。 应尽可能提供*lpBounds*参数。

*LpszDescription*参数指向的字符串在应用程序名称和图片名称之间必须包含 null 字符，并且必须以两个空字符终止，例如，"XYZ Graphics Editor\0Bald Eagle\0\0"，其中 \ 0 表示空字符。 如果*lpszDescription*为 NULL，则增强型图元文件头中没有对应的条目。

应用程序使用此函数创建的 DC 将图形图片存储在增强型图元文件中。 标识此 DC 的句柄可传递给任何 GDI 函数。

应用程序在增强型图元文件中存储图片后，可以通过调用`CDC::PlayMetaFile`函数在任何输出设备上显示该图片。 显示图片时，Windows 使用由*lpBounds*参数指向的矩形，并使用来自引用设备的解析数据来定位和缩放图片。 此函数返回的设备上下文包含与任何新 DC 关联的相同的默认属性。

应用程序必须使用 Win32 `GetWinMetaFileBits`函数将增强型图元文件转换为较旧的 Windows 图元文件格式。

增强型图元文件的文件名应使用。EMF 扩展。

## <a name="see-also"></a>请参阅

[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
