---
title: "COlePasteSpecialDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
dev_langs: C++
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8680842f0aeeebf98eabc0f278089781290ad902
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog 类
用于 OLE“选择性粘贴”对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class COlePasteSpecialDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|构造 `COlePasteSpecialDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COlePasteSpecialDialog::AddFormat](#addformat)|将自定义格式添加到你的应用程序可以粘贴的格式的列表。|  
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|将新条目添加到受支持的剪贴板格式的列表。|  
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|将添加**CF_BITMAP**， **CF_DIB**， `CF_METAFILEPICT`，和 （可选）`CF_LINKSOURCE`你的应用程序可以粘贴到格式的列表。|  
|[COlePasteSpecialDialog::CreateItem](#createitem)|创建使用指定的格式到容器文档中的项。|  
|[COlePasteSpecialDialog::DoModal](#domodal)|显示 OLE 选择性粘贴对话框。|  
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|指示是否绘制项作为图标或不。|  
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项图标窗体关联的图元文件的句柄。|  
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|获取已由用户选择的可用粘贴选项的索引。|  
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|获取所选内容的类型。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COlePasteSpecialDialog::m_ps](#m_ps)|类型的结构**OLEUIPASTESPECIAL**控制对话框中的函数。|  
  
## <a name="remarks"></a>备注  
 创建类的对象`COlePasteSpecialDialog`如果想要调用此对话框。 后`COlePasteSpecialDialog`构造对象，则可以使用[AddFormat](#addformat)和[AddStandardFormats](#addstandardformats)成员函数将剪贴板格式添加到对话框中。 你还可以使用[m_ps](#m_ps)结构初始化的值或在对话框中的控件的状态。 `m_ps`结构属于类型**OLEUIPASTESPECIAL**。  
  
 有关详细信息，请参阅[OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) Windows SDK 中的结构。  
  
 有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxodlgs.h  
  
##  <a name="addformat"></a>COlePasteSpecialDialog::AddFormat  
 调用此函数可将新的格式添加到你的应用程序可以支持选择性粘贴操作中的格式的列表。  
  
```  
void AddFormat(
    const FORMATETC& formatEtc,  
    LPTSTR lpszFormat,  
    LPTSTR lpszResult,  
    DWORD flags);

 
void AddFormat(
    UINT cf,  
    DWORD tymed,  
    UINT nFormatID,  
    BOOL bEnableIcon,  
    BOOL bLink);
```  
  
### <a name="parameters"></a>参数  
 *格式*  
 对要添加的数据类型的引用。  
  
 `lpszFormat`  
 介绍向用户格式的字符串。  
  
 *lpszResult*  
 介绍的结果，如果在对话框中选择了此格式的字符串。  
  
 `flags`  
 不同链接和嵌入可用于此格式选项。 此标志是一个或多个中的不同值的按位组合**OLEUIPASTEFLAG**枚举类型。  
  
 `cf`  
 要添加的剪贴板格式。  
  
 *tymed*  
 这种形式的媒体类型。 这是一个或多个中的值的按位组合**TYMED**枚举类型。  
  
 `nFormatID`  
 标识此格式的字符串的 ID。 此字符串的格式是以 \n 字符分隔的两个单独的字符串。 第一个字符串是相同会传递中*lpstrFormat*参数，而第二个是相同*lpstrResult*参数。  
  
 *bEnableIcon*  
 确定是否显示为图标复选框是否启用列表框中选择了此格式时的标志。  
  
 *闪烁*  
 确定在列表框中选择了此格式时，是否启用粘贴链接单选按钮的标志。  
  
### <a name="remarks"></a>备注  
 可以调用此函数以进行添加任一标准格式，例如**CF_TEXT**或**CF_TIFF**或你的应用程序已使用系统注册的自定义格式。 有关将数据对象粘贴到你的应用程序的详细信息，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227)枚举类型和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的结构。  
  
 有关详细信息，请参阅[OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172)枚举在 Windows SDK 中的类型。  
  
##  <a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry  
 将新条目添加到受支持的剪贴板格式的列表。  
  
```  
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 要添加的剪贴板格式。  
  
### <a name="return-value"></a>返回值  
 [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172)结构，它包含的新链接项的信息。  
  
##  <a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats  
 调用此函数可将以下剪贴板格式添加到你的应用程序可以支持选择性粘贴操作中的格式的列表：  
  
```  
void AddStandardFormats(BOOL bEnableLink = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bEnableLink*  
 用于确定是否将添加标志`CF_LINKSOURCE`你的应用程序可以粘贴到格式的列表。  
  
### <a name="remarks"></a>备注  
  
- **CF_BITMAP**  
  
- **CF_DIB**  
  
- `CF_METAFILEPICT`  
  
- **"嵌入的对象"**  
  
-   （可选）**"源链接"**  
  
 这些格式用于支持嵌入和链接。  
  
##  <a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog  
 构造 `COlePasteSpecialDialog` 对象。  
  
```  
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,  
    COleDataObject* pDataObject = NULL,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 创建一个标记，包含任意数量的使用按位 OR 运算符组合以下标志：  
  
