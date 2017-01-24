---
title: "CStockPropImpl Class | Microsoft Docs"
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
  - "CStockPropImpl"
  - "ATL::CStockPropImpl"
  - "ATL.CStockPropImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控件 [ATL], 常用属性"
  - "CStockPropImpl class"
  - "常用属性, ATL 控件"
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStockPropImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类支持常用属性值的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T,  
class InterfaceName,   
const IID* piid= &_ATL_IIDOF(InterfaceName),   
const GUID* plibid= &CComModule::m_libid,   
WORD wMajor= 1,  
WORD wMinor= 0,   
class tihclass= CcomTypeInfoHolder  
>  
class ATL_NO_VTABLE CStockPropImpl :  
public IDispatchImpl< InterfaceName, piid, plibid, wMajor,  
   wMinor, tihclass>  
```  
  
#### 参数  
 `T`  
 实现控件和从派生 `CStockPropImpl`的选件类。  
  
 `InterfaceName`  
 显示常用属性的双重接口。  
  
 `piid`  
 为 `InterfaceName`IID的指针。  
  
 `plibid`  
 对类型包含 `InterfaceName`定义的库的LIBID的指针。  
  
 `wMajor`  
 类型库的主版本。  默认值为 1。  
  
 `wMinor`  
 类型库的次版本。  默认值为 0。  
  
 `tihclass`  
 用于的选件类管理 `T`的类型信息。  默认值为 `CComTypeInfoHolder`。  
  
## 成员  
  
### 公共方法  
  
|||  
|-|-|  
|[get\_Appearance](../Topic/CStockPropImpl::get_Appearance.md)|调用此方法获取绘制样式使用控件，例如，平面或三维。|  
|[get\_AutoSize](../Topic/CStockPropImpl::get_AutoSize.md)|调用此方法获取指示该值指示控件是否不能是其他范围。|  
|[get\_BackColor](../Topic/CStockPropImpl::get_BackColor.md)|调用此方法获取控件的背景色。|  
|[get\_BackStyle](../Topic/CStockPropImpl::get_BackStyle.md)|调用此方法获取控件的背景样式，透明或不透明度。|  
|[get\_BorderColor](../Topic/CStockPropImpl::get_BorderColor.md)|调用此方法获取控件的边框颜色。|  
|[get\_BorderStyle](../Topic/CStockPropImpl::get_BorderStyle.md)|调用此方法获取控件的边框样式。|  
|[get\_BorderVisible](../Topic/CStockPropImpl::get_BorderVisible.md)|调用此方法获取指示该值指示在控件的边框是否可见。|  
|[get\_BorderWidth](../Topic/CStockPropImpl::get_BorderWidth.md)|调用此方法获取宽度\(以像素为单位\)的控件的边框。|  
|[get\_Caption](../Topic/CStockPropImpl::get_Caption.md)|调用此方法获取该文本指定在对象的声明。|  
|[get\_DrawMode](../Topic/CStockPropImpl::get_DrawMode.md)|调用此方法获取控件的绘制模式，例如，"异或"笔或反转颜色。|  
|[get\_DrawStyle](../Topic/CStockPropImpl::get_DrawStyle.md)|调用此方法获取控件的绘制样式，例如，纯，虚线或虚线。|  
|[get\_DrawWidth](../Topic/CStockPropImpl::get_DrawWidth.md)|调用此方法获取绘图宽度\(以像素为单位\)使用控件的绘制方法。|  
|[get\_Enabled](../Topic/CStockPropImpl::get_Enabled.md)|调用此方法获取指示该值指示控件是否启用。|  
|[get\_FillColor](../Topic/CStockPropImpl::get_FillColor.md)|调用此方法获取控件的填充颜色。|  
|[get\_FillStyle](../Topic/CStockPropImpl::get_FillStyle.md)|调用此方法获取控件的填充样式，例如，纯，透明、跨平台的涂绘制。|  
|[get\_Font](../Topic/CStockPropImpl::get_Font.md)|调用此方法获取指向控件的字体属性。|  
|[get\_ForeColor](../Topic/CStockPropImpl::get_ForeColor.md)|调用此方法获取控件的前景色。|  
|[get\_HWND](../Topic/CStockPropImpl::get_HWND.md)|调用此方法获取窗口句柄与控件关联。|  
|[get\_MouseIcon](../Topic/CStockPropImpl::get_MouseIcon.md)|调用此方法获取\(图标、位图、图元文件\)的要显示的图片属性图像，当鼠标位于控件时。|  
|[get\_MousePointer](../Topic/CStockPropImpl::get_MousePointer.md)|当鼠标位于控件，例如，箭头、跨或一个沙漏时，调用此方法获取鼠标指针的类型显示。|  
|[get\_Picture](../Topic/CStockPropImpl::get_Picture.md)|调用此方法获取指向\(图标、位图、图元文件\)的要显示的图片属性图像。|  
|[get\_ReadyState](../Topic/CStockPropImpl::get_ReadyState.md)|调用此方法获取控件的就绪状态，例如，加载或加载。|  
|[get\_TabStop](../Topic/CStockPropImpl::get_TabStop.md)|调用此方法获取指示的标志控件是否是制表位。|  
|[get\_Text](../Topic/CStockPropImpl::get_Text.md)|调用此方法获取使用控件显示的文本。|  
|[get\_Valid](../Topic/CStockPropImpl::get_Valid.md)|调用此方法获取指示该值指示控件是否有效。|  
|[get\_Window](../Topic/CStockPropImpl::get_Window.md)|调用此方法获取窗口句柄与控件关联。  与 [CStockPropImpl::get\_HWND](../Topic/CStockPropImpl::get_HWND.md)。|  
|[put\_Appearance](../Topic/CStockPropImpl::put_Appearance.md)|调用此方法将控件，例如，平面或三维使用进行绘制样式。|  
|[put\_AutoSize](../Topic/CStockPropImpl::put_AutoSize.md)|调用此方法设置一个标志的值控件是否不能是其他范围。|  
|[put\_BackColor](../Topic/CStockPropImpl::put_BackColor.md)|调用此方法将控件的背景色。|  
|[put\_BackStyle](../Topic/CStockPropImpl::put_BackStyle.md)|调用此方法将控件的背景样式。|  
|[put\_BorderColor](../Topic/CStockPropImpl::put_BorderColor.md)|调用此方法将控件的边框颜色。|  
|[put\_BorderStyle](../Topic/CStockPropImpl::put_BorderStyle.md)|调用此方法将控件的边框样式。|  
|[put\_BorderVisible](../Topic/CStockPropImpl::put_BorderVisible.md)|调用此方法设置一个标志的值的控件的边框是否可见。|  
|[put\_BorderWidth](../Topic/CStockPropImpl::put_BorderWidth.md)|调用此方法将控件的边框的宽度。|  
|[put\_Caption](../Topic/CStockPropImpl::put_Caption.md)|调用此方法设置中显示的文本与控件。|  
|[put\_DrawMode](../Topic/CStockPropImpl::put_DrawMode.md)|调用此方法将控件的绘图模式，例如，"异或"笔或反转颜色。|  
|[put\_DrawStyle](../Topic/CStockPropImpl::put_DrawStyle.md)|调用此方法将控件的绘图样式，例如，纯，虚线或虚线。|  
|[put\_DrawWidth](../Topic/CStockPropImpl::put_DrawWidth.md)|调用此方法将控件的绘制方法\(以像素为单位\)使用的宽度。|  
|[put\_Enabled](../Topic/CStockPropImpl::put_Enabled.md)|调用此方法设置一个标志控件是否启用。|  
|[put\_FillColor](../Topic/CStockPropImpl::put_FillColor.md)|调用此方法将控件的填充颜色。|  
|[put\_FillStyle](../Topic/CStockPropImpl::put_FillStyle.md)|调用此方法将控件的填充样式，例如，纯，透明、跨平台的涂绘制。|  
|[put\_Font](../Topic/CStockPropImpl::put_Font.md)|调用此方法将控件的字体属性。|  
|[put\_ForeColor](../Topic/CStockPropImpl::put_ForeColor.md)|调用此方法将控件的前景色。|  
|[put\_HWND](../Topic/CStockPropImpl::put_HWND.md)|此方法返回E\_FAIL。|  
|[put\_MouseIcon](../Topic/CStockPropImpl::put_MouseIcon.md)|调用此方法设置\(图标、位图、图元文件\)的要显示的图片属性图像，当鼠标位于控件时。|  
|[put\_MousePointer](../Topic/CStockPropImpl::put_MousePointer.md)|当鼠标位于控件，例如，箭头、跨或一个沙漏时，调用此方法定位到突出显示的鼠标指针的类型。|  
|[put\_Picture](../Topic/CStockPropImpl::put_Picture.md)|调用此方法设置\(图标、位图、图元文件\)的要显示的图片属性图像。|  
|[put\_ReadyState](../Topic/CStockPropImpl::put_ReadyState.md)|调用此方法将控件的就绪状态，例如，加载或加载。|  
|[put\_TabStop](../Topic/CStockPropImpl::put_TabStop.md)|调用此方法设置一个标志的值控件是否是制表位。|  
|[put\_Text](../Topic/CStockPropImpl::put_Text.md)|调用此方法将使用控件显示的文本。|  
|[put\_Valid](../Topic/CStockPropImpl::put_Valid.md)|调用此方法设置一个标志控件是否有效。|  
|[put\_Window](../Topic/CStockPropImpl::put_Window.md)|此方法调用 [CStockPropImpl::put\_HWND](../Topic/CStockPropImpl::put_HWND.md)，返回E\_FAIL。|  
|[putref\_Font](../Topic/CStockPropImpl::putref_Font.md)|调用此方法设置控件的字体属性，而引用计数。|  
|[putref\_MouseIcon](../Topic/CStockPropImpl::putref_MouseIcon.md)|调用此方法设置要显示的图像\(图标、位图、图元文件\)的图片属性，当鼠标位于控件时，使用引用计数。|  
|[putref\_Picture](../Topic/CStockPropImpl::putref_Picture.md)|调用此方法设置要显示的图像\(图标、位图、图元文件\)的图片属性，使用引用计数。|  
  
## 备注  
 `CStockPropImpl` 为每个常用属性提供 **put** 和 **get** 方法。  这些方法提供必要的代码设置或数据成员与每个属性以及容器通知和同步的访问，当所有属性更改。  
  
 Visual C\+\+提供常用属性支持通过其向导。  有关添加常用属性的更多信息传递给控件，请参见 [ATL教程](../../atl/active-template-library-atl-tutorial.md)。  
  
 为了实现向后兼容，`CStockPropImpl` 分别还显示 `get_Window` 和调用 `get_HWND` 和 `put_HWND`的 `put_Window` 方法。  因为 `HWND` 应是只读属性，`put_HWND` 的默认实现返回 **E\_FAIL**。  
  
 以下属性还有一个 **putref** 实现:  
  
-   字体  
  
-   MouseIcon  
  
-   图片  
  
 同样三个常用属性需要其对应的数据成员是类型 `CComPtr` 或提供正确的接口的其他选件类通过赋值运算符引用计数。  
  
## 继承层次结构  
 `T`  
  
 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)  
  
 `CStockPropImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [IDispatchImpl Class](../../atl/reference/idispatchimpl-class.md)