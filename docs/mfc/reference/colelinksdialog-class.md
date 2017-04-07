---
title: "COleLinksDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
dev_langs:
- C++
helpviewer_keywords:
- Edit Links dialog box
- COleLinksDialog class
- dialog boxes, OLE
- OLE Edit Links dialog box
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ed256b3a4d3236863e3dcccb7614949f650f058b
ms.lasthandoff: 02/24/2017

---
# <a name="colelinksdialog-class"></a>COleLinksDialog 类
用于 OLE“编辑链接”对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class COleLinksDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|构造 `COleLinksDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleLinksDialog::DoModal](#domodal)|显示 OLE 编辑链接对话框。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[COleLinksDialog::m_el](#m_el)|类型的结构**OLEUIEDITLINKS**控制对话框中的行为。|  
  
## <a name="remarks"></a>备注  
 创建类的对象`COleLinksDialog`当你想要调用此对话框。 之后`COleLinksDialog`构造对象，则可以使用[m_el](#m_el)结构初始化的值或在对话框中的控件的状态。 `m_el`结构属于类型**OLEUIEDITLINKS**。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此类。  
  
 有关详细信息，请参阅[OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxodlgs.h  
  
##  <a name="domodal"></a>COleLinksDialog::DoModal  
 显示 OLE 编辑链接对话框。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
- **IDOK**如果成功显示的对话框。  
  
- **IDCANCEL**如果用户已取消对话框。  
  
- **IDABORT**是否发生了错误。 如果**IDABORT**是返回，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能出现的错误的列表，请参阅[OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) ，此功能在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 如果您想要通过设置成员的初始化各种对话框控件[m_el](#m_el)结构中，您应该这么做，然后再调`DoModal`，但在构造对话框对象之后。  
  
##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog  
 构造 `COleLinksDialog` 对象。  
  
```  
COleLinksDialog (
    COleDocument* pDoc,  
    CView* pView,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDoc`  
 指向包含要编辑的链接的 OLE 文档。  
  
 `pView`  
 与当前视图中的点数`pDoc`。  
  
 `dwFlags`  
 创建标记，其中包含 0 或**ELF_SHOWHELP**指定对话框中显示时是否将显示帮助按钮。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框中的父窗口设置为主应用程序窗口中。  
  
### <a name="remarks"></a>备注  
 此函数只构造`COleLinksDialog`对象。 若要显示对话框中，调用[DoModal](#domodal)函数。  
  
##  <a name="m_el"></a>COleLinksDialog::m_el  
 类型的结构**OLEUIEDITLINKS**用来控制编辑链接对话框中的行为。  
  
```  
OLEUIEDITLINKS m_el;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)

