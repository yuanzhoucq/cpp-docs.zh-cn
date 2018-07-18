---
title: CDockablePaneAdapter 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
dev_langs:
- C++
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e43f6704476879e1848ce82b3327b23efe2192a8
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026301"
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter 类
为 `CWnd`派生窗格提供停靠支持。  
  
## <a name="syntax"></a>语法  
  
```  
class CDockablePaneAdapter : public CDockablePane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|返回包装的窗口。|  
|[CDockablePaneAdapter::LoadState](#loadstate)|(重写[cdockablepane:: Loadstate](http://msdn.microsoft.com/96110136-4f46-4764-8a76-3b4abaf77917)。)|  
|[CDockablePaneAdapter::SaveState](#savestate)|(重写[cdockablepane:: Savestate](http://msdn.microsoft.com/c5c24249-8d0d-46cb-96d9-9f5c6dc191db)。)|  
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||  
  
## <a name="remarks"></a>备注  
 通常情况下，该框架实例化此类的对象时使用[cmfcbasetabctrl:: Addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)或[cmfcbasetabctrl:: Inserttab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab)方法。  
  
 如果你想要自定义`CDockablePaneAdapter`行为，只需从其派生新类并使用运行时类信息设置为选项卡式窗口[:: Setdockingbarwrapperrtc](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxDockablePaneAdapter.h  
  
##  <a name="getwrappedwnd"></a>  CDockablePaneAdapter::GetWrappedWnd  
 返回可停靠窗格适配器的底层窗口。  
  
```  
virtual CWnd* GetWrappedWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向已包装的窗口的指针。  
  
### <a name="remarks"></a>备注  
 使用此函数来访问包装的窗口。  
  
##  <a name="loadstate"></a>  CDockablePaneAdapter::LoadState  
 从注册表加载窗格的状态。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszProfileName*  
 配置文件名称。  
  
 [in]*nIndex*  
 配置文件的索引。  
  
 [in]*uiID*  
 窗格 id。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="savestate"></a>  CDockablePaneAdapter::SaveState  
 将窗格的状态保存到注册表。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszProfileName*  
 配置文件名称。  
  
 [in]*nIndex*  
 配置文件的索引 （默认为窗口的控件 ID）。  
  
 [in]*uiID*  
 窗格 id。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="setwrappedwnd"></a>  CDockablePaneAdapter::SetWrappedWnd  
 设置可停靠窗格适配器的底层窗口。  
  
```  
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in]*pWnd*  
 指向要包装的窗格中适配器的窗口的指针。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)
