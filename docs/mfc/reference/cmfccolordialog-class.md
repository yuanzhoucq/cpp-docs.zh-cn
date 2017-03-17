---
title: "CMFCColorDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorDialog::m_CurrentColor data member
- CMFCColorDialog::m_pPropSheet data member
- CMFCColorDialog::m_btnColorSelect data member
- CMFCColorDialog class
- CMFCColorDialog::m_wndColors data member
- CMFCColorDialog::m_bIsMyPalette data member
- CMFCColorDialog::m_pColourSheetTwo data member
- CMFCColorDialog::m_NewColor data member
- CMFCColorDialog::m_pPalette data member
- CMFCColorDialog::m_wndStaticPlaceHolder data member
- CMFCColorDialog::m_pColourSheetOne data member
- CMFCColorDialog::m_hcurPicker data member
- CMFCColorDialog::PreTranslateMessage method
- CMFCColorDialog::m_bPickerMode data member
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
caps.latest.revision: 30
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ac621157e0fcb5bcabef2ae8f367a1b141b4ace0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog 类
`CMFCColorDialog`类表示颜色选择对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|构造 `CMFCColorDialog` 对象。|  
|`CMFCColorDialog::~CMFCColorDialog`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCColorDialog::GetColor](#getcolor)|返回当前选定的颜色。|  
|[CMFCColorDialog::GetPalette](#getpalette)|返回的颜色调色板。|  
|`CMFCColorDialog::PreTranslateMessage`|翻译窗口消息之前被发送到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 有关语法和详细信息，请参阅[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CDialogEx::PreTranslateMessage`。）|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|派生自系统调色板的调色板。|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|设置当前所选的颜色。|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|设置颜色最等效于指定的 RGB 值。|  
|[CMFCColorDialog::SetPageOne](#setpageone)|选择第一个属性页的 RGB 值。|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|选择第二个属性页的 RGB 值。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|`m_bIsMyPalette`|`TRUE`如果颜色选择对话框中使用其自己的调色板，或`FALSE`对话框中如果使用的调色板中指定`CMFCColorDialog`构造函数。|  
|`m_bPickerMode`|`TRUE`虽然用户正在从所选内容对话框中，选择一种颜色否则为`FALSE`。|  
|`m_btnColorSelect`|用户已选择此颜色按钮。|  
|`m_CurrentColor`|当前所选的颜色。|  
|`m_hcurPicker`|用于选择一个颜色时光标。|  
|`m_NewColor`|预期所选的颜色，可以永久地选择或恢复到原始的颜色。|  
|`m_pColourSheetOne`|指向颜色选择属性表的第一个属性页的指针。|  
|`m_pColourSheetTwo`|指向颜色选择属性表的第二个属性页的指针。|  
|`m_pPalette`|当前逻辑调色板。|  
|`m_pPropSheet`|指向颜色选择对话框中的属性表的指针。|  
|`m_wndColors`|颜色选取器控件对象。|  
|`m_wndStaticPlaceHolder`|一个静态控件，它是一个占位符，供颜色选取器属性表。|  
  
## <a name="remarks"></a>备注  
 颜色选择对话框中显示为具有两个页的属性表中。 在第一页上，您的标准颜色从调色板中选择系统;在第二页上，您可以选择自定义颜色。  
  
 您可以构造`CMFCColorDialog`对象在堆栈上，然后调用`DoModal`，作为一个参数传递的初始颜色`CMFCColorDialog`构造函数。 然后，颜色选择对话框中创建几个[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)对象以处理每个颜色调色板。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法来配置颜色对话框`CMFCColorDialog`类。 该示例演示如何设置当前和新的颜色的对话框中，以及如何在颜色对话框中的两个属性页上设置所选颜色的红色、 绿色和蓝色组件。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&3;](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcolordialog.h  
  
##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog  
 构造 `CMFCColorDialog` 对象。  
  
```  
CMFCColorDialog(
    COLORREF clrInit=0,  
    DWORD dwFlags=0,  
    CWnd* pParentWnd=NULL,  
    HPALETTE hPal=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `clrInit`  
 默认颜色选择。 如果未不指定任何值，默认值为 RGB(0,0,0) （黑色）。  
  
 [in] `dwFlags`  
 （保留）。  
  
 [in] `pParentWnd`  
 指向对话框中的父窗口或所有者窗口的指针。  
  
 [in] `hPal`  
 指向一个调色板的句柄。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcolor"></a>CMFCColorDialog::GetColor  
 检索用户从颜色对话框中选择的颜色。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值包含在颜色对话框中选定的颜色的 RGB 信息。  
  
### <a name="remarks"></a>备注  
 在您调用后调用此函数`DoModal`方法。  
  
##  <a name="getpalette"></a>CMFCColorDialog::GetPalette  
 检索位于当前颜色对话框的调色板。  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CPalette`中所指定的对象`CMFCColorDialog`构造函数。  
  
### <a name="remarks"></a>备注  
 调色板指定用户可以选择的颜色。  
  
##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette  
 派生自系统调色板的调色板。  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor  
 设置对话框中的当前颜色。  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>参数  
 [in] `rgb`  
 RGB 颜色值  
  
### <a name="remarks"></a>备注  
  
##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor  
 将当前的颜色设置为当前非常类似的调色板中的颜色。  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>参数  
 [in] `rgb`  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) ，它指定 RGB 颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne  
 颜色对话框的第一个属性页上，显式指定所选颜色的红色、 绿色和蓝色组件。  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>参数  
 [in] `R`  
 指定 RGB 值的红色部分。  
  
 [in] `G`  
 指定 RGB 值的绿色部分。  
  
 [in] `B`  
 指定 RGB 值的蓝色部分。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo  
 颜色对话框的第二个属性页上，显式指定所选颜色的红色、 绿色和蓝色组件。  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>参数  
 [in] `R`  
 指定 RGB 值的红色组件  
  
 [in] `G`  
 指定 RGB 值的绿色组件  
  
 [in] `B`  
 指定 RGB 值的蓝色组件  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)

