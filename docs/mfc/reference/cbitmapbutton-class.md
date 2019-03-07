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
ms.openlocfilehash: c800b40fcf2bb3008b35614390e4aafcb43a54f5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296756"
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
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|构造 `CBitmapButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CBitmapButton::AutoLoad](#autoload)|在对话框中的按钮相关联的对象`CBitmapButton`类中，按名称加载 bitmap(s) 并调整其大小以适应位图按钮。|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|从应用程序的资源文件加载一个或多个命名的位图资源并附加到对象的位图初始化的对象。|
|[CBitmapButton::SizeToContent](#sizetocontent)|调整大小以适应位图按钮。|

## <a name="remarks"></a>备注

`CBitmapButton` 对象包含最多四个位图，其中包含一个按钮可以假定的不同状态的图像： 向上 （或普通），向下 （或所选），为主要目标，并禁用。 只有第一个位图是必需的;其他是可选的。

位图按钮映像包括为图像本身或图像周围的边框。 边框通常所起的作用中显示按钮的状态。 例如，已设定焦点状态的位图通常就像一个对于松开状态，但与从边框或边界的粗实线虚线的矩形嵌入。 位图为禁用状态通常类似于一个为松开状态，但具有较低对比度 （如为灰色或灰菜单选择）。

这些位图可以是任何大小，但全部都被看作就好像松开状态的位图的大小相同。

各种应用程序要求位图图像的不同的组合：

|向上|向下|已设定焦点|已禁用|应用程序|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||而无需 WS_TABSTOP 样式的按钮|
|×|×|×|×|与所有状态对话框按钮|
|×|×|×||WS_TABSTOP 样式对话框按钮|

创建时的位图按钮控件，设置要指定按钮为所有者描述的 BS_OWNERDRAW 样式。 这将导致 Windows 发送按钮; 的 WM_MEASUREITEM 和 WM_DRAWITEM 消息框架处理这些消息，并管理为你的按钮的外观。

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>在窗口的工作区中创建的位图按钮控件

1. 创建一至四个位图图像的按钮。

1. 构造[CBitmapButton](#cbitmapbutton)对象。

1. 调用[创建](../../mfc/reference/cbutton-class.md#create)函数来创建 Windows 按钮控件，并将其附加到`CBitmapButton`对象。

1. 调用[LoadBitmaps](#loadbitmaps)成员函数来构造的位图按钮之后加载的位图资源。

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>若要在对话框中包括的位图按钮控件

1. 创建一至四个位图图像的按钮。

1. 使用放置到所需位图按钮其中一个所有者描述按钮创建对话框模板。 在模板中的按钮的大小并不重要。

1. 将按钮的标题设置为一个值，例如"MYIMAGE"，并定义如 IDC_MYIMAGE 按钮的符号。

1. 在应用程序的资源脚本中，为每个构造通过追加一个字母"U，""D、"F，"ID 为按钮创建的映像或者"X"（对于向上、 向下具有焦点和禁用） 中的按钮标题的字符串到步骤 3。 对于按钮标题"MYIMAGE"中，例如，Id 将是"MYIMAGEU，""MYIMAGED，""MYIMAGEF，"和"MYIMAGEX。" 您**必须**指定双引号位图的 ID。 否则为资源编辑器将分配给资源的一个整数，并且加载图像时，MFC 将失败。

1. 在应用程序的对话框类 (派生自`CDialog`)，添加`CBitmapButton`成员对象。

1. 在中`CDialog`对象的[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)例程，调用`CBitmapButton`对象的[AutoLoad](#autoload)函数，请使用参数作为按钮的控件 ID 和`CDialog`对象**这**指针。

如果你想要处理 Windows 通知消息，例如 BN_CLICKED，由位图按钮控件发送到其父级 (从派生的类通常`CDialog`)，将添加到`CDialog`-派生的对象的消息映射条目和消息处理程序成员每个消息的的函数。 由发送的通知`CBitmapButton`对象是否与所发送的相同[CButton](../../mfc/reference/cbutton-class.md)对象。

该类[CToolBar](../../mfc/reference/ctoolbar-class.md)针对位图按钮采用不同的方法。

有关详细信息`CBitmapButton`，请参阅[控件](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="autoload"></a>  CBitmapButton::AutoLoad

在对话框中的按钮相关联的对象`CBitmapButton`类中，按名称加载 bitmap(s) 并调整其大小以适应位图按钮。

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>参数

*nID*<br/>
按钮的控件 id。

*pParent*<br/>
对拥有按钮对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`AutoLoad`函数以初始化为位图按钮的对话框中的所有者描述按钮。 使用此函数的说明中的备注`CBitmapButton`类。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

##  <a name="cbitmapbutton"></a>  CBitmapButton::CBitmapButton

创建一个 `CBitmapButton` 对象。

```
CBitmapButton();
```

### <a name="remarks"></a>备注

创建 c + + 后`CBitmapButton`对象，请调用[CButton::Create](../../mfc/reference/cbutton-class.md#create)若要创建的 Windows 按钮控件，并将其附加到`CBitmapButton`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

##  <a name="loadbitmaps"></a>  CBitmapButton::LoadBitmaps

如果你想要加载的资源名称或其 ID 号，或不能使用应用程序识别的位图图像使用此函数`AutoLoad`函数，因为，例如，要创建不属于对话框中的位图按钮。

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
指向包含如位图按钮的常规或"up"状态的位图名称的以 null 结尾的字符串。 必需。

*lpszBitmapResourceSel*<br/>
指向包含位图的名称，为选定的位图按钮的以 null 结尾的字符串或"关闭"状态。 可以为 NULL。

*lpszBitmapResourceFocus*<br/>
指向以 null 结尾的字符串包含位图的名称的位图按钮的已设定焦点状态。 可以为 NULL。

*lpszBitmapResourceDisabled*<br/>
指向包含位图按钮的禁用状态的位图名称的以 null 结尾的字符串。 可以为 NULL。

*nIDBitmapResource*<br/>
指定位图资源，如位图按钮的常规或"up"状态的资源 ID 号。 必需。

*nIDBitmapResourceSel*<br/>
为选定的位图按钮或"关闭"状态，请指定位图资源的资源 ID 号。 可能为 0。

*nIDBitmapResourceFocus*<br/>
指定位图按钮的已设定焦点状态的位图资源的资源 ID 号。 可能为 0。

*nIDBitmapResourceDisabled*<br/>
指定位图按钮的禁用状态的位图资源的资源 ID 号。 可能为 0。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

##  <a name="sizetocontent"></a>  CBitmapButton::SizeToContent

调用此函数可调整位图的大小为位图按钮。

```
void SizeToContent();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CTRLTEST](../../visual-cpp-samples.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
