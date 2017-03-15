---
title: "COleConvertDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleConvertDialog
dev_langs:
- C++
helpviewer_keywords:
- COleConvertDialog class
- OLE Convert dialog box
- dialog boxes, OLE
- OLE dialog boxes, Convert
- Convert dialog box
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
caps.latest.revision: 22
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
ms.openlocfilehash: 6db5caf443e7f71c58e2c65b46794c2c9d246d38
ms.lasthandoff: 02/24/2017

---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 类
有关详细信息，请参阅[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="syntax"></a>语法  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|构造 `COleConvertDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleConvertDialog::DoConvert](#doconvert)|执行在对话框中指定的转换。|  
|[COleConvertDialog::DoModal](#domodal)|显示 OLE 更改项对话框。|  
|[COleConvertDialog::GetClassID](#getclassid)|获取**CLSID**与选定的项相关联。|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|指定是否要绘制项作为图标。|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标的窗体关联的图元文件的句柄。|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|获取所选内容的类型。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|一种结构，用于控制对话框中的行为。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此类。  
  
 关于特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxodlgs.h  
  
##  <a name="a-namecoleconvertdialoga--coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog  
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
 使用按位组合起来，创建标记，其中包含任意数量的以下值-或运算符︰  
  
- **CF_SELECTCONVERTTO**指定是否在对话框中调用时最初选择转换为单选按钮。 这是默认设置。  
  
- **CF_SELECTACTIVATEAS**指定是否在对话框中调用时最初选择激活单选按钮。  
  
- **CF_SETCONVERTDEFAULT**指定类的**CLSID**由指定**clsidConvertDefault**的成员`m_cv`转换为单选按钮处于选中状态时，将为默认选择的类列表框中使用结构。  
  
- **CF_SETACTIVATEDEFAULT**指定类的**CLSID**由指定**clsidActivateDefault**的成员`m_cv`结构将用作默认选择的类列表框中，选择激活单选按钮时。  
  
- **CF_SHOWHELPBUTTON**指定对话框中调用时，将显示帮助按钮。  
  
 `pClassID`  
 指向要转换或激活的项的 CLSID。 如果**NULL**、 **CLSID**与关联`pItem`将使用。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框中的父窗口设置为主应用程序窗口中。  
  
### <a name="remarks"></a>备注  
 若要显示对话框中，调用[DoModal](#domodal)函数。  
  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)和[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657)结构。  
  
##  <a name="a-namedoconverta--coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvertDialog::DoConvert  
 在从成功返回后调用此函数， [DoModal](#domodal)，将转换或要激活的对象类型[COleClientItem](../../mfc/reference/coleclientitem-class.md)。  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向要转换或激活的项。 不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 转换项目，或将其激活根据用户在转换对话框中选择的信息。  
  
##  <a name="a-namedomodala--coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvertDialog::DoModal  
 调用此函数可显示 OLE 转换对话框。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
- **IDOK**如果成功显示的对话框。  
  
- **IDCANCEL**如果用户已取消对话框。  
  
- **IDABORT**是否发生了错误。 如果**IDABORT**是返回，调用[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型的详细信息。 有关可能出现的错误的列表，请参阅[OleUIConvert](http://msdn.microsoft.com/library/windows/desktop/ms680694) ，此功能在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 如果您想要通过设置成员的初始化各种对话框控件[m_cv](#m_cv)结构中，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 如果`DoModal`返回**IDOK**，可调用其他成员函数来检索的设置或由用户输入的对话框中的信息。  
  
##  <a name="a-namegetclassida--coleconvertdialoggetclassid"></a><a name="getclassid"></a>COleConvertDialog::GetClassID  
 调用此函数可获取**CLSID**与项关联在转换对话框中选定的用户。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>返回值  
 **CLSID**与在转换对话框中选定的项相关联。  
  
### <a name="remarks"></a>备注  
 调用此函数仅在后[DoModal](#domodal)返回**IDOK**。  
  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdrawaspecta--coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect  
 调用此函数可确定是否在用户选择以图标形式显示的选定的项。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现对象所需的方法。  
  
- `DVASPECT_CONTENT`返回不已检查显示为图标复选框。  
  
- `DVASPECT_ICON`返回已选中了显示为图标复选框。  
  
### <a name="remarks"></a>备注  
 调用此函数仅在后[DoModal](#domodal)返回**IDOK**。  
  
 绘制方面的详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)数据结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegeticonicmetafilea--coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile  
 调用此函数可获取包含所选的项的图标方面的图元文件的句柄。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>返回值  
 检查显示为图标复选框是否包含所选项目，该图标方面的图元文件句柄，当对话框已关闭通过选择**确定**; 否则为**NULL**。  
  
##  <a name="a-namegetselectiontypea--coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvertDialog::GetSelectionType  
 调用此函数可确定的转换转换对话框中选择的类型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>返回值  
 所做选择的类型。  
  
### <a name="remarks"></a>备注  
 返回类型值都由指定**选择**枚举类型中声明`COleConvertDialog`类。  
  
 `enum Selection`  
  
 `{`  
  
 `noConversion,`  
  
 `convertItem,`  
  
 `activateAs`  
  
 `};`  
  
 请按照这些值的简短说明︰  
  
- **COleConvertDialog::noConversion**返回如果对话框中被取消，或在用户选择不进行转换。 如果`COleConvertDialog::DoModal`返回**IDOK**，就可能在用户选择个以前选择不同的图标。  
  
- **COleConvertDialog::convertItem**返回用户如果已选中转换为单选按钮，选择要转换到的不同的项和`DoModal`返回**IDOK**。  
  
- **COleConvertDialog::activateAs**返回用户如果已选中激活单选按钮，选择不同的项，若要激活，和`DoModal`返回**IDOK**。  
  
##  <a name="a-namemcva--coleconvertdialogmcv"></a><a name="m_cv"></a>COleConvertDialog::m_cv  
 类型的结构**OLEUICONVERT**用来控制转换对话框中的行为。  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)

