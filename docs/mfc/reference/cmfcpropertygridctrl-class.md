---
title: "CMFCPropertyGridCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyGridCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridCtrl class"
  - "CMFCPropertyGridCtrl::accHitTest method"
  - "CMFCPropertyGridCtrl::accLocation method"
  - "CMFCPropertyGridCtrl::get_accChild method"
  - "CMFCPropertyGridCtrl::get_accDefaultAction method"
  - "CMFCPropertyGridCtrl::get_accDescription method"
  - "CMFCPropertyGridCtrl::get_accName method"
  - "CMFCPropertyGridCtrl::get_accRole method"
  - "CMFCPropertyGridCtrl::get_accState method"
  - "CMFCPropertyGridCtrl::get_accValue method"
  - "CMFCPropertyGridCtrl::PreTranslateMessage method"
ms.assetid: 95877cae-2311-4a2a-9031-0c8c3cf0a5f9
caps.latest.revision: 35
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPropertyGridCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 支持可以公开属性按字母或分层顺序的可编辑属性网格控件。  
  
## 语法  
  
```  
class CMFCPropertyGridCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](../Topic/CMFCPropertyGridCtrl::CMFCPropertyGridCtrl.md)|构造 `CMFCPropertyGridCtrl` 对象。|  
|`CMFCPropertyGridCtrl::~CMFCPropertyGridCtrl`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCPropertyGridCtrl::accHitTest`|调用由框架来检索子元素或子对象中给出的点在屏幕上。  （重写 [CWnd::accHitTest](../Topic/CWnd::accHitTest.md)。）|  
|`CMFCPropertyGridCtrl::accLocation`|调用由框架检索指定对象的当前屏幕位置。  （重写 [CWnd::accLocation](../Topic/CWnd::accLocation.md)。）|  
|[CMFCPropertyGridCtrl::accSelect](../Topic/CMFCPropertyGridCtrl::accSelect.md)|调用由框架修改选择或移动指定对象的键盘焦点。  （重写 [CWnd::accSelect](../Topic/CWnd::accSelect.md)。）|  
|[CMFCPropertyGridCtrl::AddProperty](../Topic/CMFCPropertyGridCtrl::AddProperty.md)|添加新的属性到属性网格控件。|  
|[CMFCPropertyGridCtrl::AlwaysShowUserToolTip](../Topic/CMFCPropertyGridCtrl::AlwaysShowUserToolTip.md)||  
|[CMFCPropertyGridCtrl::CloseColorPopup](../Topic/CMFCPropertyGridCtrl::CloseColorPopup.md)|关闭颜色选择对话框。|  
|[CMFCPropertyGridCtrl::Create](../Topic/CMFCPropertyGridCtrl::Create.md)|创建一个属性网格控件并将它附加到属性网格控件对象。|  
|[CMFCPropertyGridCtrl::DeleteProperty](../Topic/CMFCPropertyGridCtrl::DeleteProperty.md)|从属性网格控件删除所指定的属性。|  
|[CMFCPropertyGridCtrl::DrawControlBarColors](../Topic/CMFCPropertyGridCtrl::DrawControlBarColors.md)||  
|[CMFCPropertyGridCtrl::EnableDescriptionArea](../Topic/CMFCPropertyGridCtrl::EnableDescriptionArea.md)|启用或禁用在属性列表中显示的标题区。|  
|[CMFCPropertyGridCtrl::EnableHeaderCtrl](../Topic/CMFCPropertyGridCtrl::EnableHeaderCtrl.md)|启用或禁用标头控件在属性网格控件的顶部。|  
|[CMFCPropertyGridCtrl::EnsureVisible](../Topic/CMFCPropertyGridCtrl::EnsureVisible.md)|将一个属性网格控件并展开属性项，直到所指定的属性可见。|  
|[CMFCPropertyGridCtrl::ExpandAll](../Topic/CMFCPropertyGridCtrl::ExpandAll.md)|展开或折叠所有属性网格控件节点。|  
|[CMFCPropertyGridCtrl::FindItemByData](../Topic/CMFCPropertyGridCtrl::FindItemByData.md)|检索与一个用户定义的 `DWORD` 值的属性。|  
|`CMFCPropertyGridCtrl::get_accChild`|调用由框架检索一 `IDispatch` 接口的地址指定的子级。  （重写 [CWnd::get\_accChild](../Topic/CWnd::get_accChild.md)。）|  
|[CMFCPropertyGridCtrl::get\_accChildCount](../Topic/CMFCPropertyGridCtrl::get_accChildCount.md)|调用由框架检索属于该对象的子级的数目。  （重写 [CWnd::get\_accChildCount](../Topic/CWnd::get_accChildCount.md)。）|  
|`CMFCPropertyGridCtrl::get_accDefaultAction`|调用由框架检索描述对象的默认事件的字符串。  （重写 [CWnd::get\_accDefaultAction](../Topic/CWnd::get_accDefaultAction.md)。）|  
|`CMFCPropertyGridCtrl::get_accDescription`|调用由框架检索描述指定对象的可视外观的字符串。  （重写 [CWnd::get\_accDescription](../Topic/CWnd::get_accDescription.md)。）|  
|[CMFCPropertyGridCtrl::get\_accFocus](../Topic/CMFCPropertyGridCtrl::get_accFocus.md)|调用由框架检索具有键盘焦点的对象。  （重写 [CWnd::get\_accFocus](../Topic/CWnd::get_accFocus.md)。）|  
|[CMFCPropertyGridCtrl::get\_accHelp](../Topic/CMFCPropertyGridCtrl::get_accHelp.md)|调用由框架检索对象的 `Help` 特性字符串。  （重写 [CWnd::get\_accHelp](../Topic/CWnd::get_accHelp.md)。）|  
|[CMFCPropertyGridCtrl::get\_accHelpTopic](../Topic/CMFCPropertyGridCtrl::get_accHelpTopic.md)|调用由框架检索 `WinHelp`文件的完整路径与指定的对象和适当的主题的标识符在该文件中。  （重写 [CWnd::get\_accHelpTopic](../Topic/CWnd::get_accHelpTopic.md)。）|  
|[CMFCPropertyGridCtrl::get\_accKeyboardShortcut](../Topic/CMFCPropertyGridCtrl::get_accKeyboardShortcut.md)|调用由框架检索指定对象的热键或访问键。  （重写 [CWnd::get\_accKeyboardShortcut](../Topic/CWnd::get_accKeyboardShortcut.md)。）|  
|`CMFCPropertyGridCtrl::get_accName`|调用由框架检索指定对象的名称。  （重写 [CWnd::get\_accName](../Topic/CWnd::get_accName.md)。）|  
|`CMFCPropertyGridCtrl::get_accRole`|调用由框架检索描述指定对象的角色信息。  （重写 [CWnd::get\_accRole](../Topic/CWnd::get_accRole.md)。）|  
|[CMFCPropertyGridCtrl::get\_accSelection](../Topic/CMFCPropertyGridCtrl::get_accSelection.md)|调用由框架检索此对象的选定的子级。  （重写 [CWnd::get\_accSelection](../Topic/CWnd::get_accSelection.md)。）|  
|`CMFCPropertyGridCtrl::get_accState`|调用由框架检索指定对象的当前状态。  （重写 [CWnd::get\_accState](../Topic/CWnd::get_accState.md)。）|  
|`CMFCPropertyGridCtrl::get_accValue`|调用由框架检索指定对象的值。  （重写 [CWnd::get\_accValue](../Topic/CWnd::get_accValue.md)。）|  
|[CMFCPropertyGridCtrl::GetBkColor](../Topic/CMFCPropertyGridCtrl::GetBkColor.md)|检索当前属性网格控件的背景色。|  
|[CMFCPropertyGridCtrl::GetBoldFont](../Topic/CMFCPropertyGridCtrl::GetBoldFont.md)|检索当前属性网格控件的文本以粗体样式的Windows字体。|  
|[CMFCPropertyGridCtrl::GetCurSel](../Topic/CMFCPropertyGridCtrl::GetCurSel.md)|检索当前所选的属性。|  
|[CMFCPropertyGridCtrl::GetCustomColors](../Topic/CMFCPropertyGridCtrl::GetCustomColors.md)|检索为属性网格控件元素当前定义的自定义颜色。|  
|[CMFCPropertyGridCtrl::GetDescriptionHeight](../Topic/CMFCPropertyGridCtrl::GetDescriptionHeight.md)|检索声明区域的高度位于属性网格控件的底部。|  
|[CMFCPropertyGridCtrl::GetDescriptionRows](../Topic/CMFCPropertyGridCtrl::GetDescriptionRows.md)|在当前属性网格控件的声明范围中检索行数。|  
|[CMFCPropertyGridCtrl::GetHeaderCtrl](../Topic/CMFCPropertyGridCtrl::GetHeaderCtrl.md)|检索框架使用显示当前属性网格控件的内部 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) 对象。|  
|[CMFCPropertyGridCtrl::GetHeaderHeight](../Topic/CMFCPropertyGridCtrl::GetHeaderHeight.md)|检索属性网格控件标头的高度。|  
|[CMFCPropertyGridCtrl::GetLeftColumnWidth](../Topic/CMFCPropertyGridCtrl::GetLeftColumnWidth.md)|检索当前属性网格控件的左边的列的宽度，包含每个属性的名称。|  
|[CMFCPropertyGridCtrl::GetListRect](../Topic/CMFCPropertyGridCtrl::GetListRect.md)|检索属性网格控件的边框。|  
|[CMFCPropertyGridCtrl::GetProperty](../Topic/CMFCPropertyGridCtrl::GetProperty.md)|检索指向对应于属性网格控件项的指定索引的属性对象。|  
|[CMFCPropertyGridCtrl::GetPropertyColumnWidth](../Topic/CMFCPropertyGridCtrl::GetPropertyColumnWidth.md)|检索包含属性值"列中的当前宽度。|  
|[CMFCPropertyGridCtrl::GetPropertyCount](../Topic/CMFCPropertyGridCtrl::GetPropertyCount.md)|检索属性数。属性网格控件中。|  
|[CMFCPropertyGridCtrl::GetRowHeight](../Topic/CMFCPropertyGridCtrl::GetRowHeight.md)|检索行的高度在属性网格控件中。|  
|[CMFCPropertyGridCtrl::GetScrollBarCtrl](../Topic/CMFCPropertyGridCtrl::GetScrollBarCtrl.md)|检索指向在属性网格控件的滚动条控件。  （重写 [CWnd::GetScrollBarCtrl](../Topic/CWnd::GetScrollBarCtrl.md)。）|  
|[CMFCPropertyGridCtrl::GetTextColor](../Topic/CMFCPropertyGridCtrl::GetTextColor.md)|检索属性项文本的颜色在当前属性网格控件中。|  
|`CMFCPropertyGridCtrl::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCPropertyGridCtrl::HitTest](../Topic/CMFCPropertyGridCtrl::HitTest.md)|检索指向对应于属性网格控件项目的属性对象，如果指定的点在项目。  此方法还指明了在包含该点的属性网格控件的区域。|  
|[CMFCPropertyGridCtrl::InitHeader](../Topic/CMFCPropertyGridCtrl::InitHeader.md)|初始化框架使用显示当前属性网格控件的内部 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) 对象。|  
|[CMFCPropertyGridCtrl::IsAlphabeticMode](../Topic/CMFCPropertyGridCtrl::IsAlphabeticMode.md)|指示属性网格控件是否在"按字母顺序显示模式。|  
|[CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip](../Topic/CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip.md)||  
|[CMFCPropertyGridCtrl::IsDescriptionArea](../Topic/CMFCPropertyGridCtrl::IsDescriptionArea.md)|指示属性网格控件的声明范围是否显示。|  
|[CMFCPropertyGridCtrl::IsGroupNameFullWidth](../Topic/CMFCPropertyGridCtrl::IsGroupNameFullWidth.md)|指示每个属性组名称是否可以在当前属性网格控件的宽度显示。|  
|[CMFCPropertyGridCtrl::IsHeaderCtrl](../Topic/CMFCPropertyGridCtrl::IsHeaderCtrl.md)|指示标头控件是否显示。|  
|[CMFCPropertyGridCtrl::IsMarkModifiedProperties](../Topic/CMFCPropertyGridCtrl::IsMarkModifiedProperties.md)|指示属性网格控件如何显示经过修改的属性。|  
|[CMFCPropertyGridCtrl::IsShowDragContext](../Topic/CMFCPropertyGridCtrl::IsShowDragContext.md)|指示框架是否重绘当前属性网格控件的名称和值"列中，当用户调整列。|  
|[CMFCPropertyGridCtrl::IsVSDotNetLook](../Topic/CMFCPropertyGridCtrl::IsVSDotNetLook.md)|指示属性网格控件的外观是否在使用.NET的样式。|  
|[CMFCPropertyGridCtrl::MarkModifiedProperties](../Topic/CMFCPropertyGridCtrl::MarkModifiedProperties.md)|指定如何显示已修改的属性。|  
|`CMFCPropertyGridCtrl::PreTranslateMessage`|用于使选件类 [CWinApp](../../mfc/reference/cwinapp-class.md) 转换窗口消息，并在调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前。  （重写 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。）|  
|[CMFCPropertyGridCtrl::RemoveAll](../Topic/CMFCPropertyGridCtrl::RemoveAll.md)|从属性网格控件中移除所有属性对象。|  
|[CMFCPropertyGridCtrl::ResetOriginalValues](../Topic/CMFCPropertyGridCtrl::ResetOriginalValues.md)|还原所有属性的初始值。|  
|[CMFCPropertyGridCtrl::SetAlphabeticMode](../Topic/CMFCPropertyGridCtrl::SetAlphabeticMode.md)|设置或重置字母的模式。|  
|[CMFCPropertyGridCtrl::SetBoolLabels](../Topic/CMFCPropertyGridCtrl::SetBoolLabels.md)|指定布尔值标签文本。|  
|[CMFCPropertyGridCtrl::SetCurSel](../Topic/CMFCPropertyGridCtrl::SetCurSel.md)|选择在属性网格控件的属性。|  
|[CMFCPropertyGridCtrl::SetCustomColors](../Topic/CMFCPropertyGridCtrl::SetCustomColors.md)|为各个属性网格控件元素指定自定义颜色。|  
|[CMFCPropertyGridCtrl::SetDescriptionRows](../Topic/CMFCPropertyGridCtrl::SetDescriptionRows.md)|在当前属性网格控件的声明部分指定要显示。|  
|[CMFCPropertyGridCtrl::SetGroupNameFullWidth](../Topic/CMFCPropertyGridCtrl::SetGroupNameFullWidth.md)|指定是否显示全角类别名称属性的一组在当前属性网格控件中。|  
|[CMFCPropertyGridCtrl::SetListDelimiter](../Topic/CMFCPropertyGridCtrl::SetListDelimiter.md)|定义要用作分隔符在属性列表中的字符。|  
|[CMFCPropertyGridCtrl::SetShowDragContext](../Topic/CMFCPropertyGridCtrl::SetShowDragContext.md)|指定框架是否重绘当前属性网格控件的名称和值"列中，当用户调整列。|  
|[CMFCPropertyGridCtrl::SetVSDotNetLook](../Topic/CMFCPropertyGridCtrl::SetVSDotNetLook.md)|设置属性网格控件的外观用于与.NET的样式。|  
|[CMFCPropertyGridCtrl::UpdateColor](../Topic/CMFCPropertyGridCtrl::UpdateColor.md)|将当前选定的颜色属性的颜色值。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCPropertyGridCtrl::AdjustLayout](../Topic/CMFCPropertyGridCtrl::AdjustLayout.md)|重绘属性网格控件及其属性。|  
|[CMFCPropertyGridCtrl::CompareProps](../Topic/CMFCPropertyGridCtrl::CompareProps.md)|调用由属性网格控件对属性进行排序。|  
|[CMFCPropertyGridCtrl::EditItem](../Topic/CMFCPropertyGridCtrl::EditItem.md)|调用由结构，当用户开始修改属性。|  
|[CMFCPropertyGridCtrl::EndEditItem](../Topic/CMFCPropertyGridCtrl::EndEditItem.md)|调用由结构，当用户停止修改属性。|  
|[CMFCPropertyGridCtrl::Init](../Topic/CMFCPropertyGridCtrl::Init.md)|调用framework初始化属性网格控件。|  
|[CMFCPropertyGridCtrl::OnChangeSelection](../Topic/CMFCPropertyGridCtrl::OnChangeSelection.md)|调用由框架，更改当前选择。|  
|[CMFCPropertyGridCtrl::OnClickButton](../Topic/CMFCPropertyGridCtrl::OnClickButton.md)|调用由结构，当属性单击按钮。|  
|[CMFCPropertyGridCtrl::OnDrawBorder](../Topic/CMFCPropertyGridCtrl::OnDrawBorder.md)|调用由框架在属性网格控件周围绘制边框。|  
|[CMFCPropertyGridCtrl::OnDrawDescription](../Topic/CMFCPropertyGridCtrl::OnDrawDescription.md)|调用由框架绘制声明区域和显示标题文本。|  
|[CMFCPropertyGridCtrl::OnDrawList](../Topic/CMFCPropertyGridCtrl::OnDrawList.md)|调用由框架公开属性列表在属性网格控件中。|  
|[CMFCPropertyGridCtrl::OnDrawProperty](../Topic/CMFCPropertyGridCtrl::OnDrawProperty.md)|调用由框架公开属性。|  
|[CMFCPropertyGridCtrl::OnPropertyChanged](../Topic/CMFCPropertyGridCtrl::OnPropertyChanged.md)|调用由框架，更改属性的值。|  
|[CMFCPropertyGridCtrl::OnSelectCombo](../Topic/CMFCPropertyGridCtrl::OnSelectCombo.md)|调用由结构，当一个包含组合框控件的属性中选择。|  
|[CMFCPropertyGridCtrl::ValidateItemData](../Topic/CMFCPropertyGridCtrl::ValidateItemData.md)|调用由结构验证特性数据。|  
  
## 备注  
 属性网格控件包含可编辑的属性从 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md) 选件类派生的 `CMFCPropertyGridCtrl` 选件类公开。  每个属性可能表示类型，它可以包含子项。  属性网格控件支持可调整大小的方面。可以显示选定的属性的描述的底部。  
  
 若要使用属性网格控件，请构造 `CMFCPropertyGridCtrl` 对象并调用 [CMFCPropertyGridCtrl::Create](../Topic/CMFCPropertyGridCtrl::Create.md) 方法。  使用 [CMFCPropertyGridCtrl::AddProperty](../Topic/CMFCPropertyGridCtrl::AddProperty.md) 方法将特性添加到列表。  
  
## 选择属性  
 而不是表示值，属性项可以启动允许用户选择颜色、文件或字体的对话框。  
  
 下表列出了四个选择属性类型:  
  
|类|说明|  
|-------|--------|  
|[CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)|用于指定字符串的值的泛型属性，对于布尔值，日期等。|  
|[CMFCPropertyGridColorProperty Class](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)|用于选择颜色值的属性。|  
|[CMFCPropertyGridFileProperty Class](../../mfc/reference/cmfcpropertygridfileproperty-class.md)|用于选择文件的属性。|  
|[CMFCPropertyGridFontProperty Class](../../mfc/reference/cmfcpropertygridfontproperty-class.md)|用于选择字体的属性。|  
  
## 图示  
 下图演示显示属性采用以下两种方式的属性网格控件。  第一个插图分层显示属性，第二个按字母顺序显示属性。  
  
 ![属性列表与属性表](../../mfc/reference/media/proplist.png "PropList")  
  
## 示例  
 通过在 `CMFCPropertyGridCtrl` 选件类，中的各种方法下面的示例演示如何配置属性网格控件对象。  示例演示如何启用标头控件，启用声明区域，并将属性网格控件的外观。  该示例还演示如何设置控件的字母的架构，借助它由其属性名称包含的控件排序所有属性和如何设置属性网格控件的各个组件的自定义颜色。  此示例是 [新的控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_NewControls#14](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#16](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls#20](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls#21](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_4.cpp)]  
[!code-cpp[NVC_MFC_NewControls#24](../../mfc/reference/codesnippet/CPP/cmfcpropertygridctrl-class_5.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)  
  
## 要求  
 **标头:** afxpropertygridctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)