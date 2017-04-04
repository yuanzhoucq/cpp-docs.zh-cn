---
title: "COlePasteSpecialDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- Paste Special dialog box
- dialog boxes, Paste Special
- OLE Paste Special dialog box
- COlePasteSpecialDialog class
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
caps.latest.revision: 24
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
ms.openlocfilehash: 6984d714248815b062c564c7eed5c315990855af
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[COlePasteSpecialDialog::AddFormat](#addformat)|将自定义格式添加到您的应用程序可以将粘贴的格式列表。|  
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|将新条目添加到受支持的剪贴板格式的列表。|  
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|添加**CF_BITMAP**， **CF_DIB**， `CF_METAFILEPICT`，和 （可选）`CF_LINKSOURCE`您的应用程序可以将粘贴到格式的列表。|  
|[COlePasteSpecialDialog::CreateItem](#createitem)|使用指定的格式到容器文档中创建一个项。|  
|[COlePasteSpecialDialog::DoModal](#domodal)|显示 OLE 选择性粘贴对话框。|  
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|设置是项以图标形式绘制。|  
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标的窗体关联的图元文件的句柄。|  
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|获取用户选择可用粘贴选项的索引。|  
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|获取所选内容的类型。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[COlePasteSpecialDialog::m_ps](#m_ps)|类型的结构**OLEUIPASTESPECIAL**控制对话框中的函数。|  
  
## <a name="remarks"></a>备注  
 创建类的对象`COlePasteSpecialDialog`当你想要调用此对话框。 之后`COlePasteSpecialDialog`构造对象，则可以使用[AddFormat](#addformat)和[AddStandardFormats](#addstandardformats)成员函数以添加到对话框中的剪贴板格式。 您还可以使用[m_ps](#m_ps)结构初始化的值或在对话框中的控件的状态。 `m_ps`结构属于类型**OLEUIPASTESPECIAL**。  
  
 有关详细信息，请参阅[OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxodlgs.h  
  
##  <a name="addformat"></a>COlePasteSpecialDialog::AddFormat  
 调用此函数可将新的格式添加到您的应用程序可以支持选择性粘贴操作中的格式的列表。  
  
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
 描述向用户格式的字符串。  
  
 *lpszResult*  
 描述结果，如果在对话框中选择这种格式的字符串。  
  
 `flags`  
 不同链接和嵌入选项可用于这种格式。 此标志是一个或多个中的不同值的按位组合**OLEUIPASTEFLAG**枚举类型。  
  
 `cf`  
 要添加的剪贴板格式。  
  
 *tymed*  
 在这种格式中可用的媒体类型。 这是一个或多个中的值的按位组合**TYMED**枚举类型。  
  
 `nFormatID`  
 用于标识此格式的字符串的 ID。 此字符串的格式为 \n 字符分隔的两个单独的字符串。 第一个字符串是相同将传入的*lpstrFormat*参数，并将第二个等同于*lpstrResult*参数。  
  
 *bEnableIcon*  
 确定是否已启用显示为图标复选框，在列表框中选择这种格式时的标志。  
  
 *闪烁*  
 确定在列表框中选择这种格式时，是否启用粘贴链接单选按钮的标志。  
  
### <a name="remarks"></a>备注  
 可以调用此函数以添加任一标准格式，例如**CF_TEXT**或**CF_TIFF**或您的应用程序已注册到系统的自定义格式。 有关将数据对象粘贴到您的应用程序的详细信息，请参阅文章[数据对象和数据源︰ 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227)枚举类型和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅[OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172)枚举类型中的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
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
 调用此函数可将以下剪贴板格式添加到您的应用程序可以支持选择性粘贴操作中的格式的列表︰  
  
```  
void AddStandardFormats(BOOL bEnableLink = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bEnableLink*  
 用于确定是否要添加的标志`CF_LINKSOURCE`您的应用程序可以将粘贴到格式的列表。  
  
### <a name="remarks"></a>备注  
  
- **CF_BITMAP**  
  
- **CF_DIB**  
  
- `CF_METAFILEPICT`  
  
- **"嵌入的对象"**  
  
-   （可选）**"源链接"**  
  
 这些格式用于支持嵌入对象和链接。  
  
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
 创建标记包含任意数量的使用按位或运算符组合在一起的以下标志︰  
  
- `PSF_SELECTPASTE`指定，在对话框中调用时最初检查粘贴单选按钮。 不能结合使用`PSF_SELECTPASTELINK`。 这是默认设置。  
  
- `PSF_SELECTPASTELINK`指定单选按钮将处于粘贴链接检查最初何时调用对话框。 不能结合使用`PSF_SELECTPASTE`。  
  
- `PSF_CHECKDISPLAYASICON`指定，在对话框中调用时最初检查显示为图标复选框。  
  
- `PSF_SHOWHELP`指定当调用对话框中，将显示帮助按钮。  
  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)进行粘贴。 如果此值为**NULL**，它将获取`COleDataObject`从剪贴板。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框中的父窗口设置为主应用程序窗口中。  
  
### <a name="remarks"></a>备注  
 此函数只构造`COlePasteSpecialDialog`对象。 若要显示对话框中，调用[DoModal](#domodal)函数。  
  
 有关详细信息，请参阅[OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172)枚举类型中的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="createitem"></a>COlePasteSpecialDialog::CreateItem  
 创建选择性粘贴对话框中选择了一个新项。  
  
```  
BOOL CreateItem(COleClientItem* pNewItem);
```  
  
### <a name="parameters"></a>参数  
 *pNewItem*  
 指向`COleClientItem`实例。 不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则在创建项否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数只应调用之后[DoModal](#domodal)返回**IDOK**。  
  
##  <a name="domodal"></a>COlePasteSpecialDialog::DoModal  
 显示 OLE 选择性粘贴对话框。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
- **IDOK**如果成功显示的对话框。  
  
- **IDCANCEL**如果用户已取消对话框。  
  
- **IDABORT**是否发生了错误。 如果**IDABORT**是返回，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能出现的错误的列表，请参阅[OleUIPasteSpecial](http://msdn.microsoft.com/library/windows/desktop/ms694512) ，此功能在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 如果您想要通过设置成员的初始化各种对话框控件[m_ps](#m_ps)结构中，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 如果`DoModal`返回**IDOK**，可调用其他成员函数来检索设置或用户的信息输入到对话框。  
  
##  <a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect  
 确定用户选择要以图标形式显示的选定的项。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现对象所需的方法。  
  
- `DVASPECT_CONTENT`返回解除对话框中时如果不检查显示为图标复选框。  
  
- `DVASPECT_ICON`返回解除对话框中时如果检查显示为图标复选框。  
  
### <a name="remarks"></a>备注  
 只调用此函数之后， [DoModal](#domodal)返回**IDOK**。  
  
 绘制方面的详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile  
 获取与用户选定的项关联的图元文件。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果通过选择解除对话框时选择了显示为图标复选框包含所选项目，该图标方面的图元文件的句柄**确定**; 否则为**NULL**。  
  
##  <a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex  
 获取索引值与此项关联选定的用户。  
  
```  
int GetPasteIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 转换的数组索引**OLEUIPASTEENTRY**用户选定的结构。 在执行粘贴操作时，应使用对应于所选索引的格式。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[OLEUIPASTEENTRY](http://msdn.microsoft.com/library/windows/desktop/ms690165)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType  
 确定用户所做的选择的类型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回类型所做选择。  
  
### <a name="remarks"></a>备注  
 返回类型值都由指定**选择**枚举类型中声明`COlePasteSpecialDialog`类。  
  
```  
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };  
```  
  
 请按照这些值的简短 desccriptions 操作︰  
  
- **COlePasteSpecialDialog::pasteLink**检查粘贴链接单选按钮和所选的格式使用了标准的 OLE 格式。  
  
- **COlePasteSpecialDialog::pasteNormal**检查粘贴单选按钮和所选的格式使用了标准的 OLE 格式。  
  
- **COlePasteSpecialDialog::pasteOther**所选的格式不是标准的 OLE 格式。  
  
- **COlePasteSpecialDialog::pasteStatic**所选的格式的图元文件。  
  
##  <a name="m_ps"></a>COlePasteSpecialDialog::m_ps  
 类型的结构**OLEUIPASTESPECIAL**用来控制选择性粘贴对话框中的行为。  
  
```  
OLEUIPASTESPECIAL m_ps;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)

