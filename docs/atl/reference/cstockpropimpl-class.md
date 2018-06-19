---
title: CStockPropImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
dev_langs:
- C++
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f12cff287b9a9c74b548a08d9a03f73869671fc1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366570"
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl 类
此类提供支持常用属性值的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE CStockPropImpl : public IDispatchImpl<InterfaceName, piid,
 plibid,
    wMajor,
 wMinor,
    tihclass>
```   
  
#### <a name="parameters"></a>参数  
 `T`  
 类实现控件，并从派生`CStockPropImpl`。  
  
 `InterfaceName`  
 双重接口公开常用的属性。  
  
 `piid`  
 指向 IID 的`InterfaceName`。  
  
 `plibid`  
 指向包含的定义的类型库的 LIBID `InterfaceName`。  
  
 `wMajor`  
 类型库的主版本。 默认值为 1。  
  
 `wMinor`  
 类型库的次版本。 默认值为 0。  
  
 `tihclass`  
 用于管理的类型信息的类`T`。 默认值为 `CComTypeInfoHolder`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|[get_Appearance](#get_appearance)|调用此方法来获取的绘制样式，该控件使用的例如，平面或三维。|  
|[get_AutoSize](#get_autosize)|调用此方法以获取用于指示该控件不能为任何其他大小的标志的状态。|  
|[get_BackColor](#get_backcolor)|调用此方法以获取控件的背景色。|  
|[get_BackStyle](#get_backstyle)|调用此方法以获取控件的背景样式，透明或不透明。|  
|[get_BorderColor](#get_bordercolor)|调用此方法以获取控件的边框颜色。|  
|[get_BorderStyle](#get_borderstyle)|调用此方法以获取控件的边框样式。|  
|[get_BorderVisible](#get_bordervisible)|调用此方法以获取用于指示控件的边框是否可见的标志的状态。|  
|[get_BorderWidth](#get_borderwidth)|调用此方法以获取控件的边框的宽度 （以像素为单位）。|  
|[get_Caption](#get_caption)|调用此方法以获取指定对象的标题中的文本。|  
|[get_DrawMode](#get_drawmode)|调用此方法以获取控件的绘制模式，例如，异或笔或反转颜色。|  
|[get_DrawStyle](#get_drawstyle)|例如，调用此方法以获取控件的绘制样式，实线、 虚线，线或点。|  
|[get_DrawWidth](#get_drawwidth)|调用此方法以获取该控件的绘制方法所用的绘制宽度 （以像素为单位）。|  
|[get_Enabled](#get_enabled)|调用此方法以获取用于指示是否启用的控件的标志的状态。|  
|[get_FillColor](#get_fillcolor)|调用此方法以获取控件的填充颜色。|  
|[get_FillStyle](#get_fillstyle)|例如，调用此方法以获取控件的填充样式，纯色、 透明或斜线。|  
|[get_Font](#get_font)|调用此方法以获取指向控件的字体属性的指针。|  
|[get_ForeColor](#get_forecolor)|调用此方法以获取控件的前景色。|  
|[get_HWND](#get_hwnd)|调用此方法以获取与控件关联的窗口句柄。|  
|[get_MouseIcon](#get_mouseicon)|调用此方法以获取图形 （图标、 位图或图元文件） 鼠标位于控件上方时要显示的图片属性。|  
|[get_MousePointer](#get_mousepointer)|调用此方法要获取类型的鼠标指针时鼠标位于此控件，例如显示、 箭头、 十字形或沙漏。|  
|[get_Picture](#get_picture)|调用此方法以获取指向图形 （图标、 位图或图元文件） 要显示的图片属性的指针。|  
|[get_ReadyState](#get_readystate)|加载或加载，例如，调用此方法以获取控件的就绪状态。|  
|[get_TabStop](#get_tabstop)|调用此方法以获取用于指示控件是否制表位的标志。|  
|[get_Text](#get_text)|调用此方法以获取与该控件显示的文本。|  
|[getvalid](#get_valid)|调用此方法以获取用于指示控件是否有效的标志的状态。|  
|[get_Window](#get_window)|调用此方法以获取与控件关联的窗口句柄。 等于[CStockPropImpl::get_HWND](#get_hwnd)。|  
|[put_Appearance](#put_appearance)|调用此方法以设置的绘制样式，该控件使用的例如，平面或三维。|  
|[put_AutoSize](#put_autosize)|调用此方法以设置用于指示该控件不能为任何其他大小的标志的值。|  
|[put_BackColor](#put_backcolor)|调用此方法以设置控件的背景色。|  
|[put_BackStyle](#put_backstyle)|调用此方法以设置控件的背景样式。|  
|[put_BorderColor](#put_bordercolor)|调用此方法以设置控件的边框颜色。|  
|[put_BorderStyle](#put_borderstyle)|调用此方法以设置控件的边框样式。|  
|[put_BorderVisible](#put_bordervisible)|调用此方法以设置用于指示控件的边框是否可见的标志的值。|  
|[put_BorderWidth](#put_borderwidth)|调用此方法以设置控件的边框的宽度。|  
|[put_Caption](#put_caption)|调用此方法以设置与该控件显示的文本。|  
|[put_DrawMode](#put_drawmode)|调用此方法以设置控件的绘制模式，例如，异或笔或反转颜色。|  
|[put_DrawStyle](#put_drawstyle)|例如，调用此方法以设置控件的绘制样式，实线、 虚线，线或点。|  
|[put_DrawWidth](#put_drawwidth)|调用此方法以设置由该控件的绘制方法的宽度 （以像素为单位）。|  
|[put_Enabled](#put_enabled)|调用此方法以设置用于指示是否启用的控件的标志。|  
|[put_FillColor](#put_fillcolor)|调用此方法以设置控件的填充颜色。|  
|[put_FillStyle](#put_fillstyle)|例如，调用此方法以设置控件的填充样式，纯色、 透明或斜线。|  
|[put_Font](#put_font)|调用此方法以设置控件的字体属性。|  
|[put_ForeColor](#put_forecolor)|调用此方法以设置控件的前景色。|  
|[put_HWND](#put_hwnd)|此方法返回 E_FAIL。|  
|[put_MouseIcon](#put_mouseicon)|调用此方法以设置的图形 （图标、 位图或图元文件） 鼠标位于控件上方时要显示的图片属性。|  
|[put_MousePointer](#put_mousepointer)|调用此方法以设置鼠标指针时鼠标位于此控件，例如显示、 箭头、 十字形或沙漏的类型。|  
|[put_Picture](#put_picture)|调用此方法以设置图形 （图标、 位图或图元文件） 要显示的图片属性。|  
|[put_ReadyState](#put_readystate)|例如，调用此方法以设置控件的就绪状态，加载或加载。|  
|[put_TabStop](#put_tabstop)|调用此方法以设置标志，该值指示控件是否制表位的值。|  
|[put_Text](#put_text)|调用此方法以设置与该控件显示的文本。|  
|[putvalid](#put_valid)|调用此方法以设置指示控件是否为有效的标志。|  
|[put_Window](#put_window)|此方法调用[CStockPropImpl::put_HWND](#put_hwnd)，这将返回 E_FAIL。|  
|[putref_Font](#putref_font)|调用此方法以设置控件的字体属性，引用计数。|  
|[putref_MouseIcon](#putref_mouseicon)|调用此方法以设置的图形 （图标、 位图或图元文件） 鼠标位于控件上方时要显示的图片属性，引用计数。|  
|[putref_Picture](#putref_picture)|调用此方法以设置图形 （图标、 位图或图元文件） 要显示的图片属性，引用计数。|  
  
## <a name="remarks"></a>备注  
 `CStockPropImpl` 提供**放**和**获取**每个常用的属性的方法。 这些方法提供必需设置或获取与每个属性关联的数据成员并将通知和任何属性更改时，同步与容器的代码。  
  
 Visual c + + 的通过其向导的常用属性页提供支持。 有关向控件添加常用属性的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。  
  
 为了向后兼容，`CStockPropImpl`还公开`get_Window`和`put_Window`只需调用的方法`get_HWND`和`put_HWND`分别。 默认实现`put_HWND`返回**E_FAIL**由于`HWND`应为只读属性。  
  
 以下属性也存在**putref**实现：  
  
-   字体  
  
-   MouseIcon  
  
-   Picture  
  
 相同的三个常用属性需要其对应的数据成员的类型为`CComPtr`或某些其他类，提供正确的接口引用计数通过赋值运算符。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `T`  
  
 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)  
  
 `CStockPropImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="get_appearance"></a>  CStockPropImpl::get_Appearance  
 调用此方法来获取的绘制样式，该控件使用的例如，平面或三维。  
  
```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```  
  
### <a name="parameters"></a>参数  
 *pnAppearance*  
 接收控件的绘制样式的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_autosize"></a>  CStockPropImpl::get_AutoSize  
 调用此方法以获取用于指示该控件不能为任何其他大小的标志的状态。  
  
```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```  
  
### <a name="parameters"></a>参数  
 *pbAutoSize*  
 将接收到标志状态的变量。 TRUE 表示该控件不能为任何其他大小。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_backcolor"></a>  CStockPropImpl::get_BackColor  
 调用此方法以获取控件的背景色。  
  
```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```  
  
### <a name="parameters"></a>参数  
 *pclrBackColor*  
 接收控件的背景色的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_backstyle"></a>  CStockPropImpl::get_BackStyle  
 调用此方法以获取控件的背景样式，透明或不透明。  
  
```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```  
  
### <a name="parameters"></a>参数  
 *pnBackStyle*  
 接收控件的背景样式的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_bordercolor"></a>  CStockPropImpl::get_BorderColor  
 调用此方法以获取控件的边框颜色。  
  
```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```  
  
### <a name="parameters"></a>参数  
 *pclrBorderColor*  
 接收控件的边框颜色的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_borderstyle"></a>  CStockPropImpl::get_BorderStyle  
 调用此方法以获取控件的边框样式。  
  
