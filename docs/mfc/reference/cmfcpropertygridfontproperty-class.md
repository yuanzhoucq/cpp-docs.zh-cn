---
title: "CMFCPropertyGridFontProperty 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFontProperty::OnClickButton method
- CMFCPropertyGridFontProperty class
- CMFCPropertyGridFontProperty::FormatProperty method
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 05d1db7e7de2ee72244e885d8a083ac3cda20142
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty 类
`CMFCPropertyGridFileProperty`类支持用于打开字体选择对话框中的属性列表控件项。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|构造 `CMFCPropertyGridFontProperty` 对象。|  
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|`CMFCPropertyGridFontProperty::FormatProperty`|设置属性值的文本表示形式的格式。 (重写[CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)。)|  
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|检索用户从字体对话框中选择的字体颜色。|  
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|检索用户从字体对话框中选择的字体。|  
|`CMFCPropertyGridFontProperty::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|`CMFCPropertyGridFontProperty::OnClickButton`|当用户单击属性中包含的按钮时，由框架调用。 (重写[CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|  
  
## <a name="remarks"></a>备注  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty  
 构造 `CMFCPropertyGridFontProperty` 对象。  
  
```  
CMFCPropertyGridFontProperty(
    const CString& strName,  
    LOGFONT& lf,  
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,  
    LPCTSTR lpszDescr = NULL,  
    DWORD_PTR dwData = 0,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `strName`  
 属性的名称。  
  
 [in] `lf`  
 逻辑字体结构，它指定字体的属性。  
  
 [in] `dwFontDialogFlags`  
 应用于字体对话框中，单击属性值下拉列表按钮时显示的样式。 默认值为 CF_EFFECTS 和 CF_SCREENFONTS 的按位组合 (OR)。 有关详细信息，请参阅`Flags`参数[CHOOSEFONT 结构](http://msdn.microsoft.com/library/windows/desktop/ms646832)。  
  
 [in] `lpszDescr`  
 字体属性的说明。 默认值为 `NULL`。  
  
 [in] `dwData`  
 应用程序特定的数据，如整数或其他与属性关联的数据的指针。 默认值为 0。  
  
 [in] `color`  
 字体的颜色。 默认值为默认颜色。  
  
### <a name="remarks"></a>备注  
 一个`CMFCPropertyGridFontProperty`对象都表示在属性网格字体控件的字体属性。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCPropertyGridFontProperty`类。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&26;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]  
  
##  <a name="getcolor"></a>CMFCPropertyGridFontProperty::GetColor  
 检索用户从字体对话框中选择的字体颜色。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个表示选定的字体的颜色的 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont  
 检索用户从字体对话框中选择的字体。  
  
```  
LPLOGFONT GetLogFont();
```  
  
### <a name="return-value"></a>返回值  
 一个指向[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构描述所选的字体。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)

