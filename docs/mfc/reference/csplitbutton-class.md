---
title: "CSplitButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
dev_langs:
- C++
helpviewer_keywords:
- CSplitButton class
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
caps.latest.revision: 24
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
ms.openlocfilehash: b4c038a177d5c501d4baad8eaa208af0e76ce231
ms.lasthandoff: 02/24/2017

---
# <a name="csplitbutton-class"></a>CSplitButton 类
`CSplitButton`类表示拆分按钮控件。 当用户单击按钮的主要部分时，拆分按钮控件将执行一个默认行为，而当用户单击按钮的下拉箭头时，控件将显示一个下拉菜单。  
  
## <a name="syntax"></a>语法  
  
```  
class CSplitButton : public CButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSplitButton::CSplitButton](#csplitbutton)|构造 `CSplitButton` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSplitButton::Create](#create)|创建具有指定样式的拆分按钮控件并将其附加到当前`CSplitButton`对象。|  
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|设置当用户单击当前拆分按钮控件的下拉箭头时显示的下拉列表菜单。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSplitButton::OnDropDown](#ondropdown)|处理`BCN_DROPDOWN`用户单击当前拆分按钮控件的下拉箭头时，系统将发送的通知。|  
  
## <a name="remarks"></a>备注  
 `CSplitButton`类派生自[CButton](../../mfc/reference/cbutton-class.md)类。 拆分按钮控件是一个按钮控件的样式是`BS_SPLITBUTTON`。 当用户单击下拉箭头，它会显示自定义菜单。 有关详细信息，请参阅`BS_SPLITBUTTON`和`BS_DEFSPLITBUTTON`中的样式[按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb775951)。  
  
 下图描绘了一个对话框，其中包含的页导航控件和 (1) 拆分按钮控件。 已单击 (2) 的下拉箭头，并显示 (3) 子菜单。  
  
 ![具有拆分按钮和页导航控件的对话框。] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
 此类支持在[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]及更高版本。  
  
 中介绍此类的其他要求[生成要求的 Windows Vista 公共控件](../../mfc/build-requirements-for-windows-vista-common-controls.md)。  
  
##  <a name="create"></a>CSplitButton::Create  
 创建具有指定样式的拆分按钮控件并将其附加到当前`CSplitButton`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `dwStyle`|按位组合 (OR) 要应用于控件的样式。 有关详细信息，请参阅[按钮样式](../../mfc/reference/button-styles.md)。|  
|[in] `rect`|对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，其中包含的位置和大小的控件。|  
|[in] `pParentWnd`|指向的非 null 指针[CWnd](../../mfc/reference/cwnd-class.md)是控件的父窗口的对象。|  
|[in] `nID`|控件的 ID。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
##  <a name="csplitbutton"></a>CSplitButton::CSplitButton  
 构造 `CSplitButton` 对象。 构造函数的参数指定当用户单击拆分按钮控件的下拉箭头时显示的子菜单。  
  
```  
CSplitButton();

 
CSplitButton(
    UINT nMenuId,   
    UINT nSubMenuId)  
CSplitButton(CMenu* pMenu)  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `nMenuId`|菜单栏的资源 ID。|  
|[in] `nSubMenuId`|子菜单资源 ID。|  
|[in] `pMenu`|一个指向[CMenu](../../mfc/reference/cmenu-class.md)对象，它指定一个子菜单。 `CSplitButton`对象删除`CMenu`对象和及其关联`HMENU`时`CSplitButton`对象超出范围。|  
  
### <a name="remarks"></a>备注  
 使用[CSplitButton::Create](#create)方法可创建拆分按钮控件并将其附加到`CSplitButton`对象。  
  
##  <a name="ondropdown"></a>CSplitButton::OnDropDown  
 处理`BCN_DROPDOWN`用户单击当前拆分按钮控件的下拉箭头时，系统将发送的通知。  
  
```  
afx_msg void OnDropDown(
    NMHDR* pNMHDR,   
    LRESULT* pResult);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pNMHDR`|指向[NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514)结构，它包含以下信息[BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983)通知。|  
|[out] `pResult`|（不使用; 不返回任何值。）返回值的[BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983)通知。|  
  
### <a name="remarks"></a>备注  
 当用户单击拆分按钮控件上的下拉箭头时，系统会将发送`BCN_DROPDOWN`通知消息时，其`OnDropDown`方法句柄。 但是，`CSplitButton`对象不转发`BCN_DROPDOWN`包含拆分按钮控件的控件的通知。 因此，包含控件不能以响应通知支持的自定义操作。  
  
 若要实现包含控件支持的自定义操作，使用[CButton](../../mfc/reference/cbutton-class.md)对象使用样式的`BS_SPLITBUTTON`而不是`CSplitButton`对象。 然后实现一个处理程序`BCN_DROPDOWN`中的通知`CButton`对象。 有关详细信息，请参阅[按钮样式](../../mfc/reference/button-styles.md)。  
  
 若要实现自定义操作，拆分按钮控件本身支持，使用[消息反射](../../mfc/tn062-message-reflection-for-windows-controls.md)。 派生您自己的类从`CSplitButton`类，并将其命名，例如，CMySplitButton。 然后将下面的消息映射添加到您的应用程序来处理`BCN_DROPDOWN`通知︰  
  
```  
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)  
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)  
END_MESSAGE_MAP()  
```  
  
##  <a name="setdropdownmenu"></a>CSplitButton::SetDropDownMenu  
 设置当用户单击当前拆分按钮控件的下拉箭头时显示的下拉列表菜单。  
  
```  
void SetDropDownMenu(
    UINT nMenuId,   
    UINT nSubMenuId);  
  
void SetDropDownMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `nMenuId`|菜单栏的资源 ID。|  
|[in] `nSubMenuId`|子菜单资源 ID。|  
|[in] `pMenu`|指向[CMenu](../../mfc/reference/cmenu-class.md)对象，它指定一个子菜单。 `CSplitButton`对象删除`CMenu`对象和及其关联`HMENU`时`CSplitButton`对象超出范围。|  
  
### <a name="remarks"></a>备注  
 `nMenuId`参数标识一个菜单栏，它是一个水平菜单栏项的列表。 `nSubMenuId`参数是一个从零开始的索引号标识子菜单中，这是与每个菜单栏项关联的菜单项的下拉列表。 例如，典型的应用程序具有一个包含菜单的菜单栏项"文件，""编辑"和"帮助"。 "文件"菜单栏项具有子菜单，其中包含菜单项中，"打开"状态，"关闭"和"Exit"。 单击拆分按钮控件的下拉箭头时，该控件将显示指定的子菜单中，不在菜单栏。  
  
 下图描绘了一个对话框，其中包含的页导航控件和 (1) 拆分按钮控件。 已单击 (2) 的下拉箭头，并显示 (3) 子菜单。  
  
 ![具有拆分按钮和页导航控件的对话框。] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
### <a name="example"></a>示例  
 下面的代码示例中的第一个语句演示[CSplitButton::SetDropDownMenu](#setdropdownmenu)方法。 我们创建菜单与 Visual Studio 资源编辑器，自动命名的菜单栏 ID， `IDR_MENU1`。 `nSubMenuId`参数，为零，指的菜单栏的唯一子菜单。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;&1;](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CSplitButton 类](../../mfc/reference/csplitbutton-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CButton 类](../../mfc/reference/cbutton-class.md)

