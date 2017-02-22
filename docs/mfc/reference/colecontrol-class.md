---
title: "COleControl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleControl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControl class"
  - "控件 [MFC], OLE"
  - "控件 [MFC], windowless"
  - "OLE 控件, MFC"
  - "windowless controls"
  - "windowless controls, MFC"
ms.assetid: 53e95299-38e8-447b-9c5f-a381d27f5123
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# COleControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

开发的OLE控件的功能强大的基类。  
  
## 语法  
  
```  
class COleControl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleControl::COleControl](../Topic/COleControl::COleControl.md)|创建一个 `COleControl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleControl::AmbientAppearance](../Topic/COleControl::AmbientAppearance.md)|检索该控件的当前外观。|  
|[COleControl::AmbientBackColor](../Topic/COleControl::AmbientBackColor.md)|返回环境BackColor属性的值。|  
|[COleControl::AmbientDisplayName](../Topic/COleControl::AmbientDisplayName.md)|返回控件的名称为指定的容器。|  
|[COleControl::AmbientFont](../Topic/COleControl::AmbientFont.md)|返回环境字体属性的值。|  
|[COleControl::AmbientForeColor](../Topic/COleControl::AmbientForeColor.md)|返回环境ForeColor属性的值。|  
|[COleControl::AmbientLocaleID](../Topic/COleControl::AmbientLocaleID.md)|返回容器的区域设置ID.|  
|[COleControl::AmbientScaleUnits](../Topic/COleControl::AmbientScaleUnits.md)|返回容器使用的单位的类型。|  
|[COleControl::AmbientShowGrabHandles](../Topic/COleControl::AmbientShowGrabHandles.md)|确定抓取控点是否应显示。|  
|[COleControl::AmbientShowHatching](../Topic/COleControl::AmbientShowHatching.md)|确定阴影是否应显示。|  
|[COleControl::AmbientTextAlign](../Topic/COleControl::AmbientTextAlign.md)|返回容器指定的文本对齐的类型。|  
|[COleControl::AmbientUIDead](../Topic/COleControl::AmbientUIDead.md)|确定控件是否应响应用户界面事件。|  
|[COleControl::AmbientUserMode](../Topic/COleControl::AmbientUserMode.md)|确定容器的模式。|  
|[COleControl::BoundPropertyChanged](../Topic/COleControl::BoundPropertyChanged.md)|通知容器更改了绑定属性。|  
|[COleControl::BoundPropertyRequestEdit](../Topic/COleControl::BoundPropertyRequestEdit.md)|请求权限编辑属性值。|  
|[COleControl::ClientToParent](../Topic/COleControl::ClientToParent.md)|转换点相对于控件的原点为点相对于其容器的原点。|  
|[COleControl::ClipCaretRect](../Topic/COleControl::ClipCaretRect.md)|如果它由控件，重叠调整插入符号矩形。|  
|[COleControl::ControlInfoChanged](../Topic/COleControl::ControlInfoChanged.md)|在以后调用此函数控件处理的设置助记键已更改。|  
|[COleControl::DisplayError](../Topic/COleControl::DisplayError.md)|显示股票错误事件对控件的用户。|  
|[COleControl::DoClick](../Topic/COleControl::DoClick.md)|股票 `DoClick` 方法的实现。|  
|[COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md)|序列化 `COleControl` 对象的属性。|  
|[COleControl::DoSuperclassPaint](../Topic/COleControl::DoSuperclassPaint.md)|重绘从Windows control子类的一个OLE控件。|  
|[COleControl::EnableSimpleFrame](../Topic/COleControl::EnableSimpleFrame.md)|启用简单的帧对控件的支持。|  
|[COleControl::ExchangeExtent](../Topic/COleControl::ExchangeExtent.md)|序列化控件的宽度和高度。|  
|[COleControl::ExchangeStockProps](../Topic/COleControl::ExchangeStockProps.md)|序列化控件股票属性。|  
|[COleControl::ExchangeVersion](../Topic/COleControl::ExchangeVersion.md)|序列化控件的版本号。|  
|[COleControl::FireClick](../Topic/COleControl::FireClick.md)|激发股票 `Click` 事件。|  
|[COleControl::FireDblClick](../Topic/COleControl::FireDblClick.md)|激发股票 `DblClick` 事件。|  
|[COleControl::FireError](../Topic/COleControl::FireError.md)|激发股票 `Error` 事件。|  
|[COleControl::FireEvent](../Topic/COleControl::FireEvent.md)|引发自定义事件。|  
|[COleControl::FireKeyDown](../Topic/COleControl::FireKeyDown.md)|激发股票 `KeyDown` 事件。|  
|[COleControl::FireKeyPress](../Topic/COleControl::FireKeyPress.md)|激发股票 `KeyPress` 事件。|  
|[COleControl::FireKeyUp](../Topic/COleControl::FireKeyUp.md)|激发股票 `KeyUp` 事件。|  
|[COleControl::FireMouseDown](../Topic/COleControl::FireMouseDown.md)|激发股票 `MouseDown` 事件。|  
|[COleControl::FireMouseMove](../Topic/COleControl::FireMouseMove.md)|激发股票 `MouseMove` 事件。|  
|[COleControl::FireMouseUp](../Topic/COleControl::FireMouseUp.md)|激发股票 `MouseUp` 事件。|  
|[COleControl::FireReadyStateChange](../Topic/COleControl::FireReadyStateChange.md)|当控件的就绪状态更改时，激发事件。|  
|[COleControl::GetActivationPolicy](../Topic/COleControl::GetActivationPolicy.md)|更改支持 `IPointerInactive` 界面控件的默认启动行为。|  
|[COleControl::GetAmbientProperty](../Topic/COleControl::GetAmbientProperty.md)|返回指定的单个属性的值。|  
|[COleControl::GetAppearance](../Topic/COleControl::GetAppearance.md)|返回常用外观属性的值。|  
|[COleControl::GetBackColor](../Topic/COleControl::GetBackColor.md)|返回库存BackColor属性的值。|  
|[COleControl::GetBorderStyle](../Topic/COleControl::GetBorderStyle.md)|返回库存BorderStyle属性的值。|  
|[COleControl::GetCapture](../Topic/COleControl::GetCapture.md)|确定一个无窗口，激活的控件对象是否具有鼠标捕获。|  
|[COleControl::GetClassID](../Topic/COleControl::GetClassID.md)|检索控件的OLE选件类ID。|  
|[COleControl::GetClientOffset](../Topic/COleControl::GetClientOffset.md)|检索控件的矩形区域的左上角和其工作区之间的左上角的差异。|  
|[COleControl::GetClientRect](../Topic/COleControl::GetClientRect.md)|检索控件的工作区的大小。|  
|[COleControl::GetClientSite](../Topic/COleControl::GetClientSite.md)|查询指针的对象传递给其在其容器内的当前客户端站点。|  
|[COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)|检索控制标志设置为。|  
|[COleControl::GetControlSize](../Topic/COleControl::GetControlSize.md)|返回OLE控件的位置和大小。|  
|[COleControl::GetDC](../Topic/COleControl::GetDC.md)|为无窗口控件获取提供方法从其容器的设备上下文。|  
|[COleControl::GetEnabled](../Topic/COleControl::GetEnabled.md)|返回一个库存enabled特性的值。|  
|[COleControl::GetExtendedControl](../Topic/COleControl::GetExtendedControl.md)|检索指向属于容器中扩展控件对象。|  
|[COleControl::GetFocus](../Topic/COleControl::GetFocus.md)|确定控件是否具有焦点。|  
|[COleControl::GetFont](../Topic/COleControl::GetFont.md)|返回常用字体属性的值。|  
|[COleControl::GetFontTextMetrics](../Topic/COleControl::GetFontTextMetrics.md)|返回 `CFontHolder` 对象的指标。|  
|[COleControl::GetForeColor](../Topic/COleControl::GetForeColor.md)|返回ForeColor常用属性的值。|  
|[COleControl::GetHwnd](../Topic/COleControl::GetHwnd.md)|返回库存HWND属性的值。|  
|[COleControl::GetMessageString](../Topic/COleControl::GetMessageString.md)|为菜单项提供状态栏文本。|  
|[COleControl::GetNotSupported](../Topic/COleControl::GetNotSupported.md)|由用户以防止控件的属性值的访问。|  
|[COleControl::GetReadyState](../Topic/COleControl::GetReadyState.md)|返回控件为就绪状态。|  
|[COleControl::GetRectInContainer](../Topic/COleControl::GetRectInContainer.md)|返回控件的矩形相对于其容器。|  
|[COleControl::GetStockTextMetrics](../Topic/COleControl::GetStockTextMetrics.md)|返回常用字体属性的指标。|  
|[COleControl::GetText](../Topic/COleControl::GetText.md)|返回常用文本或description属性的值。|  
|[COleControl::GetWindowlessDropTarget](../Topic/COleControl::GetWindowlessDropTarget.md)|允许无窗口控件的重写为拖放操作的目标。|  
|[COleControl::InitializeIIDs](../Topic/COleControl::InitializeIIDs.md)|通知该控件将使用的基类IIDs。|  
|[COleControl::InternalGetFont](../Topic/COleControl::InternalGetFont.md)|返回常用字体属性的一 `CFontHolder` 对象。|  
|[COleControl::InternalGetText](../Topic/COleControl::InternalGetText.md)|检索股票声明或文本属性。|  
|[COleControl::InternalSetReadyState](../Topic/COleControl::InternalSetReadyState.md)|将控件的状态和激发准备就绪状态更改事件。|  
|[COleControl::InvalidateControl](../Topic/COleControl::InvalidateControl.md)|无效显示控件的大小，使其重新绘制。|  
|[COleControl::InvalidateRgn](../Topic/COleControl::InvalidateRgn.md)|无效在给定区域内的容器窗口的工作区。  在区域可以使用重绘无窗口控件。|  
|[COleControl::IsConvertingVBX](../Topic/COleControl::IsConvertingVBX.md)|允许专用OLE控件的填充。|  
|[COleControl::IsModified](../Topic/COleControl::IsModified.md)|确定控件是否已更改。|  
|[COleControl::IsOptimizedDraw](../Topic/COleControl::IsOptimizedDraw.md)|指示容器是支持当前绘图操作的优化绘图。|  
|[COleControl::IsSubclassedControl](../Topic/COleControl::IsSubclassedControl.md)|调用确定是否控件子类Windows控件。|  
|[COleControl::Load](../Topic/COleControl::Load.md)|重置所有以前的异步数据并启动控件的异步属性的新负载。|  
|[COleControl::LockInPlaceActive](../Topic/COleControl::LockInPlaceActive.md)|确定您的控件是否能容器停用。|  
|[COleControl::OnAmbientPropertyChange](../Topic/COleControl::OnAmbientPropertyChange.md)|调用，更改一个环境属性。|  
|[COleControl::OnAppearanceChanged](../Topic/COleControl::OnAppearanceChanged.md)|调用，更改常用外观属性。|  
|[COleControl::OnBackColorChanged](../Topic/COleControl::OnBackColorChanged.md)|调用，更改股票BackColor属性。|  
|[COleControl::OnBorderStyleChanged](../Topic/COleControl::OnBorderStyleChanged.md)|调用，更改股票BorderStyle属性。|  
|[COleControl::OnClick](../Topic/COleControl::OnClick.md)|调用激发库存单击事件。|  
|[COleControl::OnClose](../Topic/COleControl::OnClose.md)|通知该控件 `IOleControl::Close` 调用。|  
|[COleControl::OnDoVerb](../Topic/COleControl::OnDoVerb.md)|调用，在控件谓词执行之后。|  
|[COleControl::OnDraw](../Topic/COleControl::OnDraw.md)|调用，当控件请求重绘自身。|  
|[COleControl::OnDrawMetafile](../Topic/COleControl::OnDrawMetafile.md)|调用由容器使用图元文件设备上下文，那么，当控件请求重绘自身。|  
|[COleControl::OnEdit](../Topic/COleControl::OnEdit.md)|调用由容器对用户界面中才能OLE控件。|  
|[COleControl::OnEnabledChanged](../Topic/COleControl::OnEnabledChanged.md)|当更改时将调用，该股票enabled特性。|  
|[COleControl::OnEnumVerbs](../Topic/COleControl::OnEnumVerbs.md)|调用由容器枚举控件上的谓词。|  
|[COleControl::OnEventAdvise](../Topic/COleControl::OnEventAdvise.md)|调用时，事件处理程序将从控件连接或断开。|  
|[COleControl::OnFontChanged](../Topic/COleControl::OnFontChanged.md)|调用，更改常用字体属性。|  
|[COleControl::OnForeColorChanged](../Topic/COleControl::OnForeColorChanged.md)|调用，更改股票ForeColor属性。|  
|[COleControl::OnFreezeEvents](../Topic/COleControl::OnFreezeEvents.md)|调用，当控件的事件冻结或解冻。|  
|[COleControl::OnGetColorSet](../Topic/COleControl::OnGetColorSet.md)|通知该控件 `IOleObject::GetColorSet` 调用。|  
|[COleControl::OnGetControlInfo](../Topic/COleControl::OnGetControlInfo.md)|提供助记键信息到容器。|  
|[COleControl::OnGetDisplayString](../Topic/COleControl::OnGetDisplayString.md)|调用获取字符串表示属性值。|  
|[COleControl::OnGetInPlaceMenu](../Topic/COleControl::OnGetInPlaceMenu.md)|请求与容器菜单将控制菜单的句柄。|  
|[COleControl::OnGetNaturalExtent](../Topic/COleControl::OnGetNaturalExtent.md)|检索控件显示范围的重写最接近建议的大小和界限模式。|  
|[COleControl::OnGetPredefinedStrings](../Topic/COleControl::OnGetPredefinedStrings.md)|返回表示属性的字符串可能的值。|  
|[COleControl::OnGetPredefinedValue](../Topic/COleControl::OnGetPredefinedValue.md)|返回值与预定义的字符串相对应。|  
|[COleControl::OnGetViewExtent](../Topic/COleControl::OnGetViewExtent.md)|检索控件的显示区域的大小重写\(可以使用启用两阶段的绘图）。|  
|[COleControl::OnGetViewRect](../Topic/COleControl::OnGetViewRect.md)|将控件的大小的重写为开始在特定位置的矩形。|  
|[COleControl::OnGetViewStatus](../Topic/COleControl::OnGetViewStatus.md)|检索控件的视图状态的重写。|  
|[COleControl::OnHideToolBars](../Topic/COleControl::OnHideToolBars.md)|调用由容器，当控件处于停用的UI。|  
|[COleControl::OnInactiveMouseMove](../Topic/COleControl::OnInactiveMouseMove.md)|重写具有非活动控件的容器是在鼠标指针计划 `WM_MOUSEMOVE` 消息下到控件。|  
|[COleControl::OnInactiveSetCursor](../Topic/COleControl::OnInactiveSetCursor.md)|重写具有非活动控件的容器是在鼠标指针计划 `WM_SETCURSOR` 消息下到控件。|  
|[COleControl::OnKeyDownEvent](../Topic/COleControl::OnKeyDownEvent.md)|调用，在股票KeyDown事件会激发之后。|  
|[COleControl::OnKeyPressEvent](../Topic/COleControl::OnKeyPressEvent.md)|调用，在股票KeyPress事件会激发之后。|  
|[COleControl::OnKeyUpEvent](../Topic/COleControl::OnKeyUpEvent.md)|调用，在股票KeyUp事件会激发之后。|  
|[COleControl::OnMapPropertyToPage](../Topic/COleControl::OnMapPropertyToPage.md)|指示要使用的属性页为编辑属性。|  
|[COleControl::OnMnemonic](../Topic/COleControl::OnMnemonic.md)|调用，当控件的助记键按下了。|  
|[COleControl::OnProperties](../Topic/COleControl::OnProperties.md)|调用，当控件的“属性” er调用。|  
|[COleControl::OnQueryHitPoint](../Topic/COleControl::OnQueryHitPoint.md)|查询的重写控件的显示是否重叠给定的点。|  
|[COleControl::OnQueryHitRect](../Topic/COleControl::OnQueryHitRect.md)|查询的重写控件的显示是否重叠任何在特定矩形点。|  
|[COleControl::OnRenderData](../Topic/COleControl::OnRenderData.md)|调用由框架中检索数据。指定的格式。|  
|[COleControl::OnRenderFileData](../Topic/COleControl::OnRenderFileData.md)|调用由框架从一个文件中检索数据。指定的格式。|  
|[COleControl::OnRenderGlobalData](../Topic/COleControl::OnRenderGlobalData.md)|调用由框架从全局内存中检索数据。指定的格式。|  
|[COleControl::OnResetState](../Topic/COleControl::OnResetState.md)|重置控件的属性设置为默认值。|  
|[COleControl::OnSetClientSite](../Topic/COleControl::OnSetClientSite.md)|通知该控件 `IOleControl::SetClientSite` 调用。|  
|[COleControl::OnSetData](../Topic/COleControl::OnSetData.md)|用另一个值替换控件数据。|  
|[COleControl::OnSetExtent](../Topic/COleControl::OnSetExtent.md)|调用控件的区域后已更改。|  
|[COleControl::OnSetObjectRects](../Topic/COleControl::OnSetObjectRects.md)|调用，在更改之后控件的尺寸。|  
|[COleControl::OnShowToolBars](../Topic/COleControl::OnShowToolBars.md)|调用，当控件处于激活的UI。|  
|[COleControl::OnTextChanged](../Topic/COleControl::OnTextChanged.md)|调用，更改常用文本或description属性。|  
|[COleControl::OnWindowlessMessage](../Topic/COleControl::OnWindowlessMessage.md)|处理windows消息\(除了鼠标和键盘消息外\)无窗口控件的。|  
|[COleControl::ParentToClient](../Topic/COleControl::ParentToClient.md)|转换点相对于容器的原点为点相对于控件的原点。|  
|[COleControl::PostModalDialog](../Topic/COleControl::PostModalDialog.md)|通知容器模式对话框已关闭。|  
|[COleControl::PreModalDialog](../Topic/COleControl::PreModalDialog.md)|通知容器模式将显示对话框。|  
|[COleControl::RecreateControlWindow](../Topic/COleControl::RecreateControlWindow.md)|销毁并重新创建控件的窗口。|  
|[COleControl::Refresh](../Topic/COleControl::Refresh.md)|强制控件外观的重新绘制。|  
|[COleControl::ReleaseCapture](../Topic/COleControl::ReleaseCapture.md)|版本鼠标捕获。|  
|[COleControl::ReleaseDC](../Topic/COleControl::ReleaseDC.md)|释放无窗口控件的容器的显示设备上下文。|  
|[COleControl::ReparentControlWindow](../Topic/COleControl::ReparentControlWindow.md)|重置控制窗口的父级。|  
|[COleControl::ResetStockProps](../Topic/COleControl::ResetStockProps.md)|初始化 `COleControl` 常用属性设置为默认值。|  
|[COleControl::ResetVersion](../Topic/COleControl::ResetVersion.md)|初始化版本号为特定值。|  
|[COleControl::ScrollWindow](../Topic/COleControl::ScrollWindow.md)|允许无窗口控件移动到其就地活动的映像内的区域在显示。|  
|[COleControl::SelectFontObject](../Topic/COleControl::SelectFontObject.md)|选择自定义字体属性设置为设备上下文。|  
|[COleControl::SelectStockFont](../Topic/COleControl::SelectStockFont.md)|选择常用字体属性设置为设备上下文。|  
|[COleControl::SerializeExtent](../Topic/COleControl::SerializeExtent.md)|序列化或初始化控件的显示空间。|  
|[COleControl::SerializeStockProps](../Topic/COleControl::SerializeStockProps.md)|序列化或初始化 `COleControl` 股票属性。|  
|[COleControl::SerializeVersion](../Topic/COleControl::SerializeVersion.md)|序列化或初始化控件的版本信息。|  
|[COleControl::SetAppearance](../Topic/COleControl::SetAppearance.md)|一组常用外观属性的值。|  
|[COleControl::SetBackColor](../Topic/COleControl::SetBackColor.md)|一组常用BackColor属性的值。|  
|[COleControl::SetBorderStyle](../Topic/COleControl::SetBorderStyle.md)|一组常用BorderStyle属性的值。|  
|[COleControl::SetCapture](../Topic/COleControl::SetCapture.md)|使控件的容器窗口个委托控件的鼠标捕获。|  
|[COleControl::SetControlSize](../Topic/COleControl::SetControlSize.md)|设置OLE控件的位置和大小。|  
|[COleControl::SetEnabled](../Topic/COleControl::SetEnabled.md)|将库存enabled特性的值。|  
|[COleControl::SetFocus](../Topic/COleControl::SetFocus.md)|使控件的容器窗口个委托控件的输入焦点。|  
|[COleControl::SetFont](../Topic/COleControl::SetFont.md)|一组常用字体属性的值。|  
|[COleControl::SetForeColor](../Topic/COleControl::SetForeColor.md)|一组常用ForeColor属性的值。|  
|[COleControl::SetInitialSize](../Topic/COleControl::SetInitialSize.md)|在容器一套OLE控件的大小，在第一次显示。|  
|[COleControl::SetModifiedFlag](../Topic/COleControl::SetModifiedFlag.md)|更改控件的已修改状态。|  
|[COleControl::SetNotPermitted](../Topic/COleControl::SetNotPermitted.md)|指示编辑请求失败。|  
|[COleControl::SetNotSupported](../Topic/COleControl::SetNotSupported.md)|由用户以防止控件的属性值的修改。|  
|[COleControl::SetRectInContainer](../Topic/COleControl::SetRectInContainer.md)|将控件的矩形相对于其容器。|  
|[COleControl::SetText](../Topic/COleControl::SetText.md)|一组常用文本或description属性的值。|  
|[COleControl::ThrowError](../Topic/COleControl::ThrowError.md)|信号错误在OLE控件生成的。|  
|[COleControl::TransformCoords](../Topic/COleControl::TransformCoords.md)|将容器和控件大小的坐标值。|  
|[COleControl::TranslateColor](../Topic/COleControl::TranslateColor.md)|转换 **OLE\_COLOR** 值转换为 **COLORREF** 值。|  
|[COleControl::WillAmbientsBeValidDuringLoad](../Topic/COleControl::WillAmbientsBeValidDuringLoad.md)|确定环境属性是否将可用控件下次加载。|  
|[COleControl::WindowProc](../Topic/COleControl::WindowProc.md)|为 `COleControl` 对象的Windows程序。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[COleControl::DrawContent](../Topic/COleControl::DrawContent.md)|调用由结构，并根据需要更新控件的外观。|  
|[COleControl::DrawMetafile](../Topic/COleControl::DrawMetafile.md)|调用由结构，当使用图元文件设备上下文。|  
|[COleControl::IsInvokeAllowed](../Topic/COleControl::IsInvokeAllowed.md)|启用自动化方法调用。|  
|[COleControl::SetInitialDataFormats](../Topic/COleControl::SetInitialDataFormats.md)|调用framework初始化数据格式列表控件支持的。|  
  
## 备注  
 从 `CWnd`派生，此选件类继承的Windows窗口对象的所有功能和其他功能特定于OLE，如事件激发并且能够支持方法和属性。  
  
 OLE控件可插入到OLE容器应用程序并与容器使用事件激发一个双向系统和显示方法和属性传递到该容器。  请注意标准OLE容器只支持OLE控件的基本功能。  它们不支持OLE控件的扩展功能。  当事件发送到容器由于出现在控件时，的某些事件激发时发生。  反过来，容器与控件进行通信通过使用显示的方法，并且属性类似于c. C\+\+的成员函数和数据成员类别。  在某些事件发生时，此方法允许开发人员控件的外观和通知容器。  
  
## 无窗口控件  
 OLE控件可用于就地活动状态，而无需窗口。  无窗口控件具有明显的好处:  
  
-   无窗口控件可以是透明和非矩形  
  
-   无窗口控件减少实例大小和对象的创建时间  
  
 控件不需要窗口。  窗口提供的服务可以通过单个共享的窗口\(通常容器的\)和个计划代码轻松提供。  具有窗口位于对象的主要不必要的问题。  
  
 当使用时无窗口的启动，包含一个窗口\)的容器\(为控件提供自己的windows另外提供的服务负责。  例如，在中，如果控件需要查询键盘焦点，查询鼠标捕获或获取设备上下文，这些操作由容器管理。  `COleControl`[无窗口操作成员函数](http://msdn.microsoft.com/zh-cn/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) 调用容器中的这些操作。  
  
 当无窗口的启动启用时，容器将输入消息发送到控件的 `IOleInPlaceObjectWindowless` 接口\( [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) 扩展无窗口的支持）。  此接口的`COleControl`的实现通过控件的消息映射进行安排这些消息，在相应调整鼠标坐之后。  您可以通过将对应项处理类似普通的窗口消息的这些消息，向消息映射。  
  
 在无窗口控件，应始终使用 `COleControl` 成员函数而不是相应的 `CWnd` 成员函数或其相关Windows API函数。  
  
 OLE控件对象还可以在窗口中，才会变为活动状态时，但是，对于非活动有效转换所需的工作量引发，并且该转换的速度断开连接。  这是问题时，会用例:例如，请考虑文本框网格。  当向上或向下cursoring通过列时，每个控件都必须就地激活然后再停用。  非活动\/有效转换的速度将直接影响滚动速度。  
  
 有关开发OLE控制结构的更多信息，请参见位于 [MFC ActiveX控件](../../mfc/mfc-activex-controls.md) 和 [概述:创建MFC ActiveX控件程序](../../mfc/reference/mfc-activex-control-wizard.md)。  有关优化OLE控件的信息，包括无窗口和无闪烁的控件的信息，请参见 [MFC ActiveX控件:优化](../../mfc/mfc-activex-controls-optimization.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `COleControl`  
  
## 要求  
 **Header:** afxctl.h  
  
## 请参阅  
 [MFC示例CIRC3](../../top/visual-cpp-samples.md)   
 [MFC示例TESTHELP](../../top/visual-cpp-samples.md)   
 [COlePropertyPage Class](../../mfc/reference/colepropertypage-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFontHolder Class](../../mfc/reference/cfontholder-class.md)   
 [CPictureHolder Class](../../mfc/reference/cpictureholder-class.md)