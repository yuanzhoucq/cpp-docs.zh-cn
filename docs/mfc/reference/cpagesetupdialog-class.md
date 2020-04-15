---
title: CPageSetupDialog 类
ms.date: 11/04/2016
f1_keywords:
- CPageSetupDialog
- AFXDLGS/CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CreatePrinterDC
- AFXDLGS/CPageSetupDialog::DoModal
- AFXDLGS/CPageSetupDialog::GetDeviceName
- AFXDLGS/CPageSetupDialog::GetDevMode
- AFXDLGS/CPageSetupDialog::GetDriverName
- AFXDLGS/CPageSetupDialog::GetMargins
- AFXDLGS/CPageSetupDialog::GetPaperSize
- AFXDLGS/CPageSetupDialog::GetPortName
- AFXDLGS/CPageSetupDialog::OnDrawPage
- AFXDLGS/CPageSetupDialog::PreDrawPage
- AFXDLGS/CPageSetupDialog::m_psd
helpviewer_keywords:
- CPageSetupDialog [MFC], CPageSetupDialog
- CPageSetupDialog [MFC], CreatePrinterDC
- CPageSetupDialog [MFC], DoModal
- CPageSetupDialog [MFC], GetDeviceName
- CPageSetupDialog [MFC], GetDevMode
- CPageSetupDialog [MFC], GetDriverName
- CPageSetupDialog [MFC], GetMargins
- CPageSetupDialog [MFC], GetPaperSize
- CPageSetupDialog [MFC], GetPortName
- CPageSetupDialog [MFC], OnDrawPage
- CPageSetupDialog [MFC], PreDrawPage
- CPageSetupDialog [MFC], m_psd
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
ms.openlocfilehash: 218ed24ccf56854622e20936299fcc2e8a3d0fa9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374788"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog 类

封装由 Windows 公共 OLE“页面设置”对话框提供的服务以及对于设置和修改打印边距的额外支持。

