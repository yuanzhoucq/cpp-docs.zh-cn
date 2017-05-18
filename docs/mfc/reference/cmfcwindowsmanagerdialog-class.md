---
title: "CMFCWindowsManagerDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCWindowsManagerDialog class
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
caps.latest.revision: 25
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 9f1508cfd3844fed413edd69063f1b3e64e80195
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog 类
`CMFCWindowsManagerDialog`对象使用户能够管理 MDI 应用程序中的 MDI 子窗口。  
  
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
  
 `CMFCWindowsManagerDialog`嵌入到内部[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)。 `CMFCWindowsManagerDialog`不是您应手动创建的类。 而应调用该函数[CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)，然后它将创建并显示`CMFCWindowsManagerDialog`对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCWindowsManagerDialog`对象通过调用`CMDIFrameWndEx::ShowWindowsDialog`。 此代码段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&18;](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxWindowsManagerDialog.h  
  
##  <a name="cmfcwindowsmanagerdialog"></a>CMFCWindowsManagerDialog::CMFCWindowsManagerDialog  
 构造[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)对象。  
  
```  
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,  
    BOOL bHelpButton = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMDIFrame`  
 指向父窗口或所有者窗口的指针。  
  
 [in] `bHelpButton`  
 一个布尔型参数，指定是否显示框架**帮助**按钮。  
  
### <a name="remarks"></a>备注  
 视觉管理器的详细信息，请参阅[可视化管理器](../../mfc/visualization-manager.md)。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)

