---
title: COlePropertiesDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 358798e3945378d0fa43fa6e2fa91d686212efab
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040176"
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog 类
封装 Windows 公共 OLE“对象属性”对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class COlePropertiesDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|构造 `COlePropertiesDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COlePropertiesDialog::DoModal](#domodal)|显示对话框中，并允许用户进行选择。|  
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|缩放的文档项的已更改时由框架调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COlePropertiesDialog::m_gp](#m_gp)|用于初始化的"常规"页的结构`COlePropertiesDialog`对象。|  
|[COlePropertiesDialog::m_lp](#m_lp)|用于初始化的"链接"页的结构`COlePropertiesDialog`对象。|  
|[COlePropertiesDialog::m_op](#m_op)|用于初始化的结构`COlePropertiesDialog`对象。|  
|[COlePropertiesDialog::m_psh](#m_psh)|使用以添加其他自定义属性页面的结构。|  
|[COlePropertiesDialog::m_vp](#m_vp)|用于自定义的"视图"页的结构`COlePropertiesDialog`对象。|  
  
## <a name="remarks"></a>备注  
 常见的 OLE 对象属性对话框中可以方便地显示和修改 OLE 文档项以与 Windows 标准一致的方式的属性。 这些属性及其他包括表示的文档项，用于在项的链接上显示的图标和缩放图像，及信息 （如果该项目链接） 的选项的文件的信息。  
  
 若要使用`COlePropertiesDialog`对象，请首先创建对象使用`COlePropertiesDialog`构造函数。 在构造对话框后，调用`DoModal`成员函数以显示对话框中，并允许用户修改项的任何属性。 `DoModal` 返回用户是否选择确定 ( **IDOK**) 或取消 ( **IDCANCEL**) 按钮。 除了确定按钮和取消按钮，没有应用按钮。 当用户选择应用时，对文档项的属性进行任何更改都应用到的项和其映像会自动更新，但将保持活动状态。  
  
 [M_psh](#m_psh)数据成员是一个指向**PROPSHEETHEADER**结构，在大多数情况下不需要显式访问。 一个例外是当你需要默认常规、 视图和链接页之外的其他属性页。 在这种情况下，你可以修改`m_psh`数据成员，以包括自定义页面之前调用`DoModal`成员函数。  
  
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
 **标头：** afxodlgs.h  
  
##  <a name="colepropertiesdialog"></a>  COlePropertiesDialog::COlePropertiesDialog  
 创建一个 `COlePropertiesDialog` 对象。  
  
```  
COlePropertiesDialog(
    COleClientItem* pItem,  
    UINT nScaleMin = 10,  
    UINT nScaleMax = 500,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pItem*  
 指向正在访问其属性的文档项的指针。  
  
 *nScaleMin*  
 最小缩放比例文档项图像的百分比。  
  
 *nScaleMax*  
 最大缩放比例文档项图像的百分比。  
  
 *pParentWnd*  
 对话框的父或所有者的指针。  
  
### <a name="remarks"></a>备注  
 派生您常用的 OLE 对象属性对话框类，从`COlePropertiesDialog`为了实现你的文档项的缩放比例。 此类的实例由实现任何对话框将不支持的文档项的缩放。  
  
 默认情况下，常见的 OLE 对象属性对话框中有三个默认页：  
  
-   常规  
  
     此页包含有关所选的文档项表示的文件系统信息。 从此页中，用户可以将选定的项转换为另一种类型。  
  
-   视图  
  
     此页包含用于显示项、 更改的图标和更改图像的缩放选项。  
  
-   链接  
  
     此页包含用于更改链接的项的位置和更新链接的项的选项。 从此页中，用户可以断开的选定项的链接。  
  
 若要添加之外提供的默认页，修改[m_psh](#m_psh)成员变量的构造函数在退出之前你`COlePropertiesDialog`-派生类。 这是的高级的实现`COlePropertiesDialog`构造函数。  
  
##  <a name="domodal"></a>  COlePropertiesDialog::DoModal  
 调用此成员函数，以显示 Windows 公共 OLE 对象属性对话框，并允许用户查看和/或更改的文档项的各种属性。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 **IDOK**或**IDCANCEL**如果成功; 否则为 0。 **IDOK**和**IDCANCEL**是指示用户是否选中确定或取消按钮的常量。  
  
 如果**IDCANCEL**返回，可以调用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定是否发生了错误。  
  
##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp  
 类型的结构[OLEUIGNRLPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687297)，可用来初始化 OLE 对象属性对话框中的常规页。  
  
```  
OLEUIGNRLPROPS m_gp;  
```  
  
### <a name="remarks"></a>备注  
 此页显示的类型和大小的嵌入，并允许对转换对话框中的用户访问权限。 此页还显示链接目标的对象是否是链接。  
  
 有关详细信息**OLEUIGNRLPROPS**结构，请参阅 Windows SDK。  
  
##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp  
 类型的结构[OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735)，可用来初始化 OLE 对象属性对话框中的链接页。  
  
```  
OLEUILINKPROPS m_lp;  
```  
  
### <a name="remarks"></a>备注  
 此页显示链接的项的位置，并允许用户更新或中断，项的链接。  
  
 有关详细信息**OLEUILINKPROPS**结构，请参阅 Windows SDK。  
  
##  <a name="m_op"></a>  COlePropertiesDialog::m_op  
 类型的结构[OLEUIOBJECTPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687199)，可用来初始化的常见的 OLE 对象属性对话框。  
  
```  
OLEUIOBJECTPROPS m_op;  
```  
  
### <a name="remarks"></a>备注  
 此结构还包含用于初始化的常规、 链接和视图页的成员。  
  
 有关详细信息，请参阅**OLEUIOBJECTPROPS**和[OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735) Windows SDK 中的结构。  
  
##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh  
 类型的结构[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)，其成员存储对话框对象的特征。  
  
```  
PROPSHEETHEADER m_psh;  
```  
  
### <a name="remarks"></a>备注  
 后构造`COlePropertiesDialog`对象时，可以使用`m_psh`设置对话框之前调用的各个方面`DoModal`成员函数。  
  
 如果你修改`m_psh`数据成员直接，您将重写任何默认行为。  
  
 有关详细信息**PROPSHEETHEADER**结构，请参阅 Windows SDK。  
  
##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp  
 类型的结构[OLEUIVIEWPROPS](http://msdn.microsoft.com/library/windows/desktop/ms693751)，可用来初始化 OLE 对象属性对话框中的视图页。  
  
```  
OLEUIVIEWPROPS m_vp;  
```  
  
### <a name="remarks"></a>备注  
 此页面允许用户切换"内容"和"图标"视图的对象，并更改其容器内缩放。 当以图标形式显示对象时，它还允许对更改图标对话框中的用户访问权限。  
  
 有关详细信息**OLEUIVIEWPROPS**结构，请参阅 Windows SDK。  
  
##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale  
 缩放值已经发生更改，并选择确定或应用，由框架调用。  
  
```  
virtual BOOL OnApplyScale(
    COleClientItem* pItem,  
    int nCurrentScale,  
    BOOL bRelativeToOrig);
```  
  
### <a name="parameters"></a>参数  
 *pItem*  
 指向正在访问其属性的文档项的指针。  
  
 *nCurrentScale*  
 对话框比例数字值。  
  
 *bRelativeToOrig*  
 指示缩放是适用于文档项的原始大小。  
  
### <a name="return-value"></a>返回值  
 如果处理; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。 你必须重写此函数可启用缩放控件。  
  
> [!NOTE]
>  常见的 OLE 对象属性对话框中将显示之前，框架调用此函数带**NULL**为*pItem*和 a-1 表示*nCurrentScale*。 这样做是为了确定是否应启用缩放控件。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CIRC](../../visual-cpp-samples.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage 类](../../mfc/reference/cpropertypage-class.md)
