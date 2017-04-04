---
title: "COleInsertDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- OLE Insert Object dialog box
- dialog boxes, OLE
- COleInsertDialog class
- Insert Object dialog box
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
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
ms.openlocfilehash: 078f421dacc79ff929249cd35c520b0c4d4a222e
ms.lasthandoff: 02/24/2017

---
# <a name="coleinsertdialog-class"></a>COleInsertDialog 类
用于 OLE“插入对象”对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|构造 `COleInsertDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleInsertDialog::CreateItem](#createitem)|创建在对话框中选择的项。|  
|[COleInsertDialog::DoModal](#domodal)|显示 OLE 插入对象对话框。|  
|[COleInsertDialog::GetClassID](#getclassid)|获取**CLSID**与选定的项相关联。|  
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|指示是否绘制为一个图标的项。|  
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标的窗体关联的图元文件的句柄。|  
|[COleInsertDialog::GetPathName](#getpathname)|获取在该对话框中选择的文件的完整路径。|  
|[COleInsertDialog::GetSelectionType](#getselectiontype)|获取所选对象的类型。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[COleInsertDialog::m_io](#m_io)|类型的结构**OLEUIINSERTOBJECT**控制对话框中的行为。|  
  
## <a name="remarks"></a>备注  
 创建类的对象`COleInsertDialog`当你想要调用此对话框。 之后`COleInsertDialog`构造对象，则可以使用[m_io](#m_io)结构初始化的值或在对话框中的控件的状态。 `m_io`结构属于类型**OLEUIINSERTOBJECT**。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此类。  
  
 有关详细信息，请参阅[OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
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
 **标头︰** afxodlgs.h  
  
##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog  
 此函数只构造`COleInsertDialog`对象。  
  
```  
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 创建包含以下值，以使用按位或运算符组合任意数量的标记︰  
  
- **IOF_SHOWHELP**指定对话框中调用时，将显示帮助按钮。  
  
- **IOF_SELECTCREATENEW**指定是否在对话框中调用时最初选择创建新的单选按钮。 这是默认值，不能与使用**IOF_SELECTCREATEFROMFILE**。  
  
- **IOF_SELECTCREATEFROMFILE**指定是否在对话框中调用时最初选择从文件创建单选按钮。 不能与使用**IOF_SELECTCREATENEW**。  
  
- **IOF_CHECKLINK**指定，在对话框中调用时最初检查链接复选框。  
  
- **IOF_DISABLELINK**指定对话框中调用时，将禁用链接复选框。  
  
- **IOF_CHECKDISPLAYASICON**将最初选中了显示为图标复选框，将显示当前图标，并且将启用更改图标按钮，当调用对话框中的指定。  
  
- **IOF_VERIFYSERVERSEXIST**指定对话框中，应验证它将添加到列表框通过确保注册数据库中指定的服务器，显示的对话框之前存在的类。 将此标志设置会显著降低性能。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为主应用程序窗口中。  
  
### <a name="remarks"></a>备注  
 若要显示对话框中，调用[DoModal](#domodal)函数。  
  
##  <a name="createitem"></a>COleInsertDialog::CreateItem  
 调用此函数可创建类型的对象[COleClientItem](../../mfc/reference/coleclientitem-class.md)才[DoModal](#domodal)返回**IDOK**。  
  
```  
BOOL CreateItem(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向要创建的项。  
  
### <a name="return-value"></a>返回值  
 非零，如果项目的创建时间;否则为 0。  
  
### <a name="remarks"></a>备注  
 您必须分配`COleClientItem`对象，然后才能调用此函数。  
  
##  <a name="domodal"></a>COleInsertDialog::DoModal  
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
  
 `COleInsertDialog::DocObjectsOnly`将插入仅 DocObjects。  
  
 `COleInsertDialog::ControlsOnly`将插入只有 ActiveX 控件。  
  
 DocObject 和 ActiveX 控件无法将插入零。 此值会导致相同的实现的第一个原型如上所列。  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
-   如果成功显示的对话框，IDOK。  
  
-   如果用户已取消对话框中的 IDCANCEL。  
  
-   IDABORT 是否发生了错误。 如果返回 IDABORT，调用[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型的详细信息。 有关可能出现的错误的列表，请参阅[OleUIInsertObject](http://msdn.microsoft.com/library/windows/desktop/ms694325) ，此功能在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 如果您想要通过设置成员的初始化各种对话框控件[m_io](#m_io)结构中，应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
 如果`DoModal`返回 IDOK，可调用其他成员函数来检索这些设置，或者由用户对话框中的信息输入。  
  
##  <a name="getclassid"></a>COleInsertDialog::GetClassID  
 调用此函数可获取**CLSID**与选定的项仅当关联[DoModal](#domodal)返回**IDOK**并且所选内容类型为**COleInsertDialog::createNewItem**。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回**CLSID**与所选项目相关联。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect  
 调用此函数可确定用户选择要以图标形式显示的选定的项。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现对象所需的方法。  
  
- `DVASPECT_CONTENT`返回不已检查显示为图标复选框。  
  
- `DVASPECT_ICON`返回已选中了显示为图标复选框。  
  
### <a name="remarks"></a>备注  
 调用此函数仅当[DoModal](#domodal)返回**IDOK**。  
  
 绘制方面的详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)数据结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile  
 调用此函数可获取包含所选的项的图标方面的图元文件的句柄。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>返回值  
 检查显示为图标复选框是否包含所选项目，该图标方面的图元文件句柄，当对话框已关闭通过选择**确定**; 否则为**NULL**。  
  
##  <a name="getpathname"></a>COleInsertDialog::GetPathName  
 调用此函数可获取选定的文件才的完整路径[DoModal](#domodal)返回**IDOK**并且所选内容类型不是**COleInsertDialog::createNewItem**。  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>返回值  
 在对话框中选择文件的完整路径。 如果所选内容类型为`createNewItem`，此函数将返回毫无意义`CString`在发布模式下或在调试模式下引发断言。  
  
##  <a name="getselectiontype"></a>COleInsertDialog::GetSelectionType  
 调用此函数可获取选定内容类型选择插入对象对话框中时通过选择解除**确定**。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>返回值  
 所做选择的类型。  
  
### <a name="remarks"></a>备注  
 返回类型值都由指定**选择**枚举类型中声明`COleInsertDialog`类。  
  
```  
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };  
```  
  
 请按照这些值的简短说明︰  
  
- **COleInsertDialog::createNewItem**选择创建新的单选按钮。  
  
- **COleInsertDialog::insertFromFile**已选择从文件创建单选按钮和链接复选框未被选中。  
  
- **COleInsertDialog::linkToFile**已选择从文件创建单选按钮和链接复选框已选中。  
  
##  <a name="m_io"></a>COleInsertDialog::m_io  
 类型的结构**OLEUIINSERTOBJECT**用来控制插入对象对话框中的行为。  
  
```  
OLEUIINSERTOBJECT m_io;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)

