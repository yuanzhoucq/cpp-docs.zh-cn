---
title: "CSnapInPropertyPageImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSnapInPropertyPageImpl
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
caps.latest.revision: 20
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f5db4d0742a423e9574db2a4268a9376491b2ed2
ms.lasthandoff: 02/24/2017

---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl 类
此类提供用于实现一个管理单元中属性的 page 对象的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
CSnapInPropertyPageImpl : public CDialogImplBase
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|更改状态的**确定**和**取消**按钮。|  
|[CSnapInPropertyPageImpl::Create](#create)|初始化新创建`CSnapInPropertyPageImpl`对象。|  
|[CSnapInPropertyPageImpl::OnApply](#onapply)|当用户单击由框架调用**立即应用**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|当用户单击由框架调用**帮助**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|在当前页不再处于活动状态时，由框架调用。|  
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|当用户单击由框架调用**取消**按钮和取消已经发生之前。|  
|[CSnapInPropertyPageImpl::OnReset](#onreset)|当用户单击由框架调用**重置**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|当前页面变为活动状态时，由框架调用。|  
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|当用户单击由框架调用**回**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|当用户单击由框架调用**完成**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|当用户单击由框架调用`Next`使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|当前将消息转发到属性表的所有页面。|  
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|调用以激活或停用**立即应用**按钮。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows **PROPSHEETPAGE**使用结构`CSnapInPropertyPageImpl`对象。|  
  
## <a name="remarks"></a>备注  
 `CSnapInPropertyPageImpl`提供了一个管理单元中属性的 page 对象的基本实现。 管理单元在属性页的基本功能使用多个不同的接口来实现，并将类型映射。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsnap.h  
  
##  <a name="a-namecanceltoclosea--csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose  
 调用此函数后对模式属性表的页中的数据进行了不可恢复的更改。  
  
```
void CancelToClose();
```  
  
### <a name="remarks"></a>备注  
 此函数将更改**确定**按钮以**关闭**和禁用**取消**按钮。 此更改不能取消更改是永久的所做的修改用户的警报。  
  
 `CancelToClose`成员函数不会在无模式属性表中，执行任何操作，因为无模式属性表没有**取消**默认情况下的按钮。  
  
##  <a name="a-namecsnapinpropertypageimpla--csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl  
 构造 `CSnapInPropertyPageImpl` 对象。  
  
```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszTitle`  
 [in]属性页上的标题。  
  
### <a name="remarks"></a>备注  
 若要初始化的基础结构，请调用[CSnapInPropertyPageImpl::Create](#create)。  
  
##  <a name="a-namecreatea--csnapinpropertypageimplcreate"></a><a name="create"></a>CSnapInPropertyPageImpl::Create  
 调用此函数可初始化属性页上的基础结构。  
  
```
HPROPSHEETPAGE Create();
```  
  
### <a name="return-value"></a>返回值  
 句柄**PROPSHEETPAGE**结构，其中包含新创建的属性表的属性。  
  
### <a name="remarks"></a>备注  
 您应首先调用[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)之前调用此函数。  
  
##  <a name="a-namempspa--csnapinpropertypageimplmpsp"></a><a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp  
 `m_psp`是一种结构的成员将存储的特征**PROPSHEETPAGE**。  
  
```
PROPSHEETPAGE m_psp;
```  
  
### <a name="remarks"></a>备注  
 使用此结构在构造之后初始化属性页的外观。  
  
 此结构，包括其成员的列表的详细信息请参阅[PROPSHEETPAGE](http://msdn.microsoft.com/library/aa815151)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonapplya--csnapinpropertypageimplonapply"></a><a name="onapply"></a>CSnapInPropertyPageImpl::OnApply  
 当用户单击调用此成员函数**确定**或**立即应用**按钮。  
  
```
BOOL OnApply();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果接受所做的更改;否则为 0。  
  
### <a name="remarks"></a>备注  
 之前`OnApply`可以调用由框架，您必须调用`SetModified`并将其参数设置为**TRUE**。 这将激活**立即应用**按钮只要用户的属性页上进行了更改。  
  
 重写该成员函数以指定在用户单击时，考虑您的程序的操作**立即应用**按钮。 重写时，该函数应返回**TRUE**以接受更改和**FALSE**防止更改生效。  
  
 默认实现`OnApply`返回**TRUE**。  
  
##  <a name="a-nameonhelpa--csnapinpropertypageimplonhelp"></a><a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp  
 当用户单击调用此成员函数**帮助**属性页上的按钮。  
  
```
void OnHelp();
```  
  
### <a name="remarks"></a>备注  
 重写该成员函数以显示属性页上的帮助。  
  
##  <a name="a-nameonkillactivea--csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive  
 在页上不再是活动的页面时，调用此成员函数。  
  
```
BOOL OnKillActive();
```  
  
### <a name="return-value"></a>返回值  
 如果数据更新成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以执行特殊的数据验证任务。  
  
##  <a name="a-nameonquerycancela--csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel  
 当用户单击调用此成员函数**取消**按钮，然后在取消之前采取任何措施的位置。  
  
```
BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>返回值  
 非零值，允许取消操作;否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定该程序将在用户单击时的操作**取消**按钮。  
  
 默认实现`OnQueryCancel`返回**TRUE**。  
  
##  <a name="a-nameonreseta--csnapinpropertypageimplonreset"></a><a name="onreset"></a>CSnapInPropertyPageImpl::OnReset  
 当用户单击调用此成员函数**取消**按钮。  
  
```
void OnReset();
```  
  
### <a name="remarks"></a>备注  
 在调用此函数时，将更改为以前单击的用户所做的所有属性页**立即应用**按钮将被放弃，且属性表将保留焦点。  
  
 重写该成员函数以指定该程序将在用户单击时的动作**取消**按钮。  
  
##  <a name="a-nameonsetactivea--csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive  
 由用户选择和成为活动页面页时，调用此成员函数。  
  
```
BOOL OnSetActive();
```  
  
### <a name="return-value"></a>返回值  
 如果页已成功设置活动状态，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以激活页面时执行的任务。 完成任何其他处理之前，此成员函数的重写应调用的默认版本。  
  
 默认实现返回**TRUE**。  
  
##  <a name="a-nameonwizardbacka--csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack  
 当用户单击调用此成员函数**回**在向导中的按钮。  
  
```
BOOL OnWizardBack();
```  
  
### <a name="return-value"></a>返回值  
  
-   若要自动前进到前一页为&0;。  
  
-   为-1，使页面无法更改。  
  
 若要跳转到下一个以外的页面，请返回对话框中，要显示的标识符。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定用户必须采取当某些操作**回**单击按钮。  
  
##  <a name="a-nameonwizardfinisha--csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish  
 当用户单击调用此成员函数**完成**在向导中的按钮。  
  
```
BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果属性表被销毁时在向导完成;否则为零。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定用户必须采取当某些操作**完成**单击按钮。  
  
##  <a name="a-nameonwizardnexta--csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext  
 当用户单击调用此成员函数`Next`在向导中的按钮。  
  
```
BOOL OnWizardNext();
```  
  
### <a name="return-value"></a>返回值  
  
-   若要自动前进到下一个页面为&0;。  
  
-   为-1，使页面无法更改。  
  
 若要跳转到下一个以外的页面，请返回对话框中，要显示的标识符。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定用户必须采取当某些操作`Next`单击按钮。  
  
##  <a name="a-namequerysiblingsa--csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings  
 调用该成员函数以将消息转发到属性表中的每一页。  
  
```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `wParam`  
 [in]指定消息相关的其他信息。  
  
 `lParam`  
 [in]指定消息相关的其他信息。  
  
### <a name="return-value"></a>返回值  
 非零，如果不应将消息转发到下一步的属性页;否则为零。  
  
### <a name="remarks"></a>备注  
 如果页面返回非零值，则属性表不向后续页面发送消息。  
  
##  <a name="a-namesetmodifieda--csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified  
 调用此成员函数可启用或禁用**立即应用**按钮时，根据是否在属性页中的设置应该应用于相应的外部对象。  
  
```
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bChanged`  
 [in]**TRUE**以指示是否尚未应用了这些; 的上次修改的属性页设置**FALSE**以指示属性页设置尚未应用，还是应忽略。  
  
### <a name="remarks"></a>备注  
 属性表中保留的跟踪所属页的"脏"，它是、 已调用的属性页**SetModified (TRUE)**。 **立即应用**将始终启用按钮，如果调用**SetModified (TRUE)**的页面之一。 **立即应用**按钮将被禁用，当您调用**SetModified (FALSE)**之一的页面，但是仅当无其他两个页面"脏"。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

