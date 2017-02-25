---
title: "CComControlBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComControlBase"
  - "ATL.CComControlBase"
  - "ATL::CComControlBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComControlBase class"
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CComControlBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为创建和管理ATL控件的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class ATL_NO_VTABLE CComControlBase  
  
```  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CComControlBase::AppearanceType](../Topic/CComControlBase::AppearanceType.md)|重写，如果您的 `m_nAppearance` 股票属性不是类型 `short`。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComControlBase::CComControlBase](../Topic/CComControlBase::CComControlBase.md)|构造函数。|  
|[CComControlBase::~CComControlBase](../Topic/CComControlBase::~CComControlBase.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComControlBase::ControlQueryInterface](../Topic/CComControlBase::ControlQueryInterface.md)|检索指向请求的接口。|  
|[CComControlBase::DoesVerbActivate](../Topic/CComControlBase::DoesVerbActivate.md)|检查用于激活控件的用户界面的 `iVerb` 参数。`IOleObjectImpl::DoVerb` 使用\(`iVerb` 等于 `OLEIVERB_UIACTIVATE`\)，定义执行的操作，当用户双击控件\(`iVerb` 等于 `OLEIVERB_PRIMARY`\)，显示控件\(`iVerb` 等于 `OLEIVERB_SHOW`\)，或者活动控件\(`iVerb` 等于 **OLEIVERB\_INPLACEACTIVATE**）。|  
|[CComControlBase::DoesVerbUIActivate](../Topic/CComControlBase::DoesVerbUIActivate.md)|检查 `IOleObjectImpl::DoVerb` 使用的 `iVerb` 参数使控件的用户界面活动并返回 **TRUE**。|  
|[CComControlBase::DoVerbProperties](../Topic/CComControlBase::DoVerbProperties.md)|显示控件的属性页。|  
|[CComControlBase::FireViewChange](../Topic/CComControlBase::FireViewChange.md)|调用此方法调用容器重绘控件或通知注册的建议接收器控件的视图已更改。|  
|[CComControlBase::GetAmbientAppearance](../Topic/CComControlBase::GetAmbientAppearance.md)|检索 **DISPID\_AMBIENT\_APPEARANCE**，设置为控件的当前外观:0简单的和1三维的。|  
|[CComControlBase::GetAmbientAutoClip](../Topic/CComControlBase::GetAmbientAutoClip.md)|检索 **DISPID\_AMBIENT\_AUTOCLIP**，指示容器是的标志支持自动剪切控件显示区域。|  
|[CComControlBase::GetAmbientBackColor](../Topic/CComControlBase::GetAmbientBackColor.md)|检索 **DISPID\_AMBIENT\_BACKCOLOR**，所有控件的单个背景色，定义由容器。|  
|[CComControlBase::GetAmbientCharSet](../Topic/CComControlBase::GetAmbientCharSet.md)|检索 **DISPID\_AMBIENT\_CHARSET**，所有控件的单个字符集，定义由容器。|  
|[CComControlBase::GetAmbientCodePage](../Topic/CComControlBase::GetAmbientCodePage.md)|检索 **DISPID\_AMBIENT\_CODEPAGE**，所有控件的单个字符集，定义由容器。|  
|[CComControlBase::GetAmbientDisplayAsDefault](../Topic/CComControlBase::GetAmbientDisplayAsDefault.md)|检索 **DISPID\_AMBIENT\_DISPLAYASDEFAULT**，是 **TRUE** 的标志，如果容器此站点指示该控件是默认按钮，该按钮控件应自行绘制使用更粗的帧。|  
|[CComControlBase::GetAmbientDisplayName](../Topic/CComControlBase::GetAmbientDisplayName.md)|检索 **DISPID\_AMBIENT\_DISPLAYNAME**，容器提供给控件的名称。|  
|[CComControlBase::GetAmbientFont](../Topic/CComControlBase::GetAmbientFont.md)|检索指向容器的环境 `IFont` 接口。|  
|[CComControlBase::GetAmbientFontDisp](../Topic/CComControlBase::GetAmbientFontDisp.md)|检索指向容器的环境 **IFontDisp** 调度接口。|  
|[CComControlBase::GetAmbientForeColor](../Topic/CComControlBase::GetAmbientForeColor.md)|检索 **DISPID\_AMBIENT\_FORECOLOR**，所有控件的单个前景色，定义由容器。|  
|[CComControlBase::GetAmbientLocaleID](../Topic/CComControlBase::GetAmbientLocaleID.md)|检索 **DISPID\_AMBIENT\_LOCALEID**，容器使用的语言标识符。|  
|[CComControlBase::GetAmbientMessageReflect](../Topic/CComControlBase::GetAmbientMessageReflect.md)|检索 **DISPID\_AMBIENT\_MESSAGEREFLECT**，指示容器是的标志接收windows消息\(例如 `WM_DRAWITEM`\)作为事件。|  
|[CComControlBase::GetAmbientPalette](../Topic/CComControlBase::GetAmbientPalette.md)|检索 **DISPID\_AMBIENT\_PALETTE**，用于访问容器的 `HPALETTE`。|  
|[CComControlBase::GetAmbientProperty](../Topic/CComControlBase::GetAmbientProperty.md)|检索 `id`指定容器的属性。|  
|[CComControlBase::GetAmbientRightToLeft](../Topic/CComControlBase::GetAmbientRightToLeft.md)|检索 **DISPID\_AMBIENT\_RIGHTTOLEFT**，方向内容由容器显示。|  
|[CComControlBase::GetAmbientScaleUnits](../Topic/CComControlBase::GetAmbientScaleUnits.md)|检索 **DISPID\_AMBIENT\_SCALEUNITS**，容器的环境单位\(例如英寸或厘米\)标记的显示。|  
|[CComControlBase::GetAmbientShowGrabHandles](../Topic/CComControlBase::GetAmbientShowGrabHandles.md)|检索 **DISPID\_AMBIENT\_SHOWGRABHANDLES**，指示容器是的标志使控件显示自身的抓取手柄，当激活时。|  
|[CComControlBase::GetAmbientShowHatching](../Topic/CComControlBase::GetAmbientShowHatching.md)|检索 **DISPID\_AMBIENT\_SHOWHATCHING**，指示容器是的标志使控件显示自身与一个阴影模式，当用户界面处于活动状态时。|  
|[CComControlBase::GetAmbientSupportsMnemonics](../Topic/CComControlBase::GetAmbientSupportsMnemonics.md)|检索 **DISPID\_AMBIENT\_SUPPORTSMNEMONICS**，指示容器是的标志支持键盘助记键。|  
|[CComControlBase::GetAmbientTextAlign](../Topic/CComControlBase::GetAmbientTextAlign.md)|检索 **DISPID\_AMBIENT\_TEXTALIGN**，容器喜欢的文本对齐方式:0泛型对齐\(数字纠正，文本\)，1左对齐的，2中心对齐的和3正确的对齐的。|  
|[CComControlBase::GetAmbientTopToBottom](../Topic/CComControlBase::GetAmbientTopToBottom.md)|检索 **DISPID\_AMBIENT\_TOPTOBOTTOM**，方向内容由容器显示。|  
|[CComControlBase::GetAmbientUIDead](../Topic/CComControlBase::GetAmbientUIDead.md)|检索 **DISPID\_AMBIENT\_UIDEAD**，指示容器是的标志希望该控件响应用户界面事件。|  
|[CComControlBase::GetAmbientUserMode](../Topic/CComControlBase::GetAmbientUserMode.md)|检索 **DISPID\_AMBIENT\_USERMODE**，指示容器是标志。运行模式\(**TRUE**\)或设计模式\(**FALSE**\)下。|  
|[CComControlBase::GetDirty](../Topic/CComControlBase::GetDirty.md)|返回数据成员 `m_bRequiresSave`的值。|  
|[CComControlBase::GetZoomInfo](../Topic/CComControlBase::GetZoomInfo.md)|检索比例因子的分子和分母的x和y的值为就地编辑激活的控件的。|  
|[CComControlBase::InPlaceActivate](../Topic/CComControlBase::InPlaceActivate.md)|导致该控件绑定到从非活动状态的转换到任意状态在 `iVerb` 的谓词指示。|  
|[CComControlBase::InternalGetSite](../Topic/CComControlBase::InternalGetSite.md)|调用此方法来查询指针的控件站点添加到由标识的接口。|  
|[CComControlBase::OnDraw](../Topic/CComControlBase::OnDraw.md)|重写此方法绘制自己的控件。|  
|[CComControlBase::OnDrawAdvanced](../Topic/CComControlBase::OnDrawAdvanced.md)|默认值 **OnDrawAdvanced** 一规范化的设备上下文来绘制准备，然后调用您的控件选件类的 `OnDraw` 方法。|  
|[CComControlBase::OnKillFocus](../Topic/CComControlBase::OnKillFocus.md)|检查该控件是否处于就地活动状态并具有有效的控制站点，然后通知容器控件失去了焦点。|  
|[CComControlBase::OnMouseActivate](../Topic/CComControlBase::OnMouseActivate.md)|检查用户界面以用户模式，然后激活该控件。|  
|[CComControlBase::OnPaint](../Topic/CComControlBase::OnPaint.md)|容器用于绘制准备，获取控件的工作区，然后调用控件选件类的 `OnDraw` 方法。|  
|[CComControlBase::OnSetFocus](../Topic/CComControlBase::OnSetFocus.md)|检查该控件是否处于就地活动状态并具有有效的控制站点，然后通知控件获得的焦点的容器。|  
|[CComControlBase::PreTranslateAccelerator](../Topic/CComControlBase::PreTranslateAccelerator.md)|重写此方法以提供您的键盘快捷键处理程序。|  
|[CComControlBase::SendOnClose](../Topic/CComControlBase::SendOnClose.md)|通知所有具有建议性接收到建议持有人注册该控件已关闭。|  
|[CComControlBase::SendOnDataChange](../Topic/CComControlBase::SendOnDataChange.md)|通知所有具有建议性接收到建议持有人控制数据已更改。|  
|[CComControlBase::SendOnRename](../Topic/CComControlBase::SendOnRename.md)|通知所有具有建议性接收到建议持有人注册该控件具有一个新的标记。|  
|[CComControlBase::SendOnSave](../Topic/CComControlBase::SendOnSave.md)|通知所有具有建议性接收到建议持有人注册该控件已保存。|  
|[CComControlBase::SendOnViewChange](../Topic/CComControlBase::SendOnViewChange.md)|通知所有注册的建议使用性接收器控件的视图已更改。|  
|[CComControlBase::SetControlFocus](../Topic/CComControlBase::SetControlFocus.md)|设置或移除键盘焦点来回控件。|  
|[CComControlBase::SetDirty](../Topic/CComControlBase::SetDirty.md)|设置数据成员 `m_bRequiresSave` 到 `bDirty`的值。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComControlBase::m\_bAutoSize](../Topic/CComControlBase::m_bAutoSize.md)|指示控件的标志不能是其他范围。|  
|[CComControlBase::m\_bDrawFromNatural](../Topic/CComControlBase::m_bDrawFromNatural.md)|标记指示 `IDataObjectImpl::GetData` 和 `CComControlBase::GetZoomInfo` 应设置从 `m_sizeNatural` 的控件大小而不是从 `m_sizeExtent`。|  
|[CComControlBase::m\_bDrawGetDataInHimetric](../Topic/CComControlBase::m_bDrawGetDataInHimetric.md)|标记指示 `IDataObjectImpl::GetData` 应使用而不是HIMETRIC单元像素，在绘制时。|  
|[CComControlBase::m\_bInPlaceActive](../Topic/CComControlBase::m_bInPlaceActive.md)|指示控件的标志是就地活动状态。|  
|[CComControlBase::m\_bInPlaceSiteEx](../Topic/CComControlBase::m_bInPlaceSiteEx.md)|指示容器的标志支持 **IOleInPlaceSiteEx** 接口和OCX96控件功能，如无窗口和无闪烁的控件。|  
|[CComControlBase::m\_bNegotiatedWnd](../Topic/CComControlBase::m_bNegotiatedWnd.md)|标记指示控件是否与容器协调为OCX96控件功能支持\(例如无闪烁的和无窗口控件\)，并且，该控件是否有窗口或无窗口的。|  
|[CComControlBase::m\_bRecomposeOnResize](../Topic/CComControlBase::m_bRecomposeOnResize.md)|当容器更改控件的显示区域时，指示控件的标志若要重新编写其呈现。|  
|[CComControlBase::m\_bRequiresSave](../Topic/CComControlBase::m_bRequiresSave.md)|则它上次保存了，指示控件的标志已更改。|  
|[CComControlBase::m\_bResizeNatural](../Topic/CComControlBase::m_bResizeNatural.md)|指示控件的标志若要调整其自然区域\(它不实际大小\)，当容器更改控件的显示范围。|  
|[CComControlBase::m\_bUIActive](../Topic/CComControlBase::m_bUIActive.md)|标记指示控件的用户界面，例如，菜单和工具栏，处于活动状态。|  
|[CComControlBase::m\_bUsingWindowRgn](../Topic/CComControlBase::m_bUsingWindowRgn.md)|指示控件的标志使用由容器提供的windows区域。|  
|[CComControlBase::m\_bWasOnceWindowless](../Topic/CComControlBase::m_bWasOnceWindowless.md)|指示控件的标志是无窗口的，但是，可以不能现在是无窗口的。|  
|[CComControlBase::m\_bWindowOnly](../Topic/CComControlBase::m_bWindowOnly.md)|指示控件的标记应有窗口，因此，即使容器支持无窗口控件。|  
|[CComControlBase::m\_bWndLess](../Topic/CComControlBase::m_bWndLess.md)|指示控件的标志是无窗口的。|  
|[CComControlBase::m\_hWndCD](../Topic/CComControlBase::m_hWndCD.md)|包含对窗口句柄与控件关联。|  
|[CComControlBase::m\_nFreezeEvents](../Topic/CComControlBase::m_nFreezeEvents.md)|次数的计数容器包含冻结的事件\(拒绝接受事件\)，不具有事件\(事件接受干预的解冻）。|  
|[CComControlBase::m\_rcPos](../Topic/CComControlBase::m_rcPos.md)|在控件的像素的位置，表示为容器的坐标。|  
|[CComControlBase::m\_sizeExtent](../Topic/CComControlBase::m_sizeExtent.md)|控件的边界。HIMETRIC单元\(每个单位是0.01毫米\)特定显示的。|  
|[CComControlBase::m\_sizeNatural](../Topic/CComControlBase::m_sizeNatural.md)|控件的实际大小。HIMETRIC单元\(每个单位是0.01毫米）。|  
|[CComControlBase::m\_spAdviseSink](../Topic/CComControlBase::m_spAdviseSink.md)|对建议性连接的一个直接指针在容器\(容器的 [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)）。|  
|[CComControlBase::m\_spAmbientDispatch](../Topic/CComControlBase::m_spAmbientDispatch.md)|允许您通过 `IDispatch` 指针检索和设置容器的属性的 `CComDispatchDriver` 对象。|  
|[CComControlBase::m\_spClientSite](../Topic/CComControlBase::m_spClientSite.md)|为控件的客户端站点的指针在容器中。|  
|[CComControlBase::m\_spDataAdviseHolder](../Topic/CComControlBase::m_spDataAdviseHolder.md)|提供标准方式保存数据对象之间的建议使用性连接和建议接收器。|  
|[CComControlBase::m\_spInPlaceSite](../Topic/CComControlBase::m_spInPlaceSite.md)|为容器的 [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)、 [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)或 [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) 接口的指针的指针。|  
|[CComControlBase::m\_spOleAdviseHolder](../Topic/CComControlBase::m_spOleAdviseHolder.md)|提供方法的标准实现保存具有建议性连接。|  
  
## 备注  
 此选件类为创建和管理ATL控件的方法。  [CComControl选件类](../../atl/reference/ccomcontrol-class.md) 从 `CComControlBase`派生。  使用ATL控件向导，当您创建标准控件或DHTML控件，该向导从 `CComControlBase`将自动派生您的选件类。  
  
 有关创建控件的更多信息，请参见 [ATL教程](../../atl/active-template-library-atl-tutorial.md)。  有关ATL项目向导的更多信息，请参见文章 [创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)