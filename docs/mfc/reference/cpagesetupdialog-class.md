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
ms.openlocfilehash: 9a8940aa23b23281a6de6ce7e75bb1e43341b14a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277880"
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
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|创建用于打印设备上下文。|
|[CPageSetupDialog::DoModal](#domodal)|显示对话框，并允许用户进行选择。|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|返回打印机的设备的名称。|
|[CPageSetupDialog::GetDevMode](#getdevmode)|返回当前 DEVMODE 的打印机。|
|[CPageSetupDialog::GetDriverName](#getdrivername)|返回使用打印机的驱动程序。|
|[CPageSetupDialog::GetMargins](#getmargins)|返回当前的打印机的边距设置。|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|返回打印机的纸张的大小。|
|[CPageSetupDialog::GetPortName](#getportname)|返回的输出端口名称。|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|由框架调用以呈现打印页的屏幕图像。|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|呈现打印页的屏幕图像之前由框架调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|用于自定义的结构`CPageSetupDialog`对象。|

## <a name="remarks"></a>备注

设计此类来代替打印设置对话框。

若要使用`CPageSetupDialog`对象，请先创建对象使用`CPageSetupDialog`构造函数。 一旦对话框的构造完成后，可以设置或修改中的任何值`m_psd`数据成员初始化的对话框的控件的值。 [M_psd](#m_psd)结构属于类型 PAGESETUPDLG。

初始化对话框控件之后, 调用`DoModal`成员函数以显示该对话框，并允许用户选择打印选项。 `DoModal` 返回用户是否选择了确定 (IDOK) 或取消 (IDCANCEL) 按钮。

如果`DoModal`返回 IDOK，您可以使用其中几`CPageSetupDialog`的成员函数或访问`m_psd`数据成员，以检索信息由用户输入。

> [!NOTE]
>  常见的 OLE 页面设置对话框关闭后，用户所做的任何更改将不保存框架。 它是应用程序本身负责保存到永久位置，例如，应用程序的文档或应用程序类的成员的此对话框中的任何值。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>要求

**标头：** afxdlgs.h

##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog

调用此函数来构造`CPageSetupDialog`对象。

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
您可以使用自定义对话框的设置的一个或多个标志。 可以使用按位 OR 运算符组合的值。 这些值的含义如下：

- PSD_DEFAULTMINMARGINS 设置页边距为打印机的最小值相同的最小允许宽度。 如果还指定 PSD_MARGINS 和 PSD_MINMARGINS 标志，则忽略此标志。

- PSD_INWININIINTLMEASURE 未实现。

- PSD_MINMARGINS 会导致系统使用中指定的值`rtMinMargin`成员作为左侧、 顶部、 右侧和底部边距的最小允许宽度。 系统可防止用户输入不超过指定的最小宽度。 如果未指定 PSD_MINMARGINS，系统会将最小允许宽度设置为所允许的打印机。

- PSD_MARGINS 激活边距控件区域。

- PSD_INTHOUSANDTHSOFINCHES 会导致对话框的要以英寸为单位的 1/1000 个单位的单位。

- PSD_INHUNDREDTHSOFMILLIMETERS 会导致对话框的 1/100 的毫米中测量的单位。

- PSD_DISABLEMARGINS 禁用边距对话框控件。

- PSD_DISABLEPRINTER 禁用打印机按钮。

- PSD_NOWARNING 阻止警告消息的默认打印机时显示。

- PSD_DISABLEORIENTATION 禁用页面方向对话框控件。

- PSD_RETURNDEFAULT 会导致`CPageSetupDialog`以返回[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)并[DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames)而不会显示一个对话框中的系统的默认打印机初始化的结构。 假定这两个`hDevNames`和`hDevMode`NULL; 否则，该函数将返回错误。 如果系统默认打印机支持的旧的打印机驱动程序 （早于 Windows 版本 3.0） 仅`hDevNames`返回;`hDevMode`为 NULL。

- PSD_DISABLEPAPER 禁用纸张选择控件。

- PSD_SHOWHELP 会使对话框以显示帮助按钮。 `hwndOwner`成员必须不可为 NULL，如果指定此标志。

- PSD_ENABLEPAGESETUPHOOK 使挂钩函数中指定`lpfnSetupHook`。

- PSD_ENABLEPAGESETUPTEMPLATE 会导致操作系统使用标识对话框模板中创建的对话框`hInstance`和`lpSetupTemplateName`。

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE 指示`hInstance`标识包含预加载的对话框模板的数据块。 系统会忽略`lpSetupTemplateName`如果指定此标志。

- PSD_ENABLEPAGEPAINTHOOK 使挂钩函数中指定`lpfnPagePaintHook`。

- PSD_DISABLEPAGEPAINTING 禁用对话框中的绘图区域。

*pParentWnd*<br/>
到对话框的父成员或所有者的指针。

### <a name="remarks"></a>备注

使用[DoModal](../../mfc/reference/cdialog-class.md#domodal)函数来显示该对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC

创建打印机设备上下文中的从[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)并[DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames)结构。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>返回值

新创建的打印机设备上下文 (DC) 的句柄。

##  <a name="domodal"></a>  CPageSetupDialog::DoModal

调用此函数可显示 Windows 公共 OLE 页面设置对话框中，并允许用户选择各种打印设置选项，如打印边距、 大小和方向的纸张和目标打印机。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL，则调用 Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定是否发生了错误。

IDOK 和 IDCANCEL 是常数，用于指示是否在用户选择了确定或取消按钮。

### <a name="remarks"></a>备注

此外，用户可以访问打印机安装程序选项，如网络位置和特定于所选打印机的属性。

如果你想要通过设置的成员初始化的各种页面设置对话框选项`m_psd`结构，您应该在调用前为`DoModal`，并在构造对话框对象之后。 在调用`DoModal`，调用函数来检索设置或用户的信息输入到对话框中的其他成员。

如果你想要传播由用户输入的当前设置，请调用[CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter)。 此函数采用从信息`CPageSetupDialog`对象并初始化并选择新打印机 DC 使用适当的属性。

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>示例

  有关示例，请参阅[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)。

##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName

调用此函数后的`DoModal`来检索当前所选打印机的名称。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>返回值

使用的设备名称`CPageSetupDialog`对象。

##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode

调用此函数后调用`DoModal`来检索有关打印机设备上下文的信息`CPageSetupDialog`对象。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>返回值

[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)数据结构，其中包含有关设备初始化和环境的打印驱动程序的信息。 您必须解除锁定此结构与 Windows 所占用的内存[GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock)函数，Windows SDK 中所述。

##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName

调用此函数后调用[DoModal](../../mfc/reference/cprintdialog-class.md#domodal)检索系统定义的打印机设备驱动程序的名称。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>返回值

一个`CString`指定的系统定义的驱动程序名称。

### <a name="remarks"></a>备注

使用指向指针`CString`返回的对象`GetDriverName`的值作为`lpszDriverName`对的调用中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。

##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins

在调用后调用此函数`DoModal`检索打印机设备驱动程序的边距。

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>参数

*lpRectMargins*<br/>
指向[RECT](/windows/desktop/api/windef/ns-windef-tagrect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)当前所选打印机的打印边距 （以 1/1000 个英寸或 1/100 mm） 描述的对象。 如果您不感兴趣此矩形，为此参数传递 NULL。

*lpRectMinMargins*<br/>
指向`RECT`结构或`CRect`当前所选打印机的最小打印边距 （以 1/1000 个英寸或 1/100 mm） 描述的对象。 如果您不感兴趣此矩形，为此参数传递 NULL。

##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize

调用此函数可检索用于打印在纸张的大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>返回值

一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，其中包含 （在 1/1000 个英寸或 1/100 mm） 打印选定的纸张大小。

##  <a name="getportname"></a>  CPageSetupDialog::GetPortName

调用后调用此函数`DoModal`来检索当前所选的打印机端口的名称。

```
CString GetPortName() const;
```

### <a name="return-value"></a>返回值

当前所选的打印机端口的名称。

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

类型 PAGESETUPDLG，其成员存储对话框对象的特征的结构。

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>备注

构造后`CPageSetupDialog`对象，可以使用`m_psd`若要设置之前，调用对话框中的各个方面`DoModal`成员函数。

如果您修改`m_psd`数据成员直接，您将重写任何默认行为。

有关详细信息[PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda)结构，请参阅 Windows SDK。

有关示例，请参阅[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)。

##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage

由框架调用以绘制打印页的屏幕图像。

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文指针。

*nMessage*<br/>
指定一条消息，指出页当前所绘制的区域。 可以是以下各项之一：

- WM_PSD_FULLPAGERECT 整个页面区域。

- WM_PSD_MINMARGINRECT 当前最小边距。

- WM_PSD_MARGINRECT 当前边距。

- WM_PSD_GREEKTEXTRECT 页面内容。

- WM_PSD_ENVSTAMPRECT 邮票表示形式为保留区域。

- 寄信人地址表示形式的 WM_PSD_YAFULLPAGERECT 区域。 此区域将扩展到示例页面区域的边缘。

*lpRect*<br/>
指向[CRect](../../atl-mfc-shared/reference/crect-class.md)或[RECT](/windows/desktop/api/windef/ns-windef-tagrect)对象，包含在绘图区域的坐标。

### <a name="return-value"></a>返回值

如果处理; 的非零值否则为 0。

### <a name="remarks"></a>备注

此映像则显示为公共 OLE 页面设置对话框中的一部分。 默认实现将绘制文本的页面的图像。

重写此函数可自定义映像或整个图像的特定区域的绘制。 您可以执行此操作通过使用**切换**语句**用例**检查的值的语句*n 消息*。 例如，若要自定义内容页面图像的呈现，可以使用下面的示例代码：

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

请注意，不需要处理的每种情况下*n 消息*。 您可以选择处理图像的图像或整个区域的多个组件的一个组件。

##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage

绘制打印页的屏幕图像之前由框架调用。

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>参数

*wPaper*<br/>
指定一个值，指示的纸张大小。 此值可以是之一**DMPAPER_** 说明中列出的值[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)结构。

*wFlags*<br/>
指示的方向的纸张或信封，并且打印机已点阵或为 HPPCL （Hewlett Packard 打印机控制语言） 设备。 此参数可以具有下列值之一：

- 0x001 纸张在横向模式下 （点阵）

- 0x003 纸张在横向模式下 (为 HPPCL)

- 0x005 纸张在纵向模式下 （点阵）

- 0x007 纸张在纵向模式下 (为 HPPCL)

- 0x00b 信封横向模式 (为 HPPCL)

- 0x00d 信封纵向模式 （点阵）

- 0x019 信封横向模式 （点阵）

- 0x01f 信封纵向模式 （点阵）

*pPSD*<br/>
指向 `PAGESETUPDLG` 结构的指针。 有关详细信息[PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda)，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

如果处理; 的非零值否则为 0。

### <a name="remarks"></a>备注

重写此函数可自定义绘制图像。 如果重写此函数，并且返回 TRUE，则必须绘制整个图像。 如果重写此函数返回 FALSE，则整个默认图像的绘制框架。

## <a name="see-also"></a>请参阅

[MFC 示例写字板](../../visual-cpp-samples.md)<br/>
[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