```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```  
  
### <a name="parameters"></a>参数  
 *pnBorderStyle*  
 接收控件的边框样式的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_bordervisible"></a>  CStockPropImpl::get_BorderVisible  
 调用此方法以获取用于指示控件的边框是否可见的标志的状态。  
  
```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```  
  
### <a name="parameters"></a>参数  
 *pbBorderVisible*  
 将接收到标志状态的变量。 TRUE 表示控件的边框是可见。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_borderwidth"></a>  CStockPropImpl::get_BorderWidth  
 调用此方法以获取控件的边框的宽度。  
  
```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```  
  
### <a name="parameters"></a>参数  
 *pnBorderWidth*  
 接收控件的边框宽度的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_caption"></a>  CStockPropImpl::get_Caption  
 调用此方法以获取指定对象的标题中的文本。  
  
```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```  
  
### <a name="parameters"></a>参数  
 *pbstrCaption*  
 要与该控件显示的文本。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_drawmode"></a>  CStockPropImpl::get_DrawMode  
 调用此方法以获取控件的绘制模式，例如，异或笔或反转颜色。  
  
```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```  
  
### <a name="parameters"></a>参数  
 *pnDrawMode*  
 接收控件的绘制模式的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_drawstyle"></a>  CStockPropImpl::get_DrawStyle  
 例如，调用此方法以获取控件的绘制样式，实线、 虚线，线或点。  
  
```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```  
  
### <a name="parameters"></a>参数  
 *pnDrawStyle*  
 接收控件的绘制样式的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_drawwidth"></a>  CStockPropImpl::get_DrawWidth  
 调用此方法以获取该控件的绘制方法所用的绘制宽度 （以像素为单位）。  
  
```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```  
  
