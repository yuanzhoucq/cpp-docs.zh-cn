---
title: "CMFCKeyMapDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CMFCKeyMapDialog class
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6599f5c3cda6eb407f4545d42528c1c68950b94c
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CMFCKeyMapDialog::DoModal](#domodal)|键盘映射对话框中显示。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](#formatitem)|由框架来构建一个字符串，描述键映射调用。 默认情况下，该字符串包含的命令名称、 快捷方式使用的密钥和快捷方式键描述。|  
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|检索一个字符串，包含与指定的命令的快捷键的列表。|  
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|在新项插入到内部列表控件中支持键盘映射控件之前，由框架调用。|  
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|由框架可在新页上打印的键盘映射的标头调用。|  
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|由框架要打印的键盘映射项调用。|  
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|调用由框架在支持键盘映射控件的内部列表控件中设置列标题。|  
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|当用户单击由框架调用**打印**按钮。|  
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|调用由框架在支持键盘映射控件的内部列表控件中设置列的宽度。|  
  
## <a name="remarks"></a>备注  
 使用`CMFCKeyMapDialog`类，以实现可调整大小的键盘映射对话框。 对话框中使用列表视图控件来显示键盘快捷方式和相关的命令。  
  
 若要使用`CMFCKeyMapDialog`类在应用程序中，将传递一个指针到主框架窗口以参数形式向`CMFCKeyMapDialog`构造函数。 然后，调用`DoModal`方法来启动一个模式对话框。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxkeymapdialog.h  
  
##  <a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog  
 构造 `CMFCKeyMapDialog` 对象。  
  
```  
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bEnablePrint=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParentFrame`  
 指向的父窗口的指针`CMFCKeyMapDialog`对象。  
  
 [in] `bEnablePrint`  
 `TRUE`如果可以打印快捷键的列表;，否则为`FALSE`。 默认值为 `FALSE`。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCKeyMapDialog`类。 此示例摘自[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&21;](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CMFCKeyMapDialog::DoModal  
 键盘映射对话框中显示。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 一个有符号的整数，如`IDOK`或`IDCANCEL`，也就是说，传递给[CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog)方法。 该方法，反过来，关闭对话框。 有关详细信息，请参阅[CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal)。  
  
### <a name="remarks"></a>备注  
 键盘映射对话框中可以选择并分配到各种类别的命令的快捷键。 此外，您可以将所选的快捷键和及其说明复制到剪贴板。  
  
##  <a name="formatitem"></a>CMFCKeyMapDialog::FormatItem  
 由框架来构建一个字符串，描述键映射调用。 默认情况下，该字符串包含的命令名称、 快捷方式使用的密钥和快捷方式键描述。  
  
```  
virtual CString FormatItem(int nItem) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nItem`  
 内部列表中的键映射的项的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 一个`CString`包含带格式的项文本的对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys  
 检索一个字符串值。 该字符串包含与指定的命令的快捷键的列表。  
  
```  
virtual CString GetCommandKeys(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 命令 id。  
  
### <a name="return-value"></a>返回值  
 以分号分隔 （;） 的键盘快捷方式的列表与指定的命令相关联。  
  
### <a name="remarks"></a>备注  
  
##  <a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem  
 在新项插入到支持键盘映射控件的内部列表控件之前，由框架调用。  
  
```  
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,  
    int nItem);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
 一个指向用于将键盘键组合映射到的命令名称和说明的工具栏按钮。 键映射项存储在内部列表控件中。  
  
 [in] `nItem`  
 一个指定内部列表控件中插入新键映射项的位置的从零开始索引。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader  
 由框架可在新页上打印的键盘映射的标头调用。  
  
```  
virtual int OnPrintHeader(
    CDC& dc,  
    int nPage,  
    int cx) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `dc`  
 打印机设备上下文。  
  
 [in] `nPage`  
 若要打印的页码。  
  
 [in] `cx`  
 标头，以像素为单位的水平偏移量。  
  
### <a name="return-value"></a>返回值  
 如果成功，则打印文本的高度。 有关详细信息，请参阅的返回值部分[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)。  
  
### <a name="remarks"></a>备注  
 框架使用此方法要打印的键盘映射。 默认情况下，此方法打印的页号、 应用程序名称和对话框标题。  
  
##  <a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem  
 由框架要打印的键盘映射项调用。  
  
```  
virtual int OnPrintItem(
    CDC& dc,  
    int nItem,  
    int y,  
    int cx,  
    BOOL bCalcHeight) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `dc`  
 打印机设备上下文。  
  
 [in] `nItem`  
 要打印的项的从零开始的索引。  
  
 [in] `y`  
 页的顶部和项的位置之间的垂直偏移量。  
  
 [in] `cx`  
 页上的左窗格和项的位置之间的水平偏移量。  
  
 [in] `bCalcHeight`  
 `TRUE`计算最佳的打印项; 高度`FALSE`截断打印的项，以使其适应默认的空间。  
  
### <a name="return-value"></a>返回值  
 打印的项的高度。  
  
### <a name="remarks"></a>备注  
 框架调用此方法，以打印键映射对话框项目。 默认情况下，此方法将输出项的命令名称、-> 快捷键和命令说明。  
  
##  <a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns  
 调用由框架在支持键盘映射控件的内部列表控件中设置列标题。  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法获取从三个资源的列标题。 命令列标题取自 IDS_AFXBARRES_COMMAND、 键列标题是从 IDS_AFXBARRES_KEYS，并说明列标题摘自 IDS_AFXBARRES_DESCRIPTION。  
  
##  <a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap  
 当用户单击由框架调用**打印**按钮。  
  
```  
virtual void PrintKeyMap();
```  
  
### <a name="remarks"></a>备注  
 `PrintKeyMap`方法打印键映射。 它创建一个新的打印作业，然后重复调用[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)和[CMFCKeyMapDialog::OnPrintItem](#onprintitem)方法之前打印所有键的映射。  
  
##  <a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth  
 调用由框架在支持键盘映射控件的内部列表控件中设置列的宽度。  
  
```  
virtual void SetColumnsWidth();
```  
  
### <a name="remarks"></a>备注  
 此方法将内部列表控件的列设置为默认宽度。 首先，计算快捷键键列的宽度。 然后的其余宽度的三分之一分配给该命令列和剩余的三分之二分配给说明列。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)

