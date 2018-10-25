---
title: CMetaFileDC 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
dev_langs:
- C++
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4b19358b97ca0afbe7a70347e5b05bed9916846
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076342"
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
|[CMetaFileDC::Close](#close)|关闭设备上下文，并创建图元文件句柄。|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|关闭增强型图元文件设备上下文，并创建增强型图元文件句柄。|
|[CMetaFileDC::Create](#create)|创建 Windows 图元文件设备上下文，并将其附加到`CMetaFileDC`对象。|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|创建增强格式图元文件的图元文件设备上下文。|

## <a name="remarks"></a>备注

若要实现 Windows 图元文件，请先创建`CMetaFileDC`对象。 调用`CMetaFileDC`构造函数，然后调用[创建](#create)成员函数，其创建的 Windows 图元文件设备上下文，并将其附加到`CMetaFileDC`对象。

接下来发送`CMetaFileDC`对象为其重播想 CDC GDI 命令序列。 创建输出，如这些 GDI 命令`MoveTo`和`LineTo`，可以使用。

已发送的图元文件的所需的命令后，调用`Close`成员函数，其关闭图元文件设备上下文，返回的图元文件句柄。 然后释放`CMetaFileDC`对象。

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)然后可以使用图元文件句柄重复播放图元文件。 图元文件还可以操作 Windows 函数如[CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea)，这将图元文件复制到磁盘。

当不再需要图元文件时，它从内存中删除具有[DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) Windows 函数。

您还可以实现`CMetaFileDC`对象，以便它可以处理，同时输出调用和属性如 GDI 调用`GetTextExtent`。 此类图元文件更灵活的详细信息可以轻松地重用常规的 GDI 代码，通常包含多个输出和属性调用。 `CMetaFileDC`类继承的两个设备上下文，`m_hDC`和`m_hAttribDC`，从 CDC。 `m_hDC`设备上下文将处理所有[CDC](../../mfc/reference/cdc-class.md) GDI 输出调用和`m_hAttribDC`设备上下文处理所有 CDC GDI 属性调用。 通常情况下，这些两个设备上下文引用同一个设备。 情况下`CMetaFileDC`，默认情况下将 DC 的属性设置为 NULL。

创建指向屏幕、 打印机或设备以外图元文件，然后调用的第二个设备上下文`SetAttribDC`成员函数将使用新的设备上下文相关联`m_hAttribDC`。 有关信息的 GDI 调用现在会定向到新`m_hAttribDC`。 输出 GDI 调用将转到`m_hDC`，它表示图元文件。

有关详细信息`CMetaFileDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="close"></a>  CMetaFileDC::Close

关闭图元文件设备上下文，并创建可用于通过使用播放图元文件的 Windows 图元文件句柄[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)成员函数。

```
HMETAFILE Close();
```

### <a name="return-value"></a>返回值

如果函数成功，则有效 HMETAFILE否则为，为 NULL。

### <a name="remarks"></a>备注

Windows 图元文件句柄也可用于处理 Windows 函数使用图元文件，如[CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea)。

在使用后删除图元文件，通过调用 Windows [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile)函数。

##  <a name="closeenhanced"></a>  CMetaFileDC::CloseEnhanced

关闭增强型图元文件设备上下文，并返回标识增强格式图元文件的句柄。

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>返回值

增强型图元文件，如果成功，则一个句柄否则为，为 NULL。

### <a name="remarks"></a>备注

应用程序可以使用此函数返回的增强型图元文件句柄执行以下任务：

- 显示存储在增强型图元文件中的图片

- 创建增强型图元文件的副本

- 枚举、 编辑或增强图元文件中的复制单个记录

- 增强型图元文件标头中检索的图元文件内容的可选描述

- 检索的增强型图元文件标头的副本

- 检索二进制增强型图元文件的副本

- 枚举中的可选调色板的颜色

- 增强格式图元文件转换为 Windows 格式图元文件

当应用程序不再需要的增强型图元文件句柄时，它应通过调用 Win32 释放句柄`DeleteEnhMetaFile`函数。

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

构造`CMetaFileDC`两个步骤中的对象。

```
CMetaFileDC();
```

### <a name="remarks"></a>备注

首先，调用`CMetaFileDC`，然后调用`Create`，它创建的 Windows 图元文件设备上下文，并将其附加到`CMetaFileDC`对象。

##  <a name="create"></a>  CMetaFileDC::Create

构造`CMetaFileDC`两个步骤中的对象。

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>参数

*lpszFilename*<br/>
指向以 null 结尾的字符串。 指定图元文件创建的文件名。 如果*lpszFilename*为 NULL，创建新的内存中图元文件。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

首先，调用构造函数`CMetaFileDC`，然后调用`Create`，它创建的 Windows 图元文件设备上下文，并将其附加到`CMetaFileDC`对象。

##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced

创建增强格式图元文件设备上下文。

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>参数

*pDCRef*<br/>
标识引用的增强型图元文件设备。

*lpszFileName*<br/>
指向以 null 结尾的字符串。 指定要创建增强型图元文件的文件名。 如果此参数为 NULL，增强型图元文件为丢失或时销毁该对象及其内容的基于内存的 Win32`DeleteEnhMetaFile`调用函数。

*lpBounds*<br/>
指向[RECT](../../mfc/reference/rect-structure1.md)数据结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)以 HIMETRIC 为单位 （以 0.1 毫米为增量） 的图片存储在增强型图元文件中指定的尺寸的对象。

*lpszDescription*<br/>
指向以零结尾的字符串，指定创建图中，以及图片的标题的应用程序的名称。

### <a name="return-value"></a>返回值

增强型图元文件，如果成功，则设备上下文的句柄否则为，为 NULL。

### <a name="remarks"></a>备注

此 DC 可以用于存储独立于设备的图片。

Windows 使用引用设备标识*pDCRef*参数解析和单位图片最初出现的设备记录。 如果*pDCRef*参数为 NULL，它使用当前的显示设备的引用。

左边和上边成员`RECT`指向数据结构*lpBounds*参数必须是小于右侧和底部成员分别。 矩形的边缘点包含在该图片。 如果*lpBounds*为 NULL，图形设备接口 (GDI) 计算可以包含由应用程序绘制图片的最小矩形的尺寸。 *LpBounds*应提供参数，在可能的情况。

指向的字符串*lpszDescription*参数必须包含 null 字符的应用程序名称和图片名称之间，并且必须使用两个空字符结束 — 例如，"XYZ 图形 Editor\0Bald Eagle\0\0，"其中 \0 表示 null 字符。 如果*lpszDescription*为 NULL，增强型图元文件标头中没有任何对应的条目。

应用程序使用此函数创建的 DC 将图形图片存储在增强型图元文件。 标识此 DC 的句柄可以传递给任何 GDI 函数。

应用程序将图片存储在增强型图元文件后，它可以显示图片任何输出设备上通过调用`CDC::PlayMetaFile`函数。 在显示图片，Windows 使用指向该矩形*lpBounds*参数和引用设备位置和缩放图片中解析的数据。 此函数返回的设备上下文包含相同的默认属性与任何新 DC 相关联。

应用程序必须使用 Win32`GetWinMetaFileBits`函数将转换为较旧的 Windows 图元文件格式的增强型图元文件。

应使用增强型图元文件的文件名。EMF 扩展。

## <a name="see-also"></a>请参阅

[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

