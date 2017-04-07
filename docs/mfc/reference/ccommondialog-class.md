---
title: "CCommonDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], Windows common dialogs
- common dialog boxes [C++], common dialog classes
- common dialog classes [C++]
- MFC dialog boxes, Windows common dialogs
- Windows common dialogs [C++]
- CCommonDialog class
- dialog classes [C++], common
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
caps.latest.revision: 20
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
ms.openlocfilehash: 93d4cd4ca794095c225641bc67353b9a53080c3c
ms.lasthandoff: 02/24/2017

---
# <a name="ccommondialog-class"></a>CCommonDialog 类
封装 Windows 公共对话框功能的类的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CCommonDialog : public CDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CCommonDialog::CCommonDialog](#ccommondialog)|构造 `CCommonDialog` 对象。|  
  
## <a name="remarks"></a>备注  
 下列类封装 Windows 公共对话框的功能︰  
  
- [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
- [CFontDialog](../../mfc/reference/cfontdialog-class.md)  
  
- [CColorDialog](../../mfc/reference/ccolordialog-class.md)  
  
- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)  
  
- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)  
  
- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)  
  
- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)  
  
- [COleDialog](../../mfc/reference/coledialog-class.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CCommonDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdlgs.h  
  
##  <a name="ccommondialog"></a>CCommonDialog::CCommonDialog  
 构造 `CCommonDialog` 对象。  
  
```  
explicit CCommonDialog(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为主应用程序窗口中。  
  
### <a name="remarks"></a>备注  
 请参阅[CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog)的完整信息。  
  
## <a name="see-also"></a>另请参阅  
 [CDialog 类](../../mfc/reference/cdialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)   
 [CFontDialog 类](../../mfc/reference/cfontdialog-class.md)   
 [CColorDialog 类](../../mfc/reference/ccolordialog-class.md)   
 [CPageSetupDialog 类](../../mfc/reference/cpagesetupdialog-class.md)   
 [CPrintDialog 类](../../mfc/reference/cprintdialog-class.md)   
 [CFindReplaceDialog 类](../../mfc/reference/cfindreplacedialog-class.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)

