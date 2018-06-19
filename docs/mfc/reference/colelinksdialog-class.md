---
title: COleLinksDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e190c8b8cb11fefccb2847214dcaebf713f35dc4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368964"
---
# <a name="colelinksdialog-class"></a>COleLinksDialog 类
用于 OLE“编辑链接”对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class COleLinksDialog : public COleDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|构造 `COleLinksDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleLinksDialog::DoModal](#domodal)|显示 OLE 编辑链接对话框。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleLinksDialog::m_el](#m_el)|类型的结构**OLEUIEDITLINKS**控制对话框中的行为。|  
  
## <a name="remarks"></a>备注  
 创建类的对象`COleLinksDialog`如果想要调用此对话框。 后`COleLinksDialog`构造对象，则可以使用[m_el](#m_el)结构初始化的值或在对话框中的控件的状态。 `m_el`结构属于类型**OLEUIEDITLINKS**。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此类。  
  
 有关详细信息，请参阅[OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) Windows SDK 中的结构。  
  
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
 **标头：** afxodlgs.h  
  
##  <a name="domodal"></a>  COleLinksDialog::DoModal  
 显示 OLE 编辑链接对话框。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
- **IDOK**如果成功显示该对话框。  
  
- **IDCANCEL**如果用户已取消对话框。  
  
- **IDABORT**如果发生错误。 如果**IDABORT**是返回，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型详细信息。 有关可能的错误的列表，请参阅[OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) Windows SDK 中的函数。  
  
### <a name="remarks"></a>备注  
 如果你想要通过设置成员的初始化各种对话框控件[m_el](#m_el)结构，你应执行此操作，然后再调`DoModal`，但在构造对话框对象之后。  
  
##  <a name="colelinksdialog"></a>  COleLinksDialog::COleLinksDialog  
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
 指向 OLE 文档包含要编辑的链接。  
  
 `pView`  
 指向上的当前视图`pDoc`。  
  
 `dwFlags`  
 创建标记，其中包含 0 或**ELF_SHOWHELP**以指定是否显示对话框中时，将显示帮助按钮。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框中的父窗口设置为应用程序主窗口。  
  
### <a name="remarks"></a>备注  
 此函数仅构造`COleLinksDialog`对象。 若要显示对话框中，调用[DoModal](#domodal)函数。  
  
##  <a name="m_el"></a>  COleLinksDialog::m_el  
 类型的结构**OLEUIEDITLINKS**用于控制编辑链接对话框中的行为。  
  
```  
OLEUIEDITLINKS m_el;  
```  
  
### <a name="remarks"></a>备注  
 直接或通过成员函数，则可以修改此结构的成员。  
  
 有关详细信息，请参阅[OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) Windows SDK 中的结构。  
  
## <a name="see-also"></a>请参阅  
 [COleDialog 类](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)
