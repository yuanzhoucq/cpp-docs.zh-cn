---
title: CBitmap按钮类
ms.date: 11/04/2016
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
ms.openlocfilehash: df21591dec1da5861125d7e9480fb9345aaad061
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752946"
---
# <a name="cbitmapbutton-class"></a>CBitmap按钮类

创建使用位图图像而非文本进行标记的按钮控件。

## <a name="syntax"></a>语法

```
class CBitmapButton : public CButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 位地图按钮：：C 位地图按钮](#cbitmapbutton)|构造 `CBitmapButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CBitmap按钮：自动加载](#autoload)|对话框中的按钮与`CBitmapButton`类的对象关联，按名称加载位图，并调整按钮的大小以适合位图。|
|[C 位地图按钮：：加载位映射](#loadbitmaps)|通过从应用程序的资源文件加载一个或多个命名位图资源并将位图附加到对象来初始化对象。|
|[CBitmap按钮：：大小到内容](#sizetocontent)|调整按钮的大小以适应位图。|

## <a name="remarks"></a>备注

`CBitmapButton`对象最多包含四个位图，其中包含按钮可以假定的不同状态的图像：向上（或正常）、向下（或选中）、聚焦和禁用。 只需要第一个位图;其他是可选的。

位图按钮图像包括图像周围的边框以及图像本身。 边框通常在显示按钮的状态时发挥作用。 例如，焦点状态的位图通常类似于向上状态的位图，但从边框中设置虚线矩形或边框处的粗实线。 禁用状态的位图通常类似于向上状态的位图，但对比度较低（如灰色或灰色菜单选择）。

这些位图的大小可以是任意大小的，但所有位图都被视为与上状态的位图大小相同。

各种应用程序需要位图图像的不同组合：

|向上|向下|已设定焦点|已禁用|应用程序|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||无WS_TABSTOP样式的按钮|
|×|×|×|×|具有所有状态的对话框按钮|
|×|×|×||具有WS_TABSTOP样式的对话框按钮|

创建位图按钮控件时，请设置BS_OWNERDRAW样式以指定按钮是所有者绘制的。 这将导致 Windows 发送按钮的WM_MEASUREITEM和WM_DRAWITEM消息;因此，Windows 会为按钮发送WM_MEASUREITEM消息，然后WM_DRAWITEM消息。框架处理这些消息，并为您管理按钮的外观。

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>在窗口的工作区中创建位图按钮控件

1. 为按钮创建一到四个位图图像。

1. 构造[CBitmapButton](#cbitmapbutton)对象。

1. 调用["创建"](../../mfc/reference/cbutton-class.md#create)函数以创建 Windows 按钮控件并将其附加到`CBitmapButton`对象。

1. 调用[LoadBitmap](#loadbitmaps)成员函数，在构造位图按钮后加载位图资源。

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>在对话框中包含位图按钮控件

1. 为按钮创建一到四个位图图像。

1. 创建一个对话框模板，其中包含所有者绘制按钮，该按钮位于所需的位图按钮的位置。 模板中按钮的大小并不重要。

1. 将按钮的标题设置为"MYIMAGE"等值，并为按钮定义符号，如IDC_MYIMAGE。

1. 在应用程序的资源脚本中，为为按钮创建的每个图像提供一个 ID，该 ID 通过将其中一个字母"U"、"D"、"F"或"X"（用于向上、向下、焦点和禁用）添加到步骤 3 中用于按钮标题的字符串中。 例如，对于按钮标题"MYIMAGE"，ID 将是"MYIMAGEU"、"MYIMAGED"、"MYIMAGEF"和"MYIMAGEX"。 **您必须**在双引号中指定位图的 ID。 否则，资源编辑器将为资源分配整数，并且 MFC 在加载映像时将失败。

1. 在应用程序的对话框类中（派生自`CDialog`），添加`CBitmapButton`成员对象。

1. `CDialog`在对象的[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)例程中，`CBitmapButton`调用对象的[自动加载](#autoload)函数，将按钮的控制 ID 和`CDialog`对象的**此**指针用作参数。

如果要处理由位图按钮控件发送到其父级（通常是派生自`CDialog`的类）发送到其父级（通常从 派生`CDialog`对象的 Windows 通知消息，如BN_CLICKED。 `CBitmapButton`对象发送的通知与[CButton](../../mfc/reference/cbutton-class.md)对象发送的通知相同。

类[CToolBar](../../mfc/reference/ctoolbar-class.md)对位图按钮采取了不同的方法。

有关 的详细信息`CBitmapButton`，请参阅[控件](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmap按钮：自动加载

对话框中的按钮与`CBitmapButton`类的对象关联，按名称加载位图，并调整按钮的大小以适合位图。

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>参数

*nID*<br/>
按钮的控制 ID。

*p 父级*<br/>
指向拥有按钮的对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`AutoLoad`函数将对话框中的所有者绘制按钮初始化为位图按钮。 有关使用此函数的说明在类的备注中`CBitmapButton`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>C 位地图按钮：：C 位地图按钮

创建一个 `CBitmapButton` 对象。

```
CBitmapButton();
```

### <a name="remarks"></a>备注

创建C++`CBitmapButton`对象后，调用[CButton：：创建](../../mfc/reference/cbutton-class.md#create)以创建 Windows 按钮控件并将其附加到`CBitmapButton`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>C 位地图按钮：：加载位映射

如果要加载由其资源名称或 ID 号标识的位贴图图像，或者由于创建不是对话框一部分的`AutoLoad`位图按钮而无法使用该函数时，请使用此功能。

```
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,
    LPCTSTR lpszBitmapResourceSel = NULL,
    LPCTSTR lpszBitmapResourceFocus = NULL,
    LPCTSTR lpszBitmapResourceDisabled = NULL);

BOOL LoadBitmaps(
    UINT nIDBitmapResource,
    UINT nIDBitmapResourceSel = 0,
    UINT nIDBitmapResourceFocus = 0,
    UINT nIDBitmapResourceDisabled = 0);
```

### <a name="parameters"></a>参数

*lpszBitmap资源*<br/>
指向包含位图按钮正常或"向上"状态的位图名称的 null 端接字符串。 必需。

*lpszBitmap 资源塞尔*<br/>
指向包含位图按钮所选或"向下"状态的位图名称的 null 端接字符串。 可以为 NULL。

*lpszBitmap 资源焦点*<br/>
指向包含位图按钮焦点状态的位图名称的 null 端接字符串。 可以为 NULL。

*lpszBitmap 资源已禁用*<br/>
指向包含位图按钮禁用状态的位图名称的 null 终止字符串。 可以为 NULL。

*nIDBitmap资源*<br/>
指定位图按钮的正常或"向上"状态的位图资源的资源 ID 号。 必需。

*nIDBitmap 资源塞尔*<br/>
指定位图按钮的选定或"向下"状态的位图资源的资源 ID 号。 可能为 0。

*nIDBitmap 资源焦点*<br/>
指定位图按钮的聚焦状态位图资源的资源 ID 号。 可能为 0。

*nIDBitmap 资源已禁用*<br/>
指定位图按钮禁用状态的位图资源的资源 ID 号。 可能为 0。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmap按钮：：大小到内容

调用此函数以将位图按钮的大小调整到位图的大小。

```cpp
void SizeToContent();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[C按钮类](../../mfc/reference/cbutton-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
