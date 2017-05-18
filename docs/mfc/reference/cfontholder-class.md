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
- custom fonts
- CFontHolder class
- fonts, ActiveX controls
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
caps.latest.revision: 19
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
ms.openlocfilehash: fdfa16756ff218159087969f2a4967ed5e76a445
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
|[CFontHolder::GetFontHandle](#getfonthandle)|Windows 字体中返回的句柄。|  
|[CFontHolder::InitializeFont](#initializefont)|初始化`CFontHolder`对象。|  
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|检索相关字体信息。|  
|[CFontHolder::ReleaseFont](#releasefont)|断开连接`CFontHolder`对象从`IFont`和`IFontNotification`接口。|  
|[CFontHolder::Select](#select)|选择到设备上下文的字体资源。|  
|[CFontHolder::SetFont](#setfont)|连接`CFontHolder`对象传递给`IFont`接口。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CFontHolder::m_pFont](#m_pfont)|一个指向`CFontHolder`对象的`IFont`接口。|  
  
## <a name="remarks"></a>备注  
 `CFontHolder`没有基类的类。  
  
 使用此类来实现您的控件的自定义字体属性。 有关创建此类属性的信息，请参阅文章[ActiveX 控件︰ 使用字体](../../mfc/mfc-activex-controls-using-fonts.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CFontHolder`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxctl.h  
  
##  <a name="cfontholder"></a>CFontHolder::CFontHolder  
 构造 `CFontHolder` 对象。  
  
```  
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```  
  
### <a name="parameters"></a>参数  
 *pNotify*  
 指向字体的`IPropertyNotifySink`接口。  
  
### <a name="remarks"></a>备注  
 必须调用`InitializeFont`来初始化所产生的对象，然后再使用它。  
  
##  <a name="getdisplaystring"></a>CFontHolder::GetDisplayString  
 检索可以在容器的属性浏览器中显示的字符串。  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>参数  
 `strValue`  
 引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)这是用于保存显示字符串。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功检索到字符串;否则为 0。  
  
##  <a name="getfontdispatch"></a>CFontHolder::GetFontDispatch  
 调用此函数可检索到的字体的调度接口指针。  
  
```  
LPFONTDISP GetFontDispatch();
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CFontHolder`对象的**IFontDisp**接口。 请注意，该函数的调用`GetFontDispatch`必须调用`IUnknown::Release`上时使用它实现此接口指针。  
  
### <a name="remarks"></a>备注  
 调用`InitializeFont`之前调用`GetFontDispatch`。  
  
##  <a name="getfonthandle"></a>CFontHolder::GetFontHandle  
 调用此函数可获取为 Windows 字体的句柄。  
  
```  
HFONT GetFontHandle();

 
HFONT GetFontHandle(
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>参数  
 `cyLogical`  
 使用逻辑单位，在其中绘制控件的矩形的高度。  
  
 `cyHimetric`  
 高度，请在`MM_HIMETRIC`单位，该控件。  
  
### <a name="return-value"></a>返回值  
 字体对象中; 的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 比率`cyLogical`和`cyHimetric`用来计算正常显示大小，使用逻辑单位，以表示字体的磅值`MM_HIMETRIC`单元︰  
  
 显示大小 = ( `cyLogical`  /  `cyHimetric`) X 字体大小  
  
 不带参数的版本返回正确设置大小，以使屏幕字体的句柄。  
  
##  <a name="initializefont"></a>CFontHolder::InitializeFont  
 初始化`CFontHolder`对象。  
  
```  
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,  
    LPDISPATCH pFontDispAmbient = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pFontDesc`  
 字体描述结构的指针 ( [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782))，它指定字体的特征。  
  
 `pFontDispAmbient`  
 指针，指向容器的环境字体属性。  
  
### <a name="remarks"></a>备注  
 如果`pFontDispAmbient`不是**NULL**、`CFontHolder`对象连接到的克隆`IFont`使用容器的环境字体属性的接口。  
  
 如果`pFontDispAmbient`是**NULL**，从所指向的字体说明，创建了一个新的字体对象`pFontDesc`或者，如果`pFontDesc`是**NULL**，从默认的说明。  
  
 在构造之后调用此函数`CFontHolder`对象。  
  
##  <a name="m_pfont"></a>CFontHolder::m_pFont  
 一个指向`CFontHolder`对象的`IFont`接口。  
  
```  
LPFONT m_pFont;  
```  
  
##  <a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics  
 检索有关所表示的物理字体`CFontHolder`对象。  
  
```  
void QueryTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>参数  
 `lptm`  
 一个指向[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)结构，它将会收到信息。  
  
##  <a name="releasefont"></a>CFontHolder::ReleaseFont  
 此函数断开`CFontHolder`对象从其`IFont`接口。  
  
```  
void ReleaseFont();
```  
  
##  <a name="select"></a>CFontHolder::Select  
 调用此函数可指定的设备上下文中选择控件的字体。  
  
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
 使用逻辑单位，在其中绘制控件的矩形的高度。  
  
 `cyHimetric`  
 高度，请在`MM_HIMETRIC`单位，该控件。  
  
### <a name="return-value"></a>返回值  
 指向要替换的字体的指针。  
  
### <a name="remarks"></a>备注  
 请参阅[GetFontHandle](#getfonthandle)有关的讨论`cyLogical`和`cyHimetric`参数。  
  
##  <a name="setfont"></a>CFontHolder::SetFont  
 释放任何现有的字体并连接`CFontHolder`对象传递给`IFont`接口。  
  
```  
void SetFont(LPFONT pNewFont);
```  
  
### <a name="parameters"></a>参数  
 *pNewFont*  
 指向新`IFont`接口。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPropExchange 类](../../mfc/reference/cpropexchange-class.md)

