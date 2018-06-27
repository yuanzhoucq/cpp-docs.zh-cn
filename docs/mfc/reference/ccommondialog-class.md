---
title: CCommonDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
dev_langs:
- C++
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53f53bdb19c6f40d73179b600051ecfaf6b69c94
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950630"
---
# <a name="ccommondialog-class"></a>CCommonDialog 类
封装 Windows 公共对话框功能的类的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CCommonDialog : public CDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CCommonDialog::CCommonDialog](#ccommondialog)|构造 `CCommonDialog` 对象。|  
  
## <a name="remarks"></a>备注  
 下列类能封装 Windows 公共对话框功能：  
  
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
 **标头：** afxdlgs.h  
  
##  <a name="ccommondialog"></a>  CCommonDialog::CCommonDialog  
 构造 `CCommonDialog` 对象。  
  
```  
explicit CCommonDialog(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>参数  
 *pParentWnd*  
 指向父或所有者窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为应用程序主窗口。  
  
### <a name="remarks"></a>备注  
 请参阅[CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog)的完整信息。  
  
## <a name="see-also"></a>请参阅  
 [CDialog 类](../../mfc/reference/cdialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)   
 [CFontDialog 类](../../mfc/reference/cfontdialog-class.md)   
 [CColorDialog 类](../../mfc/reference/ccolordialog-class.md)   
 [CPageSetupDialog 类](../../mfc/reference/cpagesetupdialog-class.md)   
 [CPrintDialog 类](../../mfc/reference/cprintdialog-class.md)   
 [CFindReplaceDialog 类](../../mfc/reference/cfindreplacedialog-class.md)   
 [COleDialog 类](../../mfc/reference/coledialog-class.md)