### <a name="parameters"></a>参数  
 *pnDrawWidth*  
 接收控件的宽度值，以像素为单位的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_enabled"></a>  CStockPropImpl::get_Enabled  
 调用此方法以获取用于指示是否启用的控件的标志的状态。  
  
```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```  
  
### <a name="parameters"></a>参数  
 `pbEnabled`  
 将接收到标志状态的变量。 TRUE 表示已启用该控件。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_fillcolor"></a>  CStockPropImpl::get_FillColor  
 调用此方法以获取控件的填充颜色。  
  
```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```  
  
### <a name="parameters"></a>参数  
 *pclrFillColor*  
 接收控件的填充颜色的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_fillstyle"></a>  CStockPropImpl::get_FillStyle  
 例如，调用此方法以获取控件的填充样式，纯色、 透明或剖面线。  
  
```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```  
  
### <a name="parameters"></a>参数  
 *pnFillStyle*  
 接收控件的填充样式的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_font"></a>  CStockPropImpl::get_Font  
 调用此方法以获取指向控件的字体属性的指针。  
  
```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>参数  
 `ppFont`  
 接收指向控件的字体属性的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_forecolor"></a>  CStockPropImpl::get_ForeColor  
 调用此方法以获取控件的前景色。  
  
```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```  
  
### <a name="parameters"></a>参数  
 *pclrForeColor*  
 接收的控件前景色的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_hwnd"></a>  CStockPropImpl::get_HWND  
 调用此方法以获取与控件关联的窗口句柄。  
  
```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>参数  
 `phWnd`  
 与控件关联的窗口句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_mouseicon"></a>  CStockPropImpl::get_MouseIcon  
 调用此方法以获取图形 （图标、 位图或图元文件） 鼠标位于控件上方时要显示的图片属性。  
  
```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>参数  
 `ppPicture`  
 接收一个指针，该图形的图片属性的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_mousepointer"></a>  CStockPropImpl::get_MousePointer  
 调用此方法要获取类型的鼠标指针时鼠标位于此控件，例如显示、 箭头、 十字形或沙漏。  
  
```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```  
  
### <a name="parameters"></a>参数  
 *pnMousePointer*  
 接收鼠标指针的类型的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_picture"></a>  CStockPropImpl::get_Picture  
 调用此方法以获取指向图形 （图标、 位图或图元文件） 要显示的图片属性的指针。  
  
```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>参数  
 `ppPicture`  
 接收一个指针，到图片属性的变量。 请参阅[IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762)有关详细信息。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_readystate"></a>  CStockPropImpl::get_ReadyState  
 加载或加载，例如，调用此方法以获取控件的就绪状态。  
  
```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```  
  
### <a name="parameters"></a>参数  
 *pnReadyState*  
 接收控件的就绪状态的变量。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_tabstop"></a>  CStockPropImpl::get_TabStop  
 调用此方法以获取用于指示控件是否制表位的标志的状态。  
  
```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```  
  
### <a name="parameters"></a>参数  
 *pbTabStop*  
 将接收到标志状态的变量。 TRUE 表示该控件是一个制表位。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_text"></a>  CStockPropImpl::get_Text  
 调用此方法以获取与该控件显示的文本。  
  
```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```  
  
### <a name="parameters"></a>参数  
 *pbstrText*  
 与该控件显示的文本。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_valid"></a>  CStockPropImpl::getvalid  
 调用此方法以获取用于指示控件是否有效的标志的状态。  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```  
  
### <a name="parameters"></a>参数  
 *pbValid*  
 将接收到标志状态的变量。 TRUE 指示控件有效。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="get_window"></a>  CStockPropImpl::get_Window  
 调用此方法以获取与控件关联的窗口句柄。 等于[CStockPropImpl::get_HWND](#get_hwnd)。  
  
```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>参数  
 `phWnd`  
 与控件关联的窗口句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_appearance"></a>  CStockPropImpl::put_Appearance  
 调用此方法以设置的绘制样式，该控件使用的例如，平面或三维。  
  
```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```  
  
