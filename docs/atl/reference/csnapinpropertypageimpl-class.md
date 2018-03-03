---
title: "CSnapInPropertyPageImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fc1135f02c31c644d7d149900bbaa755a52c579
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl 类
此类提供用于实现管理单元在属性页上对象的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|状态更改**确定**和**取消**按钮。|  
|[CSnapInPropertyPageImpl::Create](#create)|初始化新创建`CSnapInPropertyPageImpl`对象。|  
|[CSnapInPropertyPageImpl::OnApply](#onapply)|由框架调用，当用户单击**立即应用**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|由框架调用，当用户单击**帮助**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|当前页不再处于活动状态时，由框架调用。|  
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|由框架调用，当用户单击**取消**按钮和取消发生之前。|  
|[CSnapInPropertyPageImpl::OnReset](#onreset)|由框架调用，当用户单击**重置**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|当前页变为活动状态时，由框架调用。|  
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|由框架调用，当用户单击**回**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|由框架调用，当用户单击**完成**使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|由框架调用，当用户单击`Next`使用向导类型的属性表时的按钮。|  
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|将转发到的属性表的所有页面的当前消息。|  
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|调用以激活或停用**立即应用**按钮。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows **PROPSHEETPAGE**使用结构`CSnapInPropertyPageImpl`对象。|  
  
## <a name="remarks"></a>备注  
 `CSnapInPropertyPageImpl`提供了管理单元在属性页上对象的基本实现。 管理单元在属性页的基本功能使用多个不同的接口来实现，并将映射类型。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlsnap.h  
  
##  <a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose  
 对模式属性表的页面中的数据进行了不可恢复的更改后调用此函数。  
  
```
void CancelToClose();
```  
  
### <a name="remarks"></a>备注  
 此函数将更改**确定**按钮**关闭**和禁用**取消**按钮。 此更改不能取消更改是永久的修改用户的警报。  
  
 `CancelToClose`成员函数不会在无模式属性表中，执行任何操作，因为无模式属性表没有**取消**默认情况下的按钮。  
  
##  <a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl  
 构造 `CSnapInPropertyPageImpl` 对象。  
  
```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszTitle`  
 [in]在属性页标题。  
  
### <a name="remarks"></a>备注  
 若要初始化的基础结构，调用[CSnapInPropertyPageImpl::Create](#create)。  
  
##  <a name="create"></a>CSnapInPropertyPageImpl::Create  
 调用此函数可初始化的属性页的基础结构。  
  
```
HPROPSHEETPAGE Create();
```  
  
### <a name="return-value"></a>返回值  
 句柄**PROPSHEETPAGE**结构，它包含新创建的属性表的属性。  
  
### <a name="remarks"></a>备注  
 首先应调用[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)之前调用此函数。  
  
##  <a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp  
 `m_psp`是其成员存储的特征的结构**PROPSHEETPAGE**。  
  
```
PROPSHEETPAGE m_psp;
```  
  
### <a name="remarks"></a>备注  
 使用此结构在构造之后初始化属性页的外观。  
  
 此结构，包括其成员的列表的详细信息请参阅[PROPSHEETPAGE](http://msdn.microsoft.com/library/aa815151) Windows SDK 中。  
  
##  <a name="onapply"></a>CSnapInPropertyPageImpl::OnApply  
 用户单击时，此成员函数将调用**确定**或**立即应用**按钮。  
  
```
BOOL OnApply();
```  
  
### <a name="return-value"></a>返回值  
 如果接受所做的更改; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 之前`OnApply`可以调用由框架，你必须已调用`SetModified`并将其参数设置为**TRUE**。 这将激活**立即应用**按钮只要用户的属性页上进行了更改。  
  
 重写该成员函数以指定你的程序将在用户单击时什么操作**立即应用**按钮。 重写时，该函数应返回**TRUE**接受更改和**FALSE**以防止更改生效。  
  
 默认实现`OnApply`返回**TRUE**。  
  
##  <a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp  
 用户单击时，此成员函数将调用**帮助**为属性页的按钮。  
  
```
void OnHelp();
```  
  
### <a name="remarks"></a>备注  
 重写该成员函数以显示属性页的帮助。  
  
##  <a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive  
 页不再是活动的页面时调用此成员函数。  
  
```
BOOL OnKillActive();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则更新数据的时间则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以执行特殊的数据验证任务。  
  
##  <a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel  
 用户单击时，此成员函数将调用**取消**按钮，然后在取消之前操作发生。  
  
```
BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>返回值  
 非零值，允许取消操作;否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定程序采用当用户单击的操作**取消**按钮。  
  
 默认实现`OnQueryCancel`返回**TRUE**。  
  
##  <a name="onreset"></a>CSnapInPropertyPageImpl::OnReset  
 用户单击时，此成员函数将调用**取消**按钮。  
  
```
void OnReset();
```  
  
### <a name="remarks"></a>备注  
 当调用此函数时，更改为以前单击用户所做的所有属性页**立即应用**按钮将被丢弃，和属性表保留焦点。  
  
 重写该成员函数以指定程序采用当用户单击什么操作**取消**按钮。  
  
##  <a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive  
 由用户选择和成为活动页面页时调用此成员函数。  
  
```
BOOL OnSetActive();
```  
  
### <a name="return-value"></a>返回值  
 如果页已成功设置活动状态，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以激活页时执行任务。 完成其他任何处理之前，此成员函数的重写应调用的默认版本。  
  
 默认实现返回**TRUE**。  
  
##  <a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack  
 用户单击时，此成员函数将调用**回**向导中的按钮。  
  
```
BOOL OnWizardBack();
```  
  
### <a name="return-value"></a>返回值  
  
-   若要自动前进到前一页为 0。  
  
-   -1 以使页面无法更改。  
  
 若要跳转到下一步以外的页，请返回对话框中要显示的标识符。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定用户必须采取时某些操作**回**单击按钮。  
  
##  <a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish  
 用户单击时，此成员函数将调用**完成**向导中的按钮。  
  
```
BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>返回值  
 如果在向导完成后; 销毁属性表则不为否则为零。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定用户必须采取时某些操作**完成**单击按钮。  
  
##  <a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext  
 用户单击时，此成员函数将调用`Next`向导中的按钮。  
  
```
BOOL OnWizardNext();
```  
  
### <a name="return-value"></a>返回值  
  
-   0，以自动前进到下一个页面。  
  
-   -1 以使页面无法更改。  
  
 若要跳转到下一步以外的页，请返回对话框中要显示的标识符。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定用户必须采取时某些操作`Next`单击按钮。  
  
##  <a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings  
 调用此成员函数以将消息转发到属性表中每一页。  
  
```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `wParam`  
 [in]指定消息相关的其他信息。  
  
 `lParam`  
 [in]指定消息相关的其他信息。  
  
### <a name="return-value"></a>返回值  
 如果不应将消息转发到下一步的属性页; 则为非 0否则为零。  
  
### <a name="remarks"></a>备注  
 如果页面返回非零值，属性表不后续页中发送消息。  
  
##  <a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified  
 调用此成员函数可启用或禁用**立即应用**按钮，基于是否属性页中的设置应该应用于相应的外部对象。  
  
```
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bChanged`  
 [in]**TRUE**以指示是否尚未中应用; 的上次修改的属性页设置**FALSE**以指示已应用，或应忽略的属性页设置。  
  
### <a name="remarks"></a>备注  
 属性表保留的跟踪的页面的"脏"，它是、 属性页，为其调用了**SetModified (TRUE)**。 **立即应用**将始终启用按钮，如果调用**SetModified (TRUE)**页面之一。 **立即应用**在调用时，将禁用按钮**SetModified (FALSE)**之一的页面，但只有无其他页面"脏"。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
