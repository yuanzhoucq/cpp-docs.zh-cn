---
title: CMFCKeyMapDialog 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 810a375fce13d8628db5ff00d89964d84c83b525
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704036"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog 类
`CMFCKeyMapDialog`类支持将命令映射到键盘上的键的控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|构造 `CMFCKeyMapDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCKeyMapDialog::DoModal](#domodal)|显示键盘映射对话框。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](#formatitem)|由框架调用以生成描述键映射的字符串。 默认情况下，该字符串包含命令名称、 使用的键盘快捷方式和快捷方式的关键说明。|  
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|检索一个字符串，包含与指定的命令关联的键盘快捷方式的列表。|  
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|在新项插入到支持键盘映射控件的内部列表控件之前由框架调用。|  
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|由框架调用以在新页上打印的键盘映射的标头。|  
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|由框架调用以打印键盘映射项。|  
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|由框架调用以在支持键盘映射控件的内部列表控件中设置列标题。|  
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|在用户单击时由框架调用**打印**按钮。|  
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|由框架调用以在支持键盘映射控件的内部列表控件中设置列的宽度。|  
  
## <a name="remarks"></a>备注  
 使用`CMFCKeyMapDialog`类，以实现可调整大小的键盘映射对话框。 对话框中使用列表视图控件来显示键盘快捷方式和其关联的命令。  
  
 若要使用`CMFCKeyMapDialog`类在应用程序中，指针到主框架窗口作为参数传递到`CMFCKeyMapDialog`构造函数。 然后，调用`DoModal`方法以启动模式对话框。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxkeymapdialog.h  
  
##  <a name="cmfckeymapdialog"></a>  CMFCKeyMapDialog::CMFCKeyMapDialog  
 构造 `CMFCKeyMapDialog` 对象。  
  
```  
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bEnablePrint=FALSE);
```  
  
### <a name="parameters"></a>参数  
*pWndParentFrame*<br/>
[in]向父窗口的指针`CMFCKeyMapDialog`对象。  
  
*bEnablePrint*<br/>
[in]可以打印快捷键的列表; 如果为 TRUE否则为 FALSE。 默认值为 FALSE。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCKeyMapDialog`类。 此示例摘自[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>  CMFCKeyMapDialog::DoModal  
 显示键盘映射对话框。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 有符号的整数，例如 IDOK 或 IDCANCEL，传递给[CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog)方法。 该方法，反过来，关闭对话框。 有关详细信息，请参阅[CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal)。  
  
### <a name="remarks"></a>备注  
 键盘映射对话框中，可选择并为各种类别的命令分配快捷键。 此外，您可以将所选的快捷键和及其说明复制到剪贴板。  
  
##  <a name="formatitem"></a>  CMFCKeyMapDialog::FormatItem  
 由框架调用以生成描述键映射的字符串。 默认情况下，该字符串包含命令名称、 使用的键盘快捷方式和快捷方式的关键说明。  
  
```  
virtual CString FormatItem(int nItem) const;  
```  
  
### <a name="parameters"></a>参数  
*nItem*<br/>
[in]键映射的内部列表中项的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，其中包含带格式的项文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcommandkeys"></a>  CMFCKeyMapDialog::GetCommandKeys  
 检索一个字符串值。 该字符串包含与指定的命令相关联的快捷键的列表。  
  
```  
virtual CString GetCommandKeys(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>参数  
*uiCmdID*<br/>
[in]命令 id。  
  
### <a name="return-value"></a>返回值  
 以分号分隔 （;） 的键盘快捷方式的列表与指定的命令相关联。  
  
### <a name="remarks"></a>备注  
  
##  <a name="oninsertitem"></a>  CMFCKeyMapDialog::OnInsertItem  
 在新项插入到支持的键盘映射控件的内部列表控件之前由框架调用。  
  
```  
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,  
    int nItem);
```  
  
### <a name="parameters"></a>参数  
*pButton*<br/>
[in]一个指向用于将键盘键组合映射到的命令名称和说明的工具栏按钮。 键映射项存储在一个内部列表控件中。  
  
*nItem*<br/>
[in]一个指定内部列表控件中插入新的键映射项的位置的从零开始索引。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onprintheader"></a>  CMFCKeyMapDialog::OnPrintHeader  
 由框架调用以在新页上打印的键盘映射的标头。  
  
```  
virtual int OnPrintHeader(
    CDC& dc,  
    int nPage,  
    int cx) const;  
```  
  
### <a name="parameters"></a>参数  
*dc*<br/>
[in]打印机设备上下文。  
  
*n 页面*<br/>
[in]要打印的页码。  
  
*cx*<br/>
[in]标头，以像素为单位的水平偏移量。  
  
### <a name="return-value"></a>返回值  
 如果成功，则打印文本的高度。 有关详细信息，请参阅的返回值部分[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)。  
  
### <a name="remarks"></a>备注  
 该框架使用此方法要打印的键盘映射。 默认情况下，此方法将打印的页码，应用程序名称和对话框标题。  
  
##  <a name="onprintitem"></a>  CMFCKeyMapDialog::OnPrintItem  
 由框架调用以打印键盘映射项。  
  
```  
virtual int OnPrintItem(
    CDC& dc,  
    int nItem,  
    int y,  
    int cx,  
    BOOL bCalcHeight) const;  
```  
  
### <a name="parameters"></a>参数  
*dc*<br/>
[in]打印机设备上下文。  
  
*nItem*<br/>
[in]要打印的项的从零开始的索引。  
  
*y*<br/>
[in]页面顶部和项的位置之间的垂直偏移量。  
  
*cx*<br/>
[in]在页面左侧和项的位置之间的水平偏移量。  
  
*bCalcHeight*<br/>
[in]若要计算的打印项; 最佳高度，则返回 TRUE如果为 FALSE，使其适应默认空间截断打印的项。  
  
### <a name="return-value"></a>返回值  
 打印的项的高度。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以打印键映射对话框项目。 默认情况下，此方法将输出项的命令名称、 键盘快捷方式和命令说明。  
  
##  <a name="onsetcolumns"></a>  CMFCKeyMapDialog::OnSetColumns  
 由框架调用以在支持键盘映射控件的内部列表控件中设置列标题。  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法从三个资源获取的列的标题。 命令列标题是从 IDS_AFXBARRES_COMMAND，键列标题是从 IDS_AFXBARRES_KEYS，说明列标题是从 IDS_AFXBARRES_DESCRIPTION。  
  
##  <a name="printkeymap"></a>  CMFCKeyMapDialog::PrintKeyMap  
 在用户单击时由框架调用**打印**按钮。  
  
```  
virtual void PrintKeyMap();
```  
  
### <a name="remarks"></a>备注  
 `PrintKeyMap`方法打印键映射。 它将启动新的打印作业，然后重复调用[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)并[CMFCKeyMapDialog::OnPrintItem](#onprintitem)方法直到打印所有键的映射。  
  
##  <a name="setcolumnswidth"></a>  CMFCKeyMapDialog::SetColumnsWidth  
 由框架调用以在支持键盘映射控件的内部列表控件中设置列的宽度。  
  
```  
virtual void SetColumnsWidth();
```  
  
### <a name="remarks"></a>备注  
 此方法将内部列表控件的列设置为默认宽度。 首先，将计算的快捷方式键列的宽度。 然后的其余部分的三分之一分配给命令列，剩余的三分之二分配给说明列。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)