### <a name="parameters"></a>参数  
 `nAppearance`  
 使用由该控件的新的绘制样式。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_autosize"></a>  CStockPropImpl::put_AutoSize  
 调用此方法以设置该标志指示是否控件不能为任何其他大小的值。  
  
```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```  
  
### <a name="parameters"></a>参数  
 *bAutoSize*  
 如果控件不能为任何其他大小，则为 TRUE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_backcolor"></a>  CStockPropImpl::put_BackColor  
 调用此方法以设置控件的背景色。  
  
```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```  
  
### <a name="parameters"></a>参数  
 *clrBackColor*  
 新的控件背景色。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_backstyle"></a>  CStockPropImpl::put_BackStyle  
 调用此方法以设置控件的背景样式。  
  
```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```  
  
### <a name="parameters"></a>参数  
 *nBackStyle*  
 新控件的背景样式。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_bordercolor"></a>  CStockPropImpl::put_BorderColor  
 调用此方法以设置控件的边框颜色。  
  
```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```  
  
### <a name="parameters"></a>参数  
 *clrBorderColor*  
 新的边框颜色。 OLE_COLOR 数据类型在内部表示以 32 位长整型。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_borderstyle"></a>  CStockPropImpl::put_BorderStyle  
 调用此方法以设置控件的边框样式。  
  
```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```  
  
### <a name="parameters"></a>参数  
 *nBorderStyle*  
 新的边框样式。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_bordervisible"></a>  CStockPropImpl::put_BorderVisible  
 调用此方法以设置用于指示控件的边框是否可见的标志的值。  
  
```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```  
  
### <a name="parameters"></a>参数  
 *bBorderVisible*  
 如果边框可见，则为 TRUE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_borderwidth"></a>  CStockPropImpl::put_BorderWidth  
 调用此方法以设置控件的边框的宽度。  
  
```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```  
  
### <a name="parameters"></a>参数  
 `nBorderWidth`  
 新控件的边框宽度。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_caption"></a>  CStockPropImpl::put_Caption  
 调用此方法以设置与该控件显示的文本。  
  
```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```  
  
### <a name="parameters"></a>参数  
 *bstrCaption*  
 要与该控件显示的文本。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_drawmode"></a>  CStockPropImpl::put_DrawMode  
 调用此方法以设置控件的绘制模式，例如，异或笔或反转颜色。  
  
```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```  
  
### <a name="parameters"></a>参数  
 `nDrawMode`  
 控件的新绘图模式。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_drawstyle"></a>  CStockPropImpl::put_DrawStyle  
 例如，调用此方法以设置控件的绘制样式，实线、 虚线，线或点。  
  
```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```  
  
### <a name="parameters"></a>参数  
 *nDrawStyle*  
 新控件绘制样式。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_drawwidth"></a>  CStockPropImpl::put_DrawWidth  
 调用此方法以设置由该控件的绘制方法的宽度 （以像素为单位）。  
  
```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```  
  
### <a name="parameters"></a>参数  
 *nDrawWidth*  
 新的宽度将由该控件的绘制方法。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_enabled"></a>  CStockPropImpl::put_Enabled  
 调用此方法以设置用于指示是否启用的控件的标志的值。  
  
```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```  
  
### <a name="parameters"></a>参数  
 `bEnabled`  
 如果启用该控件，则为 TRUE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_fillcolor"></a>  CStockPropImpl::put_FillColor  
 调用此方法以设置控件的填充颜色。  
  
```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```  
  
### <a name="parameters"></a>参数  
 *clrFillColor*  
 新控件的填充颜色。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_fillstyle"></a>  CStockPropImpl::put_FillStyle  
 例如，调用此方法以设置控件的填充样式，纯色、 透明或斜线。  
  
```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```  
  
### <a name="parameters"></a>参数  
 *nFillStyle*  
 新控件的填充样式。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_font"></a>  CStockPropImpl::put_Font  
 调用此方法以设置控件的字体属性。  
  
