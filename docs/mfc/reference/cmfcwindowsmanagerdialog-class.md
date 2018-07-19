---
title: CMFCWindowsManagerDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b5ae46280a537577ae3e3ab0fbdf73f2e449e58
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042091"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog 类
`CMFCWindowsManagerDialog`对象使用户能够管理 MDI 子窗口的 MDI 应用程序中。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCWindowsManagerDialog : public CDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|构造 `CMFCWindowsManagerDialog` 对象。|  
  
## <a name="remarks"></a>备注  
 `CMFCWindowsManagerDialog`包含应用程序中当前打开的 MDI 子窗口的列表。 通过使用此对话框中，用户可以手动控制 MDI 子窗口的状态。  
  
 `CMFCWindowsManagerDialog` 嵌入到内部[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)。 `CMFCWindowsManagerDialog`不应手动创建的类。 而应调用该函数[CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)，然后它将创建并显示`CMFCWindowsManagerDialog`对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCWindowsManagerDialog`对象通过调用`CMDIFrameWndEx::ShowWindowsDialog`。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxWindowsManagerDialog.h  
  
##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog  
 构造[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)对象。  
  
```  
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,  
    BOOL bHelpButton = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*pMDIFrame*  
 指向父或所有者窗口的指针。  
  
 [in]*bHelpButton*  
 布尔参数可指定是否显示框架**帮助**按钮。  
  
### <a name="remarks"></a>备注  
 有关视觉管理器的详细信息，请参阅[可视化管理器](../../mfc/visualization-manager.md)。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)
