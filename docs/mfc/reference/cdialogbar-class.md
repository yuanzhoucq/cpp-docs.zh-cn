---
title: CDialogBar 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
dev_langs:
- C++
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7dbb2d8202e9b87d2825b7d40a0dde4323246aa0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdialogbar-class"></a>CDialogBar 类
提供控件条中的 Windows 无模式对话框功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CDialogBar : public CControlBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDialogBar::CDialogBar](#cdialogbar)|构造 `CDialogBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDialogBar::Create](#create)|创建 Windows 对话栏并将其附加到`CDialogBar`对象。|  
  
## <a name="remarks"></a>备注  
 对话栏类似于一个对话框，其中包含用户可以使用 tab 键之间的标准 Windows 控件。 另一种相似性就创建对话框模板来表示对话栏。  
  
 创建和使用对话栏是类似于创建和使用`CFormView`对象。 首先，使用[对话框编辑器](../../windows/dialog-editor.md)定义具有样式的对话框模板**WS_CHILD**和任何其他样式。 模板必须没有样式**WS_VISIBLE**。 在应用程序代码中，调用构造函数来构造`CDialogBar`对象，然后调用**创建**可新建对话栏窗口并将其附加到`CDialogBar`对象。  
  
 有关详细信息`CDialogBar`，请参阅文章[对话栏](../../mfc/dialog-bars.md)和[技术说明 31](../../mfc/tn031-control-bars.md)，控件条。  
  
> [!NOTE]
>  在当前版本中，`CDialogBar`对象不能承载 Windows 窗体控件。 有关 Visual c + + 的 Windows 窗体控件的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## <a name="requirements"></a>要求  
 **标头：** afxext.h  
  
##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar  
 构造 `CDialogBar` 对象。  
  
```  
CDialogBar();
```  
  
##  <a name="create"></a>  CDialogBar::Create  
 加载指定的对话框资源模板`lpszTemplateName`或`nIDTemplate`、 创建对话栏窗口、 设置其样式，和将其与关联`CDialogBar`对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
virtual BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向父`CWnd`对象。  
  
 `lpszTemplateName`  
 指向的目录名称`CDialogBar`对象的对话框资源模板。  
  
 `nStyle`  
 工具栏样式中。 支持的其他工具栏样式包括：  
  
- `CBRS_TOP` 控件条是在框架窗口的顶部。  
  
- `CBRS_BOTTOM` 控件条是在框架窗口的底部。  
  
- `CBRS_NOALIGN` 父级调整大小时，将不会重新定位控件条。  
  
- `CBRS_TOOLTIPS` 控件栏会显示工具提示。  
  
- **CBRS_SIZE_DYNAMIC**控件条是动态的。  
  
- **CBRS_SIZE_FIXED**固定的控件条。  
  
- **CBRS_FLOATING**浮点控件条。  
  
- `CBRS_FLYBY` 状态栏会显示有关该按钮的信息。  
  
- **CBRS_HIDE_INPLACE**控件条不向用户显示。  
  
 `nID`  
 对话栏控件 ID。  
  
 `nIDTemplate`  
 资源 ID`CDialogBar`对象的对话框模板。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果指定`CBRS_TOP`或`CBRS_BOTTOM`对齐样式，对话栏的宽度是框架窗口和窗体的高度是指定的资源`nIDTemplate`。 如果指定`CBRS_LEFT`或`CBRS_RIGHT`对齐样式，对话栏的高度是框架窗口，并且其宽度是指定的资源的`nIDTemplate`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CTRLBARS](../../visual-cpp-samples.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFormView 类](../../mfc/reference/cformview-class.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)
