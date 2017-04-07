---
title: "CMFCMenuButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
dev_langs:
- C++
helpviewer_keywords:
- CMFCMenuButton class
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
caps.latest.revision: 32
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 65c334ce68dbbbae2b21da2c40aa9420cdeb51bd
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton 类
在用户菜单选项上显示弹出菜单和报表的按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCMenuButton : public CMFCButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|构造 `CMFCMenuButton` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|由框架将窗口消息转换之前对它们进行调用。 （重写 `CMFCButton::PreTranslateMessage`。）|  
|[CMFCMenuButton::SizeToContent](#sizetocontent)|根据其文本和图像的大小的按钮的大小更改。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|指定是否显示默认的系统弹出菜单或使用[CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。|  
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|指定是否下方或右侧的按钮将显示弹出菜单。|  
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|指定是否菜单按钮将其状态更改之后，同时用户释放该按钮。|  
|[CMFCMenuButton::m_hMenu](#m_hmenu)|附加的 Windows 菜单句柄。|  
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|指示哪一项的标识符用户从弹出菜单中选择。|  
  
## <a name="remarks"></a>备注  
 `CMFCMenuButton`类派生自[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)，后者又派生自[CButton 类](../../mfc/reference/cbutton-class.md)。 因此，您可以使用`CMFCMenuButton`在您的代码将使用的相同方式`CButton`。  
  
 当您创建`CMFCMenuButton`，必须传递句柄关联的弹出菜单。 接下来，调用该函数`CMFCMenuButton::SizeToContent`。 `CMFCMenuButton::SizeToContent`检查该按钮的大小足以包含一个指向的位置弹出窗口中显示的位置-即下方或按钮右侧的箭头。  
  
## <a name="example"></a>示例  
 下面的示例演示如何设置附加到按钮的菜单的句柄、 调整其文本和图像的大小，请根据按钮的大小以及设置框架所显示的弹出菜单。 此代码段属于[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&38;](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&39;](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxmenubutton.h  
  
##  <a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton  
 构造一个新[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)对象。  
  
```  
CMFCMenuButton();
```  
  
##  <a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu  
 指示哪个弹出菜单的 Boolean 成员变量，框架显示。  
  
```  
BOOL m_bOSMenu;  
```  
  
### <a name="remarks"></a>备注  
 如果`m_bOSMenu`是`TRUE`，框架将调用的继承`TrackPopupMenu`此对象的方法。 否则，框架将调用[CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。  
  
##  <a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow  
 布尔值的成员变量，指示弹出菜单的位置。  
  
```  
BOOL m_bRightArrow;  
```  
  
### <a name="remarks"></a>备注  
 当用户按菜单按钮时，该应用程序将显示一个弹出菜单。 框架将显示在按钮下或按钮右侧的弹出菜单。 该按钮还包括一个小箭头，该值指示弹出菜单将显示的位置。 如果`m_bRightArrow`是`TRUE`，框架显示按钮右侧的弹出菜单。 否则，将显示按钮下的弹出菜单中。  
  
##  <a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed  
 用户进行从弹出菜单选择情况下按下的 Boolean 成员变量，该值指示是否显示菜单按钮。  
  
```  
BOOL m_bStayPressed;  
```  
  
### <a name="remarks"></a>备注  
 如果`m_bStayPressed`成员是`FALSE`，菜单按钮不会未变得按下状态时单击按钮时使用。 在这种情况下，框架显示仅弹出菜单。  
  
 如果`m_bStayPressed`成员是`TRUE`，用户单击按钮时，将成为按下菜单按钮。 用户关闭弹出菜单中，通过进行选择或取消后，它始终处于直到按下。  
  
##  <a name="m_hmenu"></a>CMFCMenuButton::m_hMenu  
 附加菜单句柄。  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="remarks"></a>备注  
 框架显示由此成员变量，当用户单击菜单按钮菜单。  
  
##  <a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult  
 一个整数，指示哪一项用户从弹出菜单中选择。  
  
```  
int m_nMenuResult;  
```  
  
### <a name="remarks"></a>备注  
 如果用户取消不做任何选择的菜单或出错时，此成员变量的值为零。  
  
##  <a name="pretranslatemessage"></a>CMFCMenuButton::PreTranslateMessage  
 由框架将窗口消息转换之前对它们进行调用。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMsg`  
 指向[MSG](../../mfc/reference/msg-structure1.md)结构，其中包含要处理的消息。  
  
### <a name="return-value"></a>返回值  
 非零，如果消息已转换，并且不应将调度;如果消息没有翻译，并且应调度为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="sizetocontent"></a>CMFCMenuButton::SizeToContent  
 根据其文本大小和图像大小的按钮的大小更改。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bCalcOnly`  
 一个布尔型参数，该值指示是否此方法调整大小按钮。  
  
### <a name="return-value"></a>返回值  
 一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，它指定按钮的新大小。  
  
### <a name="remarks"></a>备注  
 如果调用此函数和`bCalcOnly`是`TRUE`，`SizeToContent`将计算仅将新按钮的大小。  
  
 计算按钮的新大小以适应按钮文本、 图像和箭头。 该框架还将添加在 10 个像素的水平边缘和垂直边的 5 个像素的预定义的边距。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)

