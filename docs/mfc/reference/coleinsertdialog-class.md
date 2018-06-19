---
title: COleInsertDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
dev_langs:
- C++
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 041b707bec58abeb19617fbfd275428ca2cf67e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374876"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog 类
用于 OLE“插入对象”对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|构造 `COleInsertDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleInsertDialog::CreateItem](#createitem)|创建在对话框中选定的项。|  
|[COleInsertDialog::DoModal](#domodal)|显示 OLE 插入对象对话框。|  
|[COleInsertDialog::GetClassID](#getclassid)|获取**CLSID**与选定的项关联。|  
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|指示是否绘制为图标的项。|  
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项图标窗体关联的图元文件的句柄。|  
|[COleInsertDialog::GetPathName](#getpathname)|获取对话框中选择的文件的完整路径。|  
|[COleInsertDialog::GetSelectionType](#getselectiontype)|获取所选对象的类型。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleInsertDialog::m_io](#m_io)|类型的结构**OLEUIINSERTOBJECT**控制对话框中的行为。|  
  
## <a name="remarks"></a>备注  
 创建类的对象`COleInsertDialog`如果想要调用此对话框。 后`COleInsertDialog`构造对象，则可以使用[m_io](#m_io)结构初始化的值或在对话框中的控件的状态。 `m_io`结构属于类型**OLEUIINSERTOBJECT**。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此类。  
  
 有关详细信息，请参阅[OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) Windows SDK 中的结构。  
  
 有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleInsertDialog`  
  
## <a name="requirements"></a>要求  
 **标头：** afxodlgs.h  
  
##  <a name="coleinsertdialog"></a>  COleInsertDialog::COleInsertDialog  
 此函数仅构造`COleInsertDialog`对象。  
  
```  
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 创建包含任意数量的以下值，以使用按位 OR 运算符组合的标志：  
  
- **IOF_SHOWHELP**指定调用对话框中时，将显示帮助按钮。  
  
- **IOF_SELECTCREATENEW**指定，在调用对话框时最初选择创建新的单选按钮。 这是默认值，不能与使用**IOF_SELECTCREATEFROMFILE**。  
  
- **IOF_SELECTCREATEFROMFILE**指定，在调用对话框时最初选择从文件创建单选按钮。 不能与使用**IOF_SELECTCREATENEW**。  
  
- **IOF_CHECKLINK**指定，在调用对话框时最初检查链接复选框。  
  
- **IOF_DISABLELINK**指定调用对话框中时，将禁用链接复选框。  
  
- **IOF_CHECKDISPLAYASICON**指定将最初选中了显示为图标复选框，将显示当前的图标，并调用对话框中时，将启用更改图标按钮。  
  
- **IOF_VERIFYSERVERSEXIST**指定对话框中，应验证它将添加到列表框通过确保注册数据库中指定的服务器，显示该对话框之前存在的类。 设置此标志会显著降低性能。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为应用程序主窗口。  
  
### <a name="remarks"></a>备注  
 若要显示对话框中，调用[DoModal](#domodal)函数。  
  
##  <a name="createitem"></a>  COleInsertDialog::CreateItem  
 调用此函数可创建类型的对象[COleClientItem](../../mfc/reference/coleclientitem-class.md)才[DoModal](#domodal)返回**IDOK**。  
  
```  
BOOL CreateItem(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向要创建的项。  
  
### <a name="return-value"></a>返回值  
 创建项; 如果非零否则为 0。  
  
### <a name="remarks"></a>备注  
 你必须将分配`COleClientItem`对象，然后您可以调用此函数。  
  
##  <a name="domodal"></a>  COleInsertDialog::DoModal  
 调用此函数可显示 OLE 插入对象对话框。  
  
```  
virtual INT_PTR   
    DoModal();

 
INT_PTR   
    DoModal(DWORD  dwFlags);
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 以下值之一：  
  
 `COleInsertDialog::DocObjectsOnly` 将插入仅 DocObjects。  
  
 `COleInsertDialog::ControlsOnly` 将插入仅 ActiveX 控件。  
  
 既不 DocObject，也不 ActiveX 控件，将插入零。 上面列出此值将导致返回中的第一个原型相同的实现。  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
-   如果成功显示该对话框，IDOK。  
  
-   如果用户已取消对话框中的 IDCANCEL。  
  
-   如果出现错误，IDABORT。 如果返回 IDABORT，调用[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型详细信息。 有关可能的错误的列表，请参阅[OleUIInsertObject](http://msdn.microsoft.com/library/windows/desktop/ms694325) Windows SDK 中的函数。  
  
### <a name="remarks"></a>备注  
 如果你想要通过设置成员的初始化各种对话框控件[m_io](#m_io)结构，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 如果`DoModal`返回 IDOK，您可以调用其他成员函数以检索设置或信息输入到用户对话框。  
  
##  <a name="getclassid"></a>  COleInsertDialog::GetClassID  
 调用此函数可获取**CLSID**与所选的项仅当关联[DoModal](#domodal)返回**IDOK**和所选内容类型是**COleInsertDialog::createNewItem**。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回**CLSID**与所选的项相关联。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getdrawaspect"></a>  COleInsertDialog::GetDrawAspect  
 调用此函数可确定是否用户选择了以图标形式显示的选定的项。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现对象所需的方法。  
  
- `DVASPECT_CONTENT` 返回如果未选中显示为图标复选框。  
  
- `DVASPECT_ICON` 返回如果已选中了显示为图标复选框。  
  
### <a name="remarks"></a>备注  
 调用此函数仅当[DoModal](#domodal)返回**IDOK**。  
  
 绘制方面的详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的数据结构。  
  
##  <a name="geticonicmetafile"></a>  COleInsertDialog::GetIconicMetafile  
 调用此函数可获取包含所选的项的图标化方面的图元文件的句柄。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果显示为图标复选框已包含的选定项的图标化方面的图元文件的句柄检查时通过选择解除对话框**确定**; 否则为**NULL**。  
  
##  <a name="getpathname"></a>  COleInsertDialog::GetPathName  
 调用此函数可获取选定的文件才的完整路径[DoModal](#domodal)返回**IDOK**和所选内容类型不是**COleInsertDialog::createNewItem**。  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>返回值  
 在对话框中选择文件的完整路径。 如果选择类型为`createNewItem`，此函数将返回无意义`CString`在发布模式下或在调试模式下，将导致断言。  
  
##  <a name="getselectiontype"></a>  COleInsertDialog::GetSelectionType  
 调用此函数可获取选定内容类型选择插入对象对话框中时通过选择解除**确定**。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>返回值  
 所做选择的类型。  
  
### <a name="remarks"></a>备注  
 通过指定返回类型值**选择**枚举类型中声明`COleInsertDialog`类。  
  
```  
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };  
```  
  
 请按照这些值的简要说明操作：  
  
- **COleInsertDialog::createNewItem**选择创建新的单选按钮。  
  
- **COleInsertDialog::insertFromFile**选择从文件创建单选按钮和链接复选框未选中。  
  
- **COleInsertDialog::linkToFile**选择从文件创建单选按钮和链接复选框已选中。  
  
##  <a name="m_io"></a>  COleInsertDialog::m_io  
 类型的结构**OLEUIINSERTOBJECT**用于控制插入对象对话框中的行为。  
  
```  
OLEUIINSERTOBJECT m_io;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) Windows SDK 中的结构。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)
