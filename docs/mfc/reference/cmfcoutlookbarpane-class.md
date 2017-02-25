---
title: "CMFCOutlookBarPane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCOutlookBarPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanBeRestored method"
  - "CMFCOutlookBarPane class"
  - "Dock method"
  - "IsChangeState method"
  - "OnBeforeFloat method"
  - "RestoreOriginalstate method"
  - "SmartUpdate method"
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCOutlookBarPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 控件从可插入到Outlook栏的 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) 派生的\([CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)）。  Outlook栏窗格包含用按钮的列。  用户可以移到该按钮上下的列表中，如果大于窗格。  当用户分离Outlook栏中的某个Outlook栏窗格，它在主框架窗口可以浮动或停靠。  
  
## 语法  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|默认构造函数。|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCOutlookBarPane::AddButton](../Topic/CMFCOutlookBarPane::AddButton.md)|将一个按钮添加到Outlook栏窗格。|  
|[CMFCOutlookBarPane::CanBeAttached](../Topic/CMFCOutlookBarPane::CanBeAttached.md)|确定窗格是否可以停靠到另一个窗格或框架窗口。  （重写 [CBasePane::CanBeAttached](../Topic/CBasePane::CanBeAttached.md)。）|  
|`CMFCOutlookBarPane::CanBeRestored`|确定系统是否能还原工具栏到其原始状态在自定义项之后。  （重写 [CMFCToolBar::CanBeRestored](../Topic/CMFCToolBar::CanBeRestored.md)。）|  
|[CMFCOutlookBarPane::ClearAll](../Topic/CMFCOutlookBarPane::ClearAll.md)|释放图像的资源在Outlook栏窗格。|  
|[CMFCOutlookBarPane::Create](../Topic/CMFCOutlookBarPane::Create.md)|创建Outlook栏窗格。|  
|`CMFCOutlookBarPane::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|`CMFCOutlookBarPane::Dock`|调用由框架停靠Outlook栏窗格。（重写 `CPane::Dock`。）|  
|[CMFCOutlookBarPane::EnablePageScrollMode](../Topic/CMFCOutlookBarPane::EnablePageScrollMode.md)|按按钮指定在Outlook栏窗格的卷动箭头是否提升按钮列表通过页，或。|  
|[CMFCOutlookBarPane::GetRegularColor](../Topic/CMFCOutlookBarPane::GetRegularColor.md)|返回Outlook栏窗格的规则\(非选定的文本颜色。）|  
|`CMFCOutlookBarPane::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCOutlookBarPane::IsBackgroundTexture](../Topic/CMFCOutlookBarPane::IsBackgroundTexture.md)|确定是否为Outlook栏窗格加载的背景图像。|  
|`CMFCOutlookBarPane::IsChangeState`|确定一个浮动窗格是否可以停靠。  （重写 `CPane::IsChangeState`。）|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](../Topic/CMFCOutlookBarPane::IsDrawShadedHighlight.md)|确定按钮边框是否被隐藏，当按钮显示，背景图像显示。|  
|`CMFCOutlookBarPane::OnBeforeFloat`|调用由结构，当窗格将浮动。  （重写 [CPane::OnBeforeFloat](../Topic/CPane::OnBeforeFloat.md)。）|  
|[CMFCOutlookBarPane::RemoveButton](../Topic/CMFCOutlookBarPane::RemoveButton.md)|移除具有指定的命令ID.的按钮|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|还原工具栏的原始状态。  （重写 [CMFCToolBar::RestoreOriginalState](../Topic/CMFCToolBar::RestoreOriginalState.md)。）|  
|[CMFCOutlookBarPane::SetBackColor](../Topic/CMFCOutlookBarPane::SetBackColor.md)|设置背景颜色。|  
|[CMFCOutlookBarPane::SetBackImage](../Topic/CMFCOutlookBarPane::SetBackImage.md)|设置背景图像。|  
|[CMFCOutlookBarPane::SetDefaultState](../Topic/CMFCOutlookBarPane::SetDefaultState.md)|重置Outlook栏窗格对原始项的一组按钮。|  
|[CMFCOutlookBarPane::SetExtraSpace](../Topic/CMFCOutlookBarPane::SetExtraSpace.md)|将按钮周围使用的填充的像素数目在Outlook栏窗格。|  
|[CMFCOutlookBarPane::SetTextColor](../Topic/CMFCOutlookBarPane::SetTextColor.md)|设置规则和显示的文本的颜色在Outlook栏窗格中。|  
|[CMFCOutlookBarPane::SetTransparentColor](../Topic/CMFCOutlookBarPane::SetTransparentColor.md)|设置Outlook栏窗格的透明的颜色。|  
|`CMFCOutlookBarPane::SmartUpdate`|在内部用于更新Outlook栏。  （重写 `CMFCToolBar::SmartUpdate`。）|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](../Topic/CMFCOutlookBarPane::EnableContextMenuItems.md)|指定要快捷菜单项在自定义模式下显示。|  
|[CMFCOutlookBarPane::RemoveAllButtons](../Topic/CMFCOutlookBarPane::RemoveAllButtons.md)|从Outlook栏窗格中移除所有按钮。  （重写 [CMFCToolBar::RemoveAllButtons](../Topic/CMFCToolBar::RemoveAllButtons.md)。）|  
  
## 备注  
 有关如何实现Outlook栏的信息，请参见 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 有关Outlook栏的示例，请参见OutlookDemo示例项目。  
  
## 示例  
 下面的示例演示如何使用 `CMFCOutlookBarPane` 选件类中的各种方法。  此示例演示如何创建Outlook栏窗格中，起始页scroll模式，启用停靠，并将Outlook栏的背景色。  此代码段是 [Outlook多视图示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/CPP/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/CPP/cmfcoutlookbarpane-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## 要求  
 **标头:** afxoutlookbarpane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)