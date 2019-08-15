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
ms.openlocfilehash: 18b17d0f40aaab6ba2a018a568950549eda23016
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503017"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog 类

封装由 Windows 公共 OLE“页面设置”对话框提供的服务以及对于设置和修改打印边距的额外支持。

## <a name="syntax"></a>语法

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|构造 `CPageSetupDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|创建用于打印的设备上下文。|
|[CPageSetupDialog::DoModal](#domodal)|显示对话框并允许用户进行选择。|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|返回打印机的设备名称。|
|[CPageSetupDialog::GetDevMode](#getdevmode)|返回打印机的当前 DEVMODE。|
|[CPageSetupDialog::GetDriverName](#getdrivername)|返回打印机使用的驱动程序。|
|[CPageSetupDialog::GetMargins](#getmargins)|返回打印机的当前边距设置。|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|返回打印机的纸张大小。|
|[CPageSetupDialog::GetPortName](#getportname)|返回输出端口名称。|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|由框架调用以呈现打印页的屏幕图像。|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|在呈现打印页的屏幕图像之前由框架调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|用于自定义`CPageSetupDialog`对象的结构。|

## <a name="remarks"></a>备注

此类旨在取代 "打印设置" 对话框。

若要使用`CPageSetupDialog`对象, 请先`CPageSetupDialog`使用构造函数创建对象。 构造对话框后, 您可以设置或修改`m_psd`数据成员中的任何值以初始化对话框控件的值。 [M_psd](#m_psd)结构的类型为 PAGESETUPDLG。

初始化对话框控件后, 调用`DoModal`成员函数以显示对话框, 并允许用户选择打印选项。 `DoModal`返回用户是否选择了 "确定" (IDOK) 或 "取消" (IDCANCEL) 按钮。

如果`DoModal`返回 IDOK, 则可以使用`CPageSetupDialog`多个成员`m_psd`函数, 或访问数据成员来检索用户输入的信息。

> [!NOTE]
>  在 "公共 OLE 页面设置" 对话框关闭后, 框架将不保存用户所做的任何更改。 应用程序本身会将此对话框中的所有值保存到永久性位置, 如应用程序的文档或应用程序类的成员。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>要求

**标头:** afxdlgs

##  <a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog

调用此函数可构造`CPageSetupDialog`对象。

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
可用于自定义对话框的设置的一个或多个标志。 可以使用按位 "或" 运算符组合这些值。 这些值具有以下含义:

- PSD_DEFAULTMINMARGINS 将页边距的最小允许宽度设置为与打印机的最小值相同。 如果同时指定了 PSD_MARGINS 和 PSD_MINMARGINS 标志, 则会忽略此标志。

- PSD_INWININIINTLMEASURE 未实现。

- PSD_MINMARGINS 使系统使用`rtMinMargin`成员中指定的值作为左、上、右和下边距的最小允许宽度。 系统禁止用户输入小于指定最小值的宽度。 如果未指定 PSD_MINMARGINS, 系统会将允许的最小宽度设置为打印机允许的最小宽度。

- PSD_MARGINS 激活边距控制区。

- PSD_INTHOUSANDTHSOFINCHES 会使对话框的单位以英寸为1/1000。

- PSD_INHUNDREDTHSOFMILLIMETERS 会使对话框的单位以毫米的1/100 度量。

- PSD_DISABLEMARGINS 禁用 "边距" 对话框控件。

- PSD_DISABLEPRINTER 禁用 "打印机" 按钮。

- 如果没有默认打印机, PSD_NOWARNING 将阻止显示警告消息。

- PSD_DISABLEORIENTATION 禁用 "页面方向" 对话框控件。

- PSD_RETURNDEFAULT 导致`CPageSetupDialog`返回在不显示对话框的情况下为系统默认打印机初始化的[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构。 假定`hDevNames` 和`hDevMode`均为 NULL; 否则, 函数将返回错误。 如果旧打印机驱动程序支持系统默认打印机 (早于 Windows 版本 3.0), 则仅`hDevNames`返回;`hDevMode`为 NULL。

- PSD_DISABLEPAPER 禁用纸张选择控件。

- PSD_SHOWHELP 导致对话框显示 "帮助" 按钮。 如果`hwndOwner`指定此标志, 则成员不能为 NULL。

- PSD_ENABLEPAGESETUPHOOK 启用中`lpfnSetupHook`指定的挂钩函数。

- PSD_ENABLEPAGESETUPTEMPLATE 使操作系统通过使用由`hInstance`和`lpSetupTemplateName`标识的对话框模板框来创建对话框。

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE 指示`hInstance`标识包含预加载对话框模板的数据块。 如果指定此`lpSetupTemplateName`标志, 系统将忽略。

- PSD_ENABLEPAGEPAINTHOOK 启用中`lpfnPagePaintHook`指定的挂钩函数。

- PSD_DISABLEPAGEPAINTING 禁用对话框的绘图区域。

*pParentWnd*<br/>
指向对话框父对象或所有者的指针。

### <a name="remarks"></a>备注

使用[DoModal](../../mfc/reference/cdialog-class.md#domodal)函数可显示该对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>CPageSetupDialog::CreatePrinterDC

从[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构创建打印机设备上下文。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>返回值

新创建的打印机设备上下文 (DC) 的句柄。

##  <a name="domodal"></a>CPageSetupDialog::D oModal

调用此函数以显示 "Windows common OLE 页面设置" 对话框, 并允许用户选择各种打印设置选项, 如打印边距、纸张大小和方向以及目标打印机。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL, 则调用 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定是否发生了错误。

IDOK 和 IDCANCEL 是常量, 用于指示用户是否选择了 "确定" 或 "取消" 按钮。

### <a name="remarks"></a>备注

此外, 用户还可以访问打印机设置选项, 例如, 特定于所选打印机的网络位置和属性。

如果希望通过设置`m_psd`结构的成员来初始化各种页面设置对话框选项, 应在调用`DoModal`之前以及在构造对话框对象后执行此操作。 调用`DoModal`后, 调用其他成员函数以检索用户在对话框中输入的设置或信息。

如果要传播用户输入的当前设置, 请调用[CWinApp:: SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter)。 此函数从`CPageSetupDialog`对象中获取信息, 并使用适当的属性初始化并选择一个新的打印机 DC。

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>示例

  请参阅[CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog)的示例。

##  <a name="getdevicename"></a>CPageSetupDialog::GetDeviceName

请在之后`DoModal`调用此函数以检索当前选定的打印机的名称。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>返回值

`CPageSetupDialog`对象使用的设备名称。

##  <a name="getdevmode"></a>CPageSetupDialog::GetDevMode

调用`DoModal`后调用此函数可检索有关`CPageSetupDialog`对象的打印机设备上下文的信息。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>返回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)数据结构, 其中包含有关打印机驱动程序的设备初始化和环境的信息。 必须使用 Windows SDK 中描述的 Windows [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock)函数来解锁此结构使用的内存。

##  <a name="getdrivername"></a>CPageSetupDialog:: GetDriverName

在调用[DoModal](../../mfc/reference/cprintdialog-class.md#domodal)之后调用此函数可检索系统定义的打印机设备驱动程序的名称。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>返回值

一个`CString` , 指定系统定义的驱动程序名称。

### <a name="remarks"></a>备注

在对[CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc)的调用`GetDriverName`中, 使用指向`lpszDriverName` `CString`返回的对象的指针作为的值。

##  <a name="getmargins"></a>CPageSetupDialog::GetMargins

调用后调用此函数`DoModal`可检索打印机设备驱动程序的边距。

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>参数

*lpRectMargins*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针, 该对象描述当前所选打印机的打印边距 (1/1000 英寸或 1/100 mm)。 如果不对此矩形感兴趣, 请为此参数传递 NULL。

*lpRectMinMargins*<br/>
指向`RECT`结构或对象的`CRect`指针, 该结构或对象描述当前所选打印机的最小打印边距 (1/1000 英寸或 1/100 mm)。 如果不对此矩形感兴趣, 请为此参数传递 NULL。

##  <a name="getpapersize"></a>CPageSetupDialog::GetPaperSize

调用此函数可检索选定要打印的纸张的大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>返回值

一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象, 该对象包含选择打印的纸张大小 (1/1000 英寸或 1/100 mm)。

##  <a name="getportname"></a>CPageSetupDialog::GetPortName

调用`DoModal`后调用此函数可检索当前选定的打印机端口的名称。

```
CString GetPortName() const;
```

### <a name="return-value"></a>返回值

当前选定的打印机端口的名称。

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

PAGESETUPDLG 类型的结构, 其成员存储对话框对象的特征。

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>备注

构造`CPageSetupDialog`对象之后, 您可以使用`m_psd`在调用`DoModal`成员函数之前设置对话框的各个方面。

如果直接修改`m_psd`数据成员, 将重写任何默认行为。

有关[PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-psdw)结构的详细信息, 请参阅 Windows SDK。

请参阅[CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog)的示例。

##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage

由框架调用, 用于绘制打印页的屏幕图像。

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文的指针。

*nMessage*<br/>
指定一条消息, 指示当前正在绘制的页面区域。 可以是以下各项之一：

- WM_PSD_FULLPAGERECT 整个页面区域。

- WM_PSD_MINMARGINRECT 当前最小边距。

- WM_PSD_MARGINRECT 当前边距。

- WM_PSD_GREEKTEXTRECT 页面的内容。

- 为邮票表示形式保留的 WM_PSD_ENVSTAMPRECT 区域。

- 返回地址表示形式的 WM_PSD_YAFULLPAGERECT 区域。 此区域延伸到示例页区域的边缘。

*lpRect*<br/>
指向包含绘图区域坐标的[CRect](../../atl-mfc-shared/reference/crect-class.md)或[RECT](/windows/win32/api/windef/ns-windef-rect)对象的指针。

### <a name="return-value"></a>返回值

如果已处理, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此图像随后会显示为 "通用 OLE 页面设置" 对话框的一部分。 默认实现绘制文本页的图像。

重写此函数以自定义图像的特定区域或整个图像的绘制。 可以通过使用**switch**语句来执行此操作, 并用**Case**语句检查*n 消息*的值。 例如, 若要自定义页面图像内容的呈现, 可以使用以下示例代码:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

请注意, 不需要处理*n 消息*的每种情况。 你可以选择处理图像的一个组件、图像的多个组件或整个区域。

##  <a name="predrawpage"></a>CPageSetupDialog::P reDrawPage

在绘制打印页的屏幕图像之前由框架调用。

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>参数

*wPaper*<br/>
指定一个值, 该值指示纸张大小。 此值可以是[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)结构的说明中列出的**DMPAPER_** 值之一。

*wFlags*<br/>
指示纸张或信封的方向, 以及打印机是点阵还是 HPPCL (Hewlett Packard Printer Control Language) 设备。 此参数可以具有下列值之一：

- 横向模式下的0x001 纸 (点阵)

- 横向模式下的0x003 纸 (HPPCL)

- 纵向模式下的0x005 纸 (点阵)

- 纵向模式下的0x007 纸 (HPPCL)

- 横向模式下的0x00b 信封 (HPPCL)

- 纵向模式下的0x00d 信封 (点阵)

- 横向模式下的0x019 信封 (点阵)

- 纵向模式下的0x01f 信封 (点阵)

*pPSD*<br/>
指向 `PAGESETUPDLG` 结构的指针。 有关[PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-psdw)的详细信息, 请参阅 Windows SDK。

### <a name="return-value"></a>返回值

如果已处理, 则为非零值;否则为0。

### <a name="remarks"></a>备注

重写此函数以自定义图像的绘图。 如果重写此函数并返回 TRUE, 则必须绘制整个图像。 如果重写此函数并返回 FALSE, 则框架将绘制整个默认图像。

## <a name="see-also"></a>请参阅

[MFC 示例写字板](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
