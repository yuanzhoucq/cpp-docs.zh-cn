---
title: COleChangeIconDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
dev_langs:
- C++
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a67b1e405f1e3be472f9b9b3b5ebe00be3fb8a5d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041040"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog 类
用于 OLE“更改图标”对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|构造 `COleChangeIconDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|执行在对话框中指定的更改。|  
|[COleChangeIconDialog::DoModal](#domodal)|OLE 2 更改图标对话框中显示。|  
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项图标窗体关联的图元文件的句柄。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleChangeIconDialog::m_ci](#m_ci)|结构，它控制的对话框中的行为。|  
  
## <a name="remarks"></a>备注  
 创建类的对象`COleChangeIconDialog`如果想要调用此对话框。 后`COleChangeIconDialog`构造对象，则可以使用[m_ci](#m_ci)结构初始化的值或在对话框中的控件的状态。 `m_ci`结构属于类型**OLEUICHANGEICON**。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。  
  
 有关详细信息，请参阅[OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) Windows SDK 中的结构。  
  
 关于 OLE 特定对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeIconDialog`  
  
## <a name="requirements"></a>要求  
 **标头：** afxodlgs.h  
  
##  <a name="colechangeicondialog"></a>  COleChangeIconDialog::COleChangeIconDialog  
 此函数仅构造`COleChangeIconDialog`对象。  
  
```  
explicit COleChangeIconDialog(
    COleClientItem* pItem,  
    DWORD dwFlags = CIF_SELECTCURRENT,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pItem*  
 指向要转换的项。  
  
 *dwFlags*  
 使用的按位组合起来，创建标志，其中包含任意数量的以下值-或运算符：  
  
- **CIF_SELECTCURRENT**指定，在调用对话框时最初选择当前的单选按钮。 这是默认设置。  
  
- **CIF_SELECTDEFAULT**指定，在调用对话框时最初选择的默认单选按钮。  
  
- **CIF_SELECTFROMFILE**指定，在调用对话框时最初选择文件中的单选按钮。  
  
- **CIF_SHOWHELP**指定调用对话框中时，将显示帮助按钮。  
  
- **CIF_USEICONEXE**指定应从中指定的可执行文件中提取图标**szIconExe**字段[m_ci](#m_ci)而不是检索的类型。 这可用于嵌入或链接到非 OLE 文件。  
  
 *pParentWnd*  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框中的父窗口将设置为应用程序主窗口。  
  
### <a name="remarks"></a>备注  
 若要显示对话框中，调用[DoModal](#domodal)函数。  
  
 有关详细信息，请参阅[OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) Windows SDK 中的结构。  
  
##  <a name="dochangeicon"></a>  COleChangeIconDialog::DoChangeIcon  
 调用此函数可更改到对话框后中选定的一个表示项的图标[DoModal](#domodal)返回**IDOK**。  
  
```  
BOOL DoChangeIcon(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 *pItem*  
 指向以更改其图标的项。  
  
### <a name="return-value"></a>返回值  
 如果更改成功; 则为非 0否则为 0。  
  
##  <a name="domodal"></a>  COleChangeIconDialog::DoModal  
 调用此函数可显示 OLE 更改图标对话框。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
- **IDOK**如果成功显示该对话框。  
  
- **IDCANCEL**如果用户已取消对话框。  
  
- **IDABORT**如果发生错误。 如果**IDABORT**是返回，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型详细信息。 有关可能的错误的列表，请参阅[OleUIChangeIcon](http://msdn.microsoft.com/library/windows/desktop/ms688307) Windows SDK 中的函数。  
  
### <a name="remarks"></a>备注  
 如果你想要通过设置成员的初始化各种对话框控件[m_ci](#m_ci)结构，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 如果`DoModal`返回**IDOK**，您可以调用其他成员函数检索的设置或由用户输入到对话框中的信息。  
  
##  <a name="geticonicmetafile"></a>  COleChangeIconDialog::GetIconicMetafile  
 调用此函数可获取包含所选的项的图标化方面的图元文件的句柄。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果通过选择解除对话框中包含的新建图标，图标化方面的图元文件的句柄**确定**; 否则为在显示对话框之前, 已作为它的图标。  
  
##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci  
 类型的结构**OLEUICHANGEICON**用于控制更改图标对话框中的行为。  
  
```  
OLEUICHANGEICON m_ci;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) Windows SDK 中的结构。  
  
## <a name="see-also"></a>请参阅  
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)
