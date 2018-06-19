---
title: CMFCPropertyGridFontProperty 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e7acda3bf3734a325c7d603489c1305cb63bc3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367609"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty 类
`CMFCPropertyGridFileProperty`类支持用于打开字体选择对话框中的属性列表控件项。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|构造 `CMFCPropertyGridFontProperty` 对象。|  
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCPropertyGridFontProperty::FormatProperty`|设置属性值的文本表示形式的格式。 (重写[cmfcpropertygridproperty:: Formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)。)|  
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|检索用户从字体对话框中选择的字体颜色。|  
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|检索用户从字体对话框中选择的字体。|  
|`CMFCPropertyGridFontProperty::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|`CMFCPropertyGridFontProperty::OnClickButton`|当用户单击属性中包含的按钮时，由框架调用。 (重写[cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|  
  
## <a name="remarks"></a>备注  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty  
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
 逻辑字体结构，它指定的字体特性。  
  
 [in] `dwFontDialogFlags`  
 应用于字体对话框中单击属性值下拉列表按钮时显示的样式。 默认值为 CF_EFFECTS 和 CF_SCREENFONTS 的按位组合 (OR)。 有关详细信息，请参阅`Flags`参数[CHOOSEFONT 结构](http://msdn.microsoft.com/library/windows/desktop/ms646832)。  
  
 [in] `lpszDescr`  
 字体属性的说明。 默认值为 `NULL`。  
  
 [in] `dwData`  
 应用程序特定数据，如整数或与属性关联的其他数据的指针。 默认值为 0。  
  
 [in] `color`  
 字体的颜色。 默认值为默认颜色。  
  
### <a name="remarks"></a>备注  
 A`CMFCPropertyGridFontProperty`对象表示在属性网格字体控件中的字体属性。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCPropertyGridFontProperty`类。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]  
  
##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor  
 检索用户从字体对话框中选择的字体颜色。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个表示选定的字体的颜色的 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont  
 检索用户从字体对话框中选择的字体。  
  
```  
LPLOGFONT GetLogFont();
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)描述选定的字体的结构。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)