## <a name="syntax"></a>语法

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPagesetup对话：：CPage安装程序对话](#cpagesetupdialog)|构造 `CPageSetupDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPageSetup：：创建打印机DC](#createprinterdc)|创建用于打印的设备上下文。|
|[CPagesetup对话：:Do模态](#domodal)|显示对话框，并允许用户进行选择。|
|[CPagesetup对话：获取设备名称](#getdevicename)|返回打印机的设备名称。|
|[CPagesetup对话：：获取开发模式](#getdevmode)|返回打印机的当前 DEVMODE。|
|[CPagesetup对话：：获取驱动程序名称](#getdrivername)|返回打印机使用的驱动程序。|
|[CPagesetup对话：获取边缘](#getmargins)|返回打印机的当前边距设置。|
|[CPagesetup对话：：获取纸张大小](#getpapersize)|返回打印机的纸张大小。|
|[CPagesetup对话：：获取端口名称](#getportname)|返回输出端口名称。|
|[CPagesetup对话：：在画页](#ondrawpage)|由框架调用以呈现打印页的屏幕图像。|
|[CPagesetup对话：:P重新绘制页面](#predrawpage)|在渲染打印页的屏幕图像之前，由框架调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CPagesetup对话：：m_psd](#m_psd)|用于自定义对象的结构`CPageSetupDialog`。|

## <a name="remarks"></a>备注

此类旨在取代"打印设置"对话框。

要使用`CPageSetupDialog`对象，请首先使用`CPageSetupDialog`构造函数创建对象。 构造对话框后，可以设置或修改`m_psd`数据成员中的任何值，以初始化对话框控件的值。 [m_psd](#m_psd)结构为PAGESETUPDLG型。

初始化对话框控件后，调用`DoModal`成员函数以显示对话框，并允许用户选择打印选项。 `DoModal`返回用户是否选择了"确定 （IDOK）"还是"取消"（IDCANCEL）按钮。

如果`DoModal`返回 IDOK，则可以使用多个`CPageSetupDialog`成员函数或访问`m_psd`数据成员来检索用户输入的信息。

> [!NOTE]
> 取消通用 OLE 页面设置对话框后，框架将不会保存用户所做的任何更改。 由应用程序本身将此对话框中的任何值保存到永久位置，例如应用程序的文档或应用程序类的成员。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>要求

**标题：** afxdlgs.h

## <a name="cpagesetupdialogcpagesetupdialog"></a><a name="cpagesetupdialog"></a>CPagesetup对话：：CPage安装程序对话

调用此函数以构造对象`CPageSetupDialog`。

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

dwFlags**<br/>
可用于自定义对话框设置的一个或多个标志。 可以使用位-OR 运算符组合这些值。 这些值将具有以下含义：

- PSD_DEFAULTMINMARGINS 将页边距的最小允许宽度设置为与打印机最小值相同的最小宽度。 如果还指定了PSD_MARGINS和PSD_MINMARGINS标志，则忽略此标志。

- PSD_INWININIINTLMEASURE未实现。

- PSD_MINMARGINS 使系统使用`rtMinMargin`成员中指定的值作为左侧、顶部、右侧和底部边距的最小允许宽度。 系统可防止用户输入小于指定最小值的宽度。 如果未指定PSD_MINMARGINS，系统将允许的最小宽度设置为打印机允许的最小宽度。

- PSD_MARGINS激活边距控制区域。

- PSD_INTHOUSANDTHSOFINCHES 使对话框的单位以 1/1000 英寸为单位进行测量。

- PSD_INHUNDREDTHSOFMILLIMETERS 使对话框的单位以 1/100 毫米为单位进行测量。

- PSD_DISABLEMARGINS禁用边距对话框控件。

- PSD_DISABLEPRINTER禁用打印机按钮。

- PSD_NOWARNING 防止在没有默认打印机时显示警告消息。

- PSD_DISABLEORIENTATION 禁用页面方向对话框控件。

- PSD_RETURNDEFAULT`CPageSetupDialog`导致返回为系统默认打印机初始化的[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构而不显示对话框。 假定两者`hDevNames``hDevMode`均为 NULL;否则，函数将返回一个错误。 如果旧打印机驱动程序支持系统默认打印机（早于 Windows 版本 3.0），则仅返回`hDevNames`系统默认打印机;如果旧打印机驱动程序支持系统默认打印机（早于 Windows 版本 3.0），则仅返回系统默认打印机。`hDevMode`为 NULL。

- PSD_DISABLEPAPER禁用纸张选择控件。

- PSD_SHOWHELP 使对话框显示"帮助"按钮。 如果`hwndOwner`指定了此标志，则成员不能为 NULL。

- PSD_ENABLEPAGESETUPHOOK 启用 中`lpfnSetupHook`指定的挂钩函数。

- PSD_ENABLEPAGESETUPTEMPLATE 使操作系统使用 和`hInstance``lpSetupTemplateName`标识的对话框模板框创建对话框。

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE 指示`hInstance`标识包含预加载对话框模板的数据块。 如果指定了此`lpSetupTemplateName`标志，系统将忽略。

- PSD_ENABLEPAGEPAINTHOOK 启用 中`lpfnPagePaintHook`指定的挂钩函数。

- PSD_DISABLEPAGEPAINTING禁用对话框的绘制区域。

*pparentwnd*<br/>
指向对话框的父或所有者的指针。

### <a name="remarks"></a>备注

使用["DoModal"](../../mfc/reference/cdialog-class.md#domodal)功能显示对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

## <a name="cpagesetupdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPageSetup：：创建打印机DC

从[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构创建打印机设备上下文。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>返回值

处理新创建的打印机设备上下文 （DC）。

## <a name="cpagesetupdialogdomodal"></a><a name="domodal"></a>CPagesetup对话：:Do模态

调用此函数以显示 Windows 通用 OLE 页面设置对话框，并允许用户选择各种打印设置选项，如打印边距、纸张的大小和方向以及目标打印机。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL，请调用 Windows [CommDlg 扩展错误](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能以确定是否发生了错误。

IDOK 和 IDCANCEL 是指示用户选择"确定"还是"取消"按钮的常量。

### <a name="remarks"></a>备注

此外，用户可以访问打印机设置选项，如网络位置和特定于所选打印机的属性。

如果要通过设置`m_psd`结构成员来初始化各种页面设置对话框选项，则应在调用`DoModal`之前和构造对话框对象之后执行此操作。 调用`DoModal`后 调用 其他成员函数以检索用户输入到对话框中的设置或信息。

如果要传播用户输入的当前设置，请调用[CWinApp：：选择打印机](../../mfc/reference/cwinapp-class.md#selectprinter)。 此函数从`CPageSetupDialog`对象获取信息并初始化，并选择具有正确属性的新打印机 DC。

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>示例

  请参阅[CPageSetup对话框的示例：cPagesetupDialog](#cpagesetupdialog)。

## <a name="cpagesetupdialoggetdevicename"></a><a name="getdevicename"></a>CPagesetup对话：获取设备名称

在此之后`DoModal`调用此功能以检索当前所选打印机的名称。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>返回值

`CPageSetupDialog`对象使用的设备名称。

## <a name="cpagesetupdialoggetdevmode"></a><a name="getdevmode"></a>CPagesetup对话：：获取开发模式

调用后调用`DoModal`此功能以检索有关`CPageSetupDialog`对象的打印机设备上下文的信息。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>返回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)数据结构，其中包含有关打印驱动程序的设备初始化和环境的信息。 您必须使用 Windows[全局解锁](/windows/win32/api/winbase/nf-winbase-globalunlock)功能解锁此结构占用的内存，该功能在 Windows SDK 中进行了描述。

## <a name="cpagesetupdialoggetdrivername"></a><a name="getdrivername"></a>CPagesetup对话：：获取驱动程序名称

调用[DoModal](../../mfc/reference/cprintdialog-class.md#domodal)后调用此功能以检索系统定义的打印机设备驱动程序的名称。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>返回值

指定`CString`系统定义的驱动程序名称。

### <a name="remarks"></a>备注

`CString`使用指向 返回`GetDriverName`的对象的指针作为 调用`lpszDriverName`[CDC：：：createDC](../../mfc/reference/cdc-class.md#createdc)中的值。

## <a name="cpagesetupdialoggetmargins"></a><a name="getmargins"></a>CPagesetup对话：获取边缘

调用后调用此功能以`DoModal`检索打印机设备驱动程序的边距。

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>参数

*lprect 边缘*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，该对象描述当前所选打印机的打印边距（以 1/1000 英寸或 1/100 mm 为单位）。 如果对此矩形不感兴趣，则通过 NULL。

*lpRectMin 边缘*<br/>
指向结构或`RECT`对象，`CRect`该结构或对象描述当前所选打印机的最小打印边距（1/1000 英寸或 1/100 mm）。 如果对此矩形不感兴趣，则通过 NULL。

## <a name="cpagesetupdialoggetpapersize"></a><a name="getpapersize"></a>CPagesetup对话：：获取纸张大小

调用此函数以检索选择要打印的纸张的大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>返回值

选择用于打印的包含纸张大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)对象（以 1/1000 英寸或 1/100 毫米为单位）。

## <a name="cpagesetupdialoggetportname"></a><a name="getportname"></a>CPagesetup对话：：获取端口名称

调用后调用`DoModal`此功能以检索当前选定的打印机端口的名称。

```
CString GetPortName() const;
```

### <a name="return-value"></a>返回值

当前选定的打印机端口的名称。

## <a name="cpagesetupdialogm_psd"></a><a name="m_psd"></a>CPagesetup对话：：m_psd

PAGESETUPDLG 类型的结构，其成员存储对话框对象的特征。

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>备注

构造`CPageSetupDialog`对象后，可以使用`m_psd`在调用`DoModal`成员函数之前设置对话框的各个方面。

如果直接修改`m_psd`数据成员，将覆盖任何默认行为。

有关[PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)结构的详细信息，请参阅 Windows SDK。

请参阅[CPageSetup对话框的示例：cPagesetupDialog](#cpagesetupdialog)。

## <a name="cpagesetupdialogondrawpage"></a><a name="ondrawpage"></a>CPagesetup对话：：在画页

由框架调用以绘制打印页的屏幕图像。

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文的指针。

*n消息*<br/>
指定一条消息，指示当前正在绘制的页面的区域。 可以是以下值之一：

- WM_PSD_FULLPAGERECT整个页面区域。

- WM_PSD_MINMARGINRECT 当前最小边距。

- WM_PSD_MARGINRECT 当前边距。

- WM_PSD_GREEKTEXTRECT页面的内容。

- WM_PSD_ENVSTAMPRECT为邮票表示而保留的区域。

- WM_PSD_YAFULLPAGERECT 返回地址表示的区域。 此区域延伸到示例页面区域的边缘。

*lpRect*<br/>
指向包含绘图区域坐标的[CRect](../../atl-mfc-shared/reference/crect-class.md)或[RECT](/windows/win32/api/windef/ns-windef-rect)对象的指针。

### <a name="return-value"></a>返回值

处理时非零值;否则 0。

### <a name="remarks"></a>备注

然后，此图像将作为通用 OLE 页面设置对话框的一部分显示。 默认实现绘制文本页面的图像。

重写此函数以自定义图像的特定区域或整个图像的图形。 可以通过对**大小写**语句使用**switch**语句来检查*nMessage*的值来执行此操作。 例如，要自定义页面图像内容的呈现，可以使用以下示例代码：

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

请注意，您不需要处理每种情况下的*nMessage*。 您可以选择处理图像的一个组件、图像的几个组件或整个区域。

## <a name="cpagesetupdialogpredrawpage"></a><a name="predrawpage"></a>CPagesetup对话：:P重新绘制页面

在绘制打印页的屏幕图像之前，由框架调用。

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>参数

*wPaper*<br/>
指定指示纸张大小的值。 此值可以是[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)结构描述中列出的**DMPAPER_** 值之一。

*wFlags*<br/>
指示纸张或信封的方向，以及打印机是点阵还是 HPPCL（惠普打印机控制语言）设备。 此参数可以具有下列值之一：

- 0x001 横向模式下的纸张（点矩阵）

- 0x003 横向模式下的纸张 （HPPCL）

- 0x005 纵向模式下的纸张（点矩阵）

- 0x007 纵向模式下的纸张 （HPPCL）

- 0x00b 横向模式下的信封 （HPPCL）

- 0x00d 纵向模式下的信封（点矩阵）

- 0x019 横向模式下的信封（点矩阵）

- 0x01f 纵向模式下的信封（点矩阵）

*pPSD*<br/>
指向 `PAGESETUPDLG` 结构的指针。 有关[PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)的详细信息，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

处理时非零值;否则 0。

### <a name="remarks"></a>备注

重写此函数以自定义图像的图形。 如果重写此函数并返回 TRUE，则必须绘制整个图像。 如果重写此函数并返回 FALSE，则整个默认图像由框架绘制。

## <a name="see-also"></a>另请参阅

[MFC 样品 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
