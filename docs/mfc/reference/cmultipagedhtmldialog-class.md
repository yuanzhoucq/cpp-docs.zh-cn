---
title: CMultiPageDHtmlDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
dev_langs:
- C++
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1a4ca77e4b7a2cda10d87bd657e73931a50612
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038001"
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog 类
多页对话框按顺序显示多个 HTML 页并处理每页中的事件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|构造多页 （向导式） DHTML 对话框对象。|  
|[CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|销毁多页 DHTML 对话框对象。|  
  
## <a name="remarks"></a>备注  
 执行此操作的机制是[DHTML 和 URL 事件映射](dhtml-event-maps.md)，其中包含嵌入事件映射为每个页。  
  
## <a name="example"></a>示例  
 此多页对话框假定定义简单的向导类似功能的三个 HTML 资源。 第一页具有`Next`按钮，第二个**Prev**和`Next`按钮和第三个**Prev**按钮。 按下的按钮之一时，处理程序函数调用[CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource)以加载相应的新页面。  
  
 （中 CMyMultiPageDlg.h) 的类声明的相关部分：  
  
 [!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]  
  
 （在 CMyMultipageDlg.cpp) 中的类实现的相关部分：  
  
 [!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)  
  
 `CMultiPageDHtmlDialog`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdhtml.h  
  
##  <a name="cmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog::CMultiPageDHtmlDialog  
 构造多页 （向导式） DHTML 对话框对象。  
  
```  
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,  
    LPCTSTR szHtmlResID = NULL,  
    CWnd* pParentWnd = NULL);

 
CMultiPageDHtmlDialog(
    UINT nIDTemplate,  
    UINT nHtmlResID = 0,  
    CWnd* pParentWnd = NULL);  
  
CMultiPageDHtmlDialog();
```  
  
### <a name="parameters"></a>参数  
 *lpszTemplateName*  
 以 null 结尾的字符串，表示对话框模板资源的名称。  
  
 *szHtmlResID*  
 以 null 结尾的字符串，表示一个 HTML 资源的名称。  
  
 *pParentWnd*  
 指向父或所有者窗口对象的指针 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为应用程序主窗口。  
  
 *nIDTemplate*  
 包含对话框模板资源的 ID 号。  
  
 *nHtmlResID*  
 包含一个 HTML 资源的 ID 号。  
  
##  <a name="_dtorcmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog  
 销毁多页 DHTML 对话框对象。  
  
```  
virtual ~CMultiPageDHtmlDialog();
```  
  
## <a name="see-also"></a>请参阅  
 [CDHtmlDialog 类](../../mfc/reference/cdhtmldialog-class.md)
