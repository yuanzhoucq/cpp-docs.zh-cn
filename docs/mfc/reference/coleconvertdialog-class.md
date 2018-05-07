---
title: COleConvertDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
dev_langs:
- C++
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90453d4e8550038493545b691c978b59bda90fad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 类
有关详细信息，请参阅[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) Windows SDK 中的结构。  
  
## <a name="syntax"></a>语法  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|构造 `COleConvertDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleConvertDialog::DoConvert](#doconvert)|执行在对话框中指定的转换。|  
|[COleConvertDialog::DoModal](#domodal)|OLE 更改项对话框中显示。|  
|[COleConvertDialog::GetClassID](#getclassid)|获取**CLSID**与选定的项关联。|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|指定是否要绘制项作为图标。|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项图标窗体关联的图元文件的句柄。|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|获取所选内容的类型。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|结构，它控制的对话框中的行为。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此类。  
  
 关于 OLE 特定对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## <a name="requirements"></a>要求  
 **标头：** afxodlgs.h  
  
##  <a name="coleconvertdialog"></a>  COleConvertDialog::COleConvertDialog  
 仅构造`COleConvertDialog`对象。  
  
```  
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向要转换或激活的项。  
  
 `dwFlags`  
 使用的按位组合起来，创建标志，其中包含任意数量的以下值-或运算符：  
  
- **CF_SELECTCONVERTTO**指定，在调用对话框时最初选择的转换为单选按钮。 这是默认设置。  
  
- **CF_SELECTACTIVATEAS**指定，在调用对话框时最初选择激活单选按钮。  
  
- **CF_SETCONVERTDEFAULT**指定类其**CLSID**指定**clsidConvertDefault**的成员`m_cv`结构将用作默认选择类列表中选中框时转换为单选按钮。  
  
- **CF_SETACTIVATEDEFAULT**指定类其**CLSID**指定**clsidActivateDefault**的成员`m_cv`结构将用作默认值当选中激活单选按钮时的类列表框中选择。  
  
- **CF_SHOWHELPBUTTON**指定调用对话框中时，将显示帮助按钮。  
  
 `pClassID`  
 指向要转换或激活的项的 CLSID。 如果**NULL**、 **CLSID**与关联`pItem`将使用。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框中的父窗口设置为应用程序主窗口。  
  
### <a name="remarks"></a>备注  
 若要显示对话框中，调用[DoModal](#domodal)函数。  
  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)和[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657)结构。  
  
##  <a name="doconvert"></a>  COleConvertDialog::DoConvert  
 从已成功返回后，调用此函数， [DoModal](#domodal)要转换或要激活的对象类型， [COleClientItem](../../mfc/reference/coleclientitem-class.md)。  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向要转换或激活的项。 不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 转换或激活根据选择的转换对话框中的用户的信息项。  
  
##  <a name="domodal"></a>  COleConvertDialog::DoModal  
 调用此函数可显示 OLE 转换对话框。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
- **IDOK**如果成功显示该对话框。  
  
- **IDCANCEL**如果用户已取消对话框。  
  
- **IDABORT**如果发生错误。 如果**IDABORT**是返回，调用[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型详细信息。 有关可能的错误的列表，请参阅[OleUIConvert](http://msdn.microsoft.com/library/windows/desktop/ms680694) Windows SDK 中的函数。  
  
### <a name="remarks"></a>备注  
 如果你想要通过设置成员的初始化各种对话框控件[m_cv](#m_cv)结构，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 如果`DoModal`返回**IDOK**，您可以调用其他成员函数检索的设置或由用户输入到对话框中的信息。  
  
##  <a name="getclassid"></a>  COleConvertDialog::GetClassID  
 调用此函数可获取**CLSID**与项关联的转换对话框中选定的用户。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>返回值  
 **CLSID**与已在转换对话框中选定的项的关联。  
  
### <a name="remarks"></a>备注  
 调用此函数后，才[DoModal](#domodal)返回**IDOK**。  
  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getdrawaspect"></a>  COleConvertDialog::GetDrawAspect  
 调用此函数可确定是否在用户选择以图标形式显示的选定的项。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现对象所需的方法。  
  
- `DVASPECT_CONTENT` 返回如果未选中显示为图标复选框。  
  
- `DVASPECT_ICON` 返回如果已选中了显示为图标复选框。  
  
### <a name="remarks"></a>备注  
 调用此函数后，才[DoModal](#domodal)返回**IDOK**。  
  
 绘制方面的详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的数据结构。  
  
##  <a name="geticonicmetafile"></a>  COleConvertDialog::GetIconicMetafile  
 调用此函数可获取包含所选的项的图标化方面的图元文件的句柄。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果显示为图标复选框已包含的选定项的图标化方面的图元文件的句柄检查时通过选择解除对话框**确定**; 否则为**NULL**。  
  
##  <a name="getselectiontype"></a>  COleConvertDialog::GetSelectionType  
 调用此函数可确定的转换转换对话框中选定的类型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>返回值  
 所做选择的类型。  
  
### <a name="remarks"></a>备注  
 通过指定返回类型值**选择**枚举类型中声明`COleConvertDialog`类。  
  
```  
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };  
```  
  
 请按照这些值的简要说明操作：  
  
- **COleConvertDialog::noConversion**返回如果则对话框中已取消或用户选择任何转换。 如果`COleConvertDialog::DoModal`返回**IDOK**，很可能用户选择不同于以前选择的图标。  
  
- **COleConvertDialog::convertItem**返回用户如果已选中转换为单选按钮，选择不同的项要转换到的和`DoModal`返回**IDOK**。  
  
- **COleConvertDialog::activateAs**返回用户如果已选中激活单选按钮，选择不同的项，若要激活，和`DoModal`返回**IDOK**。  
  
##  <a name="m_cv"></a>  COleConvertDialog::m_cv  
 类型的结构**OLEUICONVERT**用于控制转换对话框中的行为。  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) Windows SDK 中的结构。  
  
## <a name="see-also"></a>请参阅  
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)
