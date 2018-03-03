---
title: "COleUpdateDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 32a7d41c507c2b7b932ba33df911151bfc417091
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog 类
用于 OLE“编辑链接”对话框的特例，当你只需要更新文档中现有的链接对象或嵌入对象时才可使用。  
  
## <a name="syntax"></a>语法  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|构造 `COleUpdateDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleUpdateDialog::DoModal](#domodal)|显示**编辑链接**处于更新模式对话框。|  
  
## <a name="remarks"></a>备注  
 有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
 `COleUpdateDialog`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxodlgs.h  
  
##  <a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog  
 构造 `COleUpdateDialog` 对象。  
  
```  
explicit COleUpdateDialog(
    COleDocument* pDoc,  
    BOOL bUpdateLinks = TRUE,  
    BOOL bUpdateEmbeddings = FALSE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDoc`  
 指向包含可能需要更新的链接的文档。  
  
 *bUpdateLinks*  
 确定是否要更新链接的对象的标志。  
  
 *bUpdateEmbeddings*  
 确定是否要更新嵌入的对象的标志。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象所属。 如果它是**NULL**，对话框中的父窗口将设置为应用程序主窗口。  
  
### <a name="remarks"></a>备注  
 此函数仅构造`COleUpdateDialog`对象。 若要显示对话框中，调用[DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)。 此类应使用而不是`COleLinksDialog`如果想要更新仅现有链接或嵌入项。  
  
##  <a name="domodal"></a>COleUpdateDialog::DoModal  
 显示编辑链接对话框框中更新模式。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 对话框中的完成状态。 以下值之一：  
  
- **IDOK**如果对话框中成功返回。  
  
- **IDCANCEL**如果无当前文档中的链接或嵌入项需要更新。  
  
- **IDABORT**如果发生错误。 如果**IDABORT**是返回，调用[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型详细信息。 有关可能的错误的列表，请参阅[OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) Windows SDK 中的函数。  
  
### <a name="remarks"></a>备注  
 除非用户选择取消按钮，将更新所有链接和/或嵌入。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [COleLinksDialog 类](../../mfc/reference/colelinksdialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleLinksDialog 类](../../mfc/reference/colelinksdialog-class.md)
