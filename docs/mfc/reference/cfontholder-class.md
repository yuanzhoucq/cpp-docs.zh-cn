---
title: "CFontHolder 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
dev_langs:
- C++
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd5f13f2ec48f38fde140361d31a5e08ae6228b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cfontholder-class"></a>CFontHolder 类
实现常用字体属性并封装 Windows 字体对象和 `IFont` 接口的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CFontHolder  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFontHolder::CFontHolder](#cfontholder)|构造 `CFontHolder` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFontHolder::GetDisplayString](#getdisplaystring)|检索容器的属性浏览器中显示的字符串。|  
|[CFontHolder::GetFontDispatch](#getfontdispatch)|返回的字体`IDispatch`接口。|  
|[CFontHolder::GetFontHandle](#getfonthandle)|返回一个 Windows 字体的句柄。|  
|[CFontHolder::InitializeFont](#initializefont)|初始化`CFontHolder`对象。|  
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|检索相关字体的信息。|  
|[CFontHolder::ReleaseFont](#releasefont)|断开连接`CFontHolder`对象`IFont`和`IFontNotification`接口。|  
|[CFontHolder::Select](#select)|选择字体资源入设备上下文。|  
|[CFontHolder::SetFont](#setfont)|连接`CFontHolder`对象传递给`IFont`接口。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CFontHolder::m_pFont](#m_pfont)|指向的指针`CFontHolder`对象的`IFont`接口。|  
  
## <a name="remarks"></a>备注  
 `CFontHolder`没有基类。  
  
 使用此类实现为您的控件的自定义字体属性。 有关创建此类属性的信息，请参阅文章[ActiveX 控件： 使用字体](../../mfc/mfc-activex-controls-using-fonts.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CFontHolder`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxctl.h  
  
##  <a name="cfontholder"></a>CFontHolder::CFontHolder  
 构造 `CFontHolder` 对象。  
  
```  
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```  
  
### <a name="parameters"></a>参数  
 *pNotify*  
 指向字体的`IPropertyNotifySink`接口。  
  
### <a name="remarks"></a>备注  
 必须调用`InitializeFont`初始化生成的对象，然后再使用它。  
  
##  <a name="getdisplaystring"></a>CFontHolder::GetDisplayString  
 检索可以在容器的属性浏览器中显示的字符串。  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>参数  
 `strValue`  
 引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)即来保存显示字符串。  
  
### <a name="return-value"></a>返回值  
 如果成功检索字符串; 则为非 0否则为 0。  
  
##  <a name="getfontdispatch"></a>CFontHolder::GetFontDispatch  
 调用此函数可检索指向字体的调度接口的指针。  
  
```  
LPFONTDISP GetFontDispatch();
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`CFontHolder`对象的**IFontDisp**接口。 请注意，该函数的调用`GetFontDispatch`必须调用`IUnknown::Release`上完成它此接口指针。  
  
### <a name="remarks"></a>备注  
 调用`InitializeFont`之前调用`GetFontDispatch`。  
  
##  <a name="getfonthandle"></a>CFontHolder::GetFontHandle  
 调用此函数可获取到 Windows 字体的句柄。  
  
```  
HFONT GetFontHandle();

 
HFONT GetFontHandle(
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>参数  
 `cyLogical`  
 逻辑单位，在其中绘制控件的矩形的高度。  
  
 `cyHimetric`  
 高度，在`MM_HIMETRIC`单位的控件。  
  
### <a name="return-value"></a>返回值  
 字体对象中; 的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 比率`cyLogical`和`cyHimetric`用于计算正确的显示大小，逻辑单位，以表示字体的磅值`MM_HIMETRIC`单位：  
  
 显示大小 = ( `cyLogical`  /  `cyHimetric`) X 字体大小  
  
 不带任何参数的版本正确设置大小，该屏幕的字体中返回的句柄。  
  
##  <a name="initializefont"></a>CFontHolder::InitializeFont  
 初始化`CFontHolder`对象。  
  
```  
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,  
    LPDISPATCH pFontDispAmbient = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pFontDesc`  
 指向字体描述结构 ( [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782))，它指定字体的特征。  
  
 `pFontDispAmbient`  
 指向容器的环境字体属性。  
  
### <a name="remarks"></a>备注  
 如果`pFontDispAmbient`不**NULL**、`CFontHolder`对象连接到的克隆`IFont`由容器的环境字体属性的接口。  
  
 如果`pFontDispAmbient`是**NULL**，从指向字体说明创建一个新的字体对象`pFontDesc`或者，如果`pFontDesc`是**NULL**，从默认说明。  
  
 在构造之后调用此函数`CFontHolder`对象。  
  
##  <a name="m_pfont"></a>CFontHolder::m_pFont  
 指向的指针`CFontHolder`对象的`IFont`接口。  
  
```  
LPFONT m_pFont;  
```  
  
##  <a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics  
 检索信息由物理字体`CFontHolder`对象。  
  
```  
void QueryTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>参数  
 `lptm`  
 指向的指针[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)将接收信息的结构。  
  
##  <a name="releasefont"></a>CFontHolder::ReleaseFont  
 此函数断开连接`CFontHolder`对象从其`IFont`接口。  
  
```  
void ReleaseFont();
```  
  
##  <a name="select"></a>CFontHolder::Select  
 调用此函数可在指定的设备上下文选择控件的字体。  
  
```  
CFont* Select(
    CDC* pDC,  
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 在其中选择字体的设备上下文。  
  
 `cyLogical`  
 逻辑单位，在其中绘制控件的矩形的高度。  
  
 `cyHimetric`  
 高度，在`MM_HIMETRIC`单位的控件。  
  
### <a name="return-value"></a>返回值  
 指向要替换的字体的指针。  
  
### <a name="remarks"></a>备注  
 请参阅[GetFontHandle](#getfonthandle)有关的讨论`cyLogical`和`cyHimetric`参数。  
  
##  <a name="setfont"></a>CFontHolder::SetFont  
 释放任何现有的字体和连接`CFontHolder`对象传递给`IFont`接口。  
  
```  
void SetFont(LPFONT pNewFont);
```  
  
### <a name="parameters"></a>参数  
 *pNewFont*  
 指向新`IFont`接口。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPropExchange 类](../../mfc/reference/cpropexchange-class.md)