```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>参数  
 `pFont`  
 控件的字体属性指向的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_forecolor"></a>  CStockPropImpl::put_ForeColor  
 调用此方法以设置控件的前景色。  
  
```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```  
  
### <a name="parameters"></a>参数  
 *clrForeColor*  
 新的控件的前景颜色。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_hwnd"></a>  CStockPropImpl::put_HWND  
 此方法返回 E_FAIL。  
  
```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```  
  
### <a name="parameters"></a>参数  
 */\* hWnd \*/*  
 保留。  
  
### <a name="return-value"></a>返回值  
 返回 E_FAIL。  
  
### <a name="remarks"></a>备注  
 窗口句柄是只读的值。  
  
##  <a name="put_mouseicon"></a>  CStockPropImpl::put_MouseIcon  
 调用此方法以设置的图形 （图标、 位图或图元文件） 鼠标位于控件上方时要显示的图片属性。  
  
```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>参数  
 `pPicture`  
 指向图形的图片属性的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_mousepointer"></a>  CStockPropImpl::put_MousePointer  
 调用此方法以设置鼠标指针时鼠标位于此控件，例如显示、 箭头、 十字形或沙漏的类型。  
  
```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```  
  
### <a name="parameters"></a>参数  
 *nMousePointer*  
 鼠标指针的类型。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_picture"></a>  CStockPropImpl::put_Picture  
 调用此方法以设置图形 （图标、 位图或图元文件） 要显示的图片属性。  
  
```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>参数  
 `pPicture`  
 图片的属性指向的指针。 请参阅[IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762)有关详细信息。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_readystate"></a>  CStockPropImpl::put_ReadyState  
 例如，调用此方法以设置控件的就绪状态，加载或加载。  
  
```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```  
  
### <a name="parameters"></a>参数  
 *nReadyState*  
 控件的就绪状态。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_tabstop"></a>  CStockPropImpl::put_TabStop  
 调用此方法以设置用于指示控件是否制表位的标志。  
  
```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```  
  
### <a name="parameters"></a>参数  
 *bTabStop*  
 如果控件是一个制表位，则为 TRUE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_text"></a>  CStockPropImpl::put_Text  
 调用此方法以设置与该控件显示的文本。  
  
```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```  
  
### <a name="parameters"></a>参数  
 `bstrText`  
 与该控件显示的文本。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_valid"></a>  CStockPropImpl::putvalid  
 调用此方法以设置指示控件是否为有效的标志。  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```  
  
### <a name="parameters"></a>参数  
 *bValid*  
 如果控件是有效，则为 TRUE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="put_window"></a>  CStockPropImpl::put_Window  
 此方法调用[CStockPropImpl::put_HWND](#put_hwnd)，这将返回 E_FAIL。  
  
```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 窗口句柄。  
  
### <a name="return-value"></a>返回值  
 返回 E_FAIL。  
  
### <a name="remarks"></a>备注  
 窗口句柄是只读的值。  
  
##  <a name="putref_font"></a>  CStockPropImpl::putref_Font  
 调用此方法以设置控件的字体属性，引用计数。  
  
```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>参数  
 `pFont`  
 控件的字体属性指向的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 与相同[CStockPropImpl::put_Font](#put_font)，但使用引用计数。  
  
##  <a name="putref_mouseicon"></a>  CStockPropImpl::putref_MouseIcon  
 调用此方法以设置的图形 （图标、 位图或图元文件） 鼠标位于控件上方时要显示的图片属性，引用计数。  
  
```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>参数  
 `pPicture`  
 指向图形的图片属性的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 与相同[CStockPropImpl::put_MouseIcon](#put_mouseicon)，但使用引用计数。  
  
##  <a name="putref_picture"></a>  CStockPropImpl::putref_Picture  
 调用此方法以设置图形 （图标、 位图或图元文件） 要显示的图片属性，引用计数。  
  
```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>参数  
 `pPicture`  
 图片的属性指向的指针。 请参阅[IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762)有关详细信息。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 与相同[CStockPropImpl::put_Picture](#put_picture)，但使用引用计数。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)