- `PSF_SELECTPASTE`指定当调用对话框中，确认将最初选中粘贴单选按钮。 不能与结合使用`PSF_SELECTPASTELINK`。 这是默认设置。  
  
- `PSF_SELECTPASTELINK`指定单选按钮将处于粘贴链接检查最初调用对话框中时。 不能与结合使用`PSF_SELECTPASTE`。  
  
- `PSF_CHECKDISPLAYASICON`指定调用对话框中时，确认将最初选中显示为图标复选框。  
  
- `PSF_SHOWHELP`指定调用对话框中时，将显示帮助按钮。  
  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)粘贴。 如果此值为**NULL**，它获取`COleDataObject`从剪贴板。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框中的父窗口设置为应用程序主窗口。  
  
### <a name="remarks"></a>备注  
 此函数仅构造`COlePasteSpecialDialog`对象。 若要显示对话框中，调用[DoModal](#domodal)函数。  
  
 有关详细信息，请参阅[OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172)枚举在 Windows SDK 中的类型。  
  
##  <a name="createitem"></a>COlePasteSpecialDialog::CreateItem  
 创建已在选择性粘贴对话框中选择的新项。  
  
```  
BOOL CreateItem(COleClientItem* pNewItem);
```  
  
### <a name="parameters"></a>参数  
 *pNewItem*  
 指向`COleClientItem`实例。 不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则在创建项则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数应该仅调用后[DoModal](#domodal)返回**IDOK**。  
  
##  <a name="domodal"></a>COlePasteSpecialDialog::DoModal  
 显示 OLE 选择性粘贴对话框。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
- **IDOK**如果成功显示该对话框。  
  
- **IDCANCEL**如果用户已取消对话框。  
  
- **IDABORT**如果发生错误。 如果**IDABORT**是返回，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型详细信息。 有关可能的错误的列表，请参阅[OleUIPasteSpecial](http://msdn.microsoft.com/library/windows/desktop/ms694512) Windows SDK 中的函数。  
  
### <a name="remarks"></a>备注  
 如果你想要通过设置成员的初始化各种对话框控件[m_ps](#m_ps)结构，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 如果`DoModal`返回**IDOK**，您可以调用其他成员函数检索的设置或用户的信息输入到对话框。  
  
##  <a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect  
 确定是否用户选择了以图标形式显示的选定的项。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现对象所需的方法。  
  
- `DVASPECT_CONTENT`返回如果解除该对话框时，显示为图标复选框已不检查。  
  
- `DVASPECT_ICON`返回如果解除对话框中时，则显示为图标复选框已选中状态。  
  
### <a name="remarks"></a>备注  
 仅调用此函数后的[DoModal](#domodal)返回**IDOK**。  
  
 绘制方面的详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的结构。  
  
##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile  
 获取与用户选择的项关联的元文件。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果显示为图标复选框时通过选择解除对话框中选择了包含的选定项的图标化方面的图元文件的句柄**确定**; 否则为**NULL**。  
  
##  <a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex  
 获取的索引值与此项关联选定的用户。  
  
```  
int GetPasteIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 到的数组索引**OLEUIPASTEENTRY**用户选定的结构。 执行粘贴操作时，应使用对应于所选索引的格式。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[OLEUIPASTEENTRY](http://msdn.microsoft.com/library/windows/desktop/ms690165) Windows SDK 中的结构。  
  
##  <a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType  
 确定用户所做的选择的类型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回类型所做选择。  
  
### <a name="remarks"></a>备注  
 通过指定返回类型值**选择**枚举类型中声明`COlePasteSpecialDialog`类。  
  
```  
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };  
```  
  
 请按照这些值的简短 desccriptions 操作：  
  
- **COlePasteSpecialDialog::pasteLink**检查粘贴链接单选按钮，并且所选的格式标准的 OLE 格式。  
  
- **COlePasteSpecialDialog::pasteNormal**检查粘贴单选按钮，并且所选的格式标准的 OLE 格式。  
  
- **COlePasteSpecialDialog::pasteOther**所选的格式不标准 OLE 格式。  
  
- **COlePasteSpecialDialog::pasteStatic**选的格式出现图元文件。  
  
##  <a name="m_ps"></a>COlePasteSpecialDialog::m_ps  
 类型的结构**OLEUIPASTESPECIAL**用于控制选择性粘贴对话框中的行为。  
  
```  
OLEUIPASTESPECIAL m_ps;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) Windows SDK 中的结构。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)
