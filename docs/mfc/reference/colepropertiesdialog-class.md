---
title: "COlePropertiesDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
dev_langs:
- C++
helpviewer_keywords:
- OLE Object Properties dialog box
- Object Properties dialog box
- dialog boxes, OLE
- OLE documents, modifying properties
- property pages, OLE
- COlePropertiesDialog class
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0c07766bca6bbc546f877e10255d80bd388d30d7
ms.lasthandoff: 02/24/2017

---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog 类
封装 Windows 公共 OLE“对象属性”对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class COlePropertiesDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|构造 `COlePropertiesDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COlePropertiesDialog::DoModal](#domodal)|显示对话框中，并允许用户进行选择。|  
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|当文档项的缩放发生更改时由框架调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COlePropertiesDialog::m_gp](#m_gp)|若要初始化的"常规"页中使用的结构`COlePropertiesDialog`对象。|  
|[COlePropertiesDialog::m_lp](#m_lp)|若要初始化的"链接"页中使用的结构`COlePropertiesDialog`对象。|  
|[COlePropertiesDialog::m_op](#m_op)|一个用于初始化结构`COlePropertiesDialog`对象。|  
|[COlePropertiesDialog::m_psh](#m_psh)|用于添加其他自定义属性页的结构。|  
|[COlePropertiesDialog::m_vp](#m_vp)|若要自定义的"视图"页中使用的结构`COlePropertiesDialog`对象。|  
  
## <a name="remarks"></a>备注  
 常见的 OLE 对象属性对话框中可以方便地显示和修改 OLE 文档项与 Windows 标准一致的方式的属性。 这些属性及其他，包括表示文档项，以便在项目的链接上显示的图标和图像缩放，及信息 （如果该项目链接） 的选项的文件的信息。  
  
 若要使用`COlePropertiesDialog`对象，请首先创建对象使用`COlePropertiesDialog`构造函数。 对话框中已经过构造后，调用`DoModal`成员函数以显示对话框中，并让用户能够修改项的任何属性。 `DoModal`返回用户是否选择了确定 ( **IDOK**) 或取消 ( **IDCANCEL**) 按钮。 除了确定和取消按钮，还有一个应用按钮。 当用户选择应用时，对文档项的属性所做的任何更改都应用到的项和其图像会自动更新，但仍处于活动状态。  
  
 [M_psh](#m_psh)数据成员是一个指向**PROPSHEETHEADER**结构，并且在大多数情况下不需要显式地对其进行访问。 一个例外是当您需要默认的常规、 视图和链接页之外的附加属性页。 在这种情况下，您可以修改`m_psh`数据成员，以包括自定义页面之前，先调用`DoModal`成员函数。  
  
 OLE 对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxodlgs.h  
  
##  <a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog  
 创建一个 `COlePropertiesDialog` 对象。  
  
```  
COlePropertiesDialog(
    COleClientItem* pItem,  
    UINT nScaleMin = 10,  
    UINT nScaleMax = 500,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向正在访问其属性的文档项的指针。  
  
 *nScaleMin*  
 最小缩放比例为文档项图像的百分比。  
  
 *nScaleMax*  
 最大缩放比例为文档项图像的百分比。  
  
 `pParentWnd`  
 一个指针，指向对话框中的父或所有者。  
  
### <a name="remarks"></a>备注  
 派生公共 OLE 对象属性对话框类从`COlePropertiesDialog`为了实现扩展以供您的文档项。 实现此类的实例的任何对话框将不支持的文档项的缩放比例。  
  
 默认情况下，公共 OLE 对象属性对话框中有三个默认页︰  
  
-   常规  
  
     此页包含所选的文档项表示的文件名的系统信息。 从此页中，用户可以将所选的项目转换为另一种类型。  
  
-   视图  
  
     此页包含用于显示项、 更改该图标，以及更改图像的缩放选项。  
  
-   Link  
  
     此页包含用于更改链接的项的位置和更新链接的项目的选项。 从此页中，用户可以断开所选的项的链接。  
  
 若要添加页面之外提供默认情况下，修改[m_psh](#m_psh)成员变量的构造函数在退出之前您`COlePropertiesDialog`的派生类。 这是高级的实现`COlePropertiesDialog`构造函数。  
  
##  <a name="domodal"></a>COlePropertiesDialog::DoModal  
 调用该成员函数以显示 Windows 公共 OLE 对象属性对话框中，并让用户能够查看和/或更改文档项的各种属性。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 **IDOK**或**IDCANCEL**如果成功; 否则为 0。 **IDOK**和**IDCANCEL**是常数，指示用户是否选择了确定或取消按钮。  
  
 如果**IDCANCEL**返回，则可以调用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定是否发生了错误。  
  
##  <a name="m_gp"></a>COlePropertiesDialog::m_gp  
 类型的结构[OLEUIGNRLPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687297)，可用来初始化 OLE 对象属性对话框中的常规页。  
  
```  
OLEUIGNRLPROPS m_gp;  
```  
  
### <a name="remarks"></a>备注  
 此页显示的类型和大小的一个嵌入，并允许用户对转换对话框中的访问权限。 此页还显示链接目标的对象是否为链接。  
  
 有关详细信息**OLEUIGNRLPROPS**结构，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_lp"></a>COlePropertiesDialog::m_lp  
 类型的结构[OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735)，可用来初始化 OLE 对象属性对话框中的链接页。  
  
```  
OLEUILINKPROPS m_lp;  
```  
  
### <a name="remarks"></a>备注  
 此页显示的链接项的位置，并允许用户更新或中断，项的链接。  
  
 有关详细信息**OLEUILINKPROPS**结构，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_op"></a>COlePropertiesDialog::m_op  
 类型的结构[OLEUIOBJECTPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687199)，可用来初始化公共 OLE 对象属性对话框。  
  
```  
OLEUIOBJECTPROPS m_op;  
```  
  
### <a name="remarks"></a>备注  
 此结构包含用来初始化的常规、 链接和视图页的成员。  
  
 有关详细信息，请参阅**OLEUIOBJECTPROPS**和[OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735)中结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_psh"></a>COlePropertiesDialog::m_psh  
 类型的结构[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)，其成员存储对话框对象的特征。  
  
```  
PROPSHEETHEADER m_psh;  
```  
  
### <a name="remarks"></a>备注  
 在构造之后`COlePropertiesDialog`对象，可以使用`m_psh`设置之前，先调用对话框中的各个方面`DoModal`成员函数。  
  
 如果您修改`m_psh`数据成员，直接将覆盖任何默认行为。  
  
 有关详细信息**PROPSHEETHEADER**结构，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_vp"></a>COlePropertiesDialog::m_vp  
 类型的结构[OLEUIVIEWPROPS](http://msdn.microsoft.com/library/windows/desktop/ms693751)，可用来初始化 OLE 对象属性对话框中的视图页。  
  
```  
OLEUIVIEWPROPS m_vp;  
```  
  
### <a name="remarks"></a>备注  
 此页面允许用户切换"内容"和"图标"视图的对象，并更改其容器内缩放比例。 当以图标形式显示该对象时，它还允许用户对更改图标对话框中的访问权限。  
  
 有关详细信息**OLEUIVIEWPROPS**结构，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale  
 已更改的缩放值，且选择了确定或应用时由框架调用。  
  
```  
virtual BOOL OnApplyScale(
    COleClientItem* pItem,  
    int nCurrentScale,  
    BOOL bRelativeToOrig);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向正在访问其属性的文档项的指针。  
  
 `nCurrentScale`  
 对话框刻度的数字值。  
  
 *bRelativeToOrig*  
 指示缩放是适用于原始文档项的大小。  
  
### <a name="return-value"></a>返回值  
 非零，如果已处理。否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。 必须重写此函数可启用缩放控件。  
  
> [!NOTE]
>  公共 OLE 对象属性对话框中显示之前，框架将调用此函数与**NULL**为`pItem`，– 1 表示`nCurrentScale`。 这样做是为了确定是否应启用缩放控件。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CIRC](../../visual-cpp-samples.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage 类](../../mfc/reference/cpropertypage-class.md)

