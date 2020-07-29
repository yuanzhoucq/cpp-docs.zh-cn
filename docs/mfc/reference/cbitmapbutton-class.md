---
title: CBitmapButton 类
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
ms.openlocfilehash: 0cf4554f86f4a9275e4d96b3db519fde7fb05b22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231866"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton 类

创建使用位图图像而非文本进行标记的按钮控件。

## <a name="syntax"></a>语法

```
class CBitmapButton : public CButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CBitmapButton：： CBitmapButton](#cbitmapbutton)|构造 `CBitmapButton` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CBitmapButton：： AutoLoad](#autoload)|将对话框中的按钮与类的对象相关联 `CBitmapButton` ，按名称加载位图，并调整按钮的大小以适合位图。|
|[CBitmapButton：： LoadBitmaps](#loadbitmaps)|通过从应用程序的资源文件加载一个或多个命名的位图资源并将位图附加到对象来初始化对象。|
|[CBitmapButton：： System.windows.window.sizetocontent](#sizetocontent)|调整按钮大小以容纳位图。|

## <a name="remarks"></a>备注

`CBitmapButton`对象包含最多四个位图，其中包含一个按钮可以采用的不同状态的图像：向上（或向下）、向下（或选择）、重点和禁用。 只需要第一个位图;其他选项是可选的。

位图按钮图像包括图像周围的边框以及图像本身。 边框通常在显示按钮状态的过程中发挥作用。 例如，聚焦状态的位图通常类似于 "启动" 状态的位图，但带有边框填充的虚线矩形或边框上的粗实线。 禁用状态的位图通常类似于 "正常" 状态，但对比度较低（如灰显或灰色菜单选项）。

这些位图可为任意大小，但会将所有位图视为与 "启动" 状态的位图大小相同的值。

各种应用程序需要位图图像的不同组合：

|向上|向下|已设定焦点|已禁用|应用程序|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||没有 WS_TABSTOP 样式的按钮|
|×|×|×|×|具有所有状态的对话框按钮|
|×|×|×||具有 WS_TABSTOP 样式的对话框按钮|

创建位图按钮控件时，请设置 BS_OWNERDRAW 样式以指定该按钮是所有者描述的按钮。 这会导致 Windows 发送按钮的 WM_MEASUREITEM 和 WM_DRAWITEM 消息;框架将处理这些消息并管理按钮的外观。

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>在窗口的工作区中创建位图按钮控件

1. 为按钮创建一个到四个位图图像。

1. 构造[CBitmapButton](#cbitmapbutton)对象。

1. 调用[create](../../mfc/reference/cbutton-class.md#create)函数以创建 Windows 按钮控件并将其附加到 `CBitmapButton` 对象。

1. 调用[LoadBitmaps](#loadbitmaps)成员函数，以便在构造位图按钮后加载位图资源。

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>在对话框中包含位图按钮控件

1. 为按钮创建一个到四个位图图像。

1. 创建一个对话框模板，其中包含一个所有者描述的按钮，并将其放置在您希望使用位图按钮的位置。 模板中的按钮大小并不重要。

1. 将按钮的 "标题" 设置为 "MYIMAGE" 之类的值，并为按钮定义符号，如 IDC_MYIMAGE。

1. 在应用程序的资源脚本中，为按钮创建的每个映像提供一个 ID，该 ID 是通过将 "U"、"D"、"F" 或 "X" （对于向上、向下、重点和禁用）附加到用于步骤3中的按钮标题的字符串而构建的。 例如，对于 "MYIMAGE" 按钮标题，Id 为 "MYIMAGEU"、"MYIMAGED"、"MYIMAGEF" 和 "MYIMAGEX"。 **必须**在双引号中指定位图的 ID。 否则，资源编辑器会为资源分配一个整数，在加载该图像时 MFC 将会失败。

1. 在应用程序的对话框类（派生自 `CDialog` ）中添加 `CBitmapButton` 成员对象。

1. 在 `CDialog` 对象的[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)例程中，调用 `CBitmapButton` 对象的[AutoLoad](#autoload)函数，并将该按钮的控件 ID 和该 `CDialog` 对象的指针用作参数 **`this`** 。

如果要处理 Windows 通知消息（如 BN_CLICKED），由位图按钮控件发送给其父对象（通常是从派生的类 `CDialog` ），请将 `CDialog` 每条消息的消息映射项和消息处理程序成员函数添加到派生的对象。 对象发送的通知与 `CBitmapButton` [CButton](../../mfc/reference/cbutton-class.md)对象发送的通知相同。

类[CToolBar](../../mfc/reference/ctoolbar-class.md)采用不同的位图按钮方式。

有关的详细信息 `CBitmapButton` ，请参阅[控件](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>要求

**标头：** afxext。h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmapButton：： AutoLoad

将对话框中的按钮与类的对象相关联 `CBitmapButton` ，按名称加载位图，并调整按钮的大小以适合位图。

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>参数

*nID*<br/>
按钮的控件 ID。

*pParent*<br/>
指向拥有按钮的对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用 `AutoLoad` 函数将对话框中的所有者描述按钮初始化为位图按钮。 有关使用此函数的说明，请查看类的 "备注" `CBitmapButton` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>CBitmapButton：： CBitmapButton

创建一个 `CBitmapButton` 对象。

```
CBitmapButton();
```

### <a name="remarks"></a>备注

创建 c + + `CBitmapButton` 对象后，调用[CButton：： create](../../mfc/reference/cbutton-class.md#create)以创建 Windows 按钮控件并将其附加到 `CBitmapButton` 对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>CBitmapButton：： LoadBitmaps

如果要加载由其资源名称或 ID 号标识的位图图像，或者无法使用该函数时使用此函数，这是 `AutoLoad` 因为您创建的位图按钮不是对话框的一部分。

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

*lpszBitmapResource*<br/>
指向以 null 结尾的字符串，该字符串包含位图按钮正常或 "up" 状态的位图的名称。 必需。

*lpszBitmapResourceSel*<br/>
指向以 null 结尾的字符串，该字符串包含位图按钮的选定或 "关闭" 状态的位图的名称。 可以为 NULL。

*lpszBitmapResourceFocus*<br/>
指向以 null 结尾的字符串，该字符串包含位图按钮聚焦状态的位图的名称。 可以为 NULL。

*lpszBitmapResourceDisabled*<br/>
指向以 null 结尾的字符串，该字符串包含位图按钮的禁用状态的位图的名称。 可以为 NULL。

*nIDBitmapResource*<br/>
指定位图按钮正常或 "向上" 状态的位图资源的资源 ID 号。 必需。

*nIDBitmapResourceSel*<br/>
指定位图按钮的选定或 "关闭" 状态的位图资源的资源 ID 号。 可能为0。

*nIDBitmapResourceFocus*<br/>
为位图按钮的聚焦状态指定位图资源的资源 ID 号。 可能为0。

*nIDBitmapResourceDisabled*<br/>
为位图按钮的禁用状态指定位图资源的资源 ID 号。 可能为0。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmapButton：： System.windows.window.sizetocontent

调用此函数可将位图按钮调整为位图的大小。

```cpp
void SizeToContent();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
