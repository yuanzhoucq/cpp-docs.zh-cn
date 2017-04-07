---
title: "CMFCShellTreeCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
dev_langs:
- C++
helpviewer_keywords:
- CMFCShellTreeCtrl class
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
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
ms.openlocfilehash: cf9c7c3577646895546c443c975a92431194d3f4
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 类
`CMFCShellTreeCtrl`类扩展[CTreeCtrl 类](../../mfc/reference/ctreectrl-class.md)通过显示 Shell 项的层次结构的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCShellTreeCtrl : public CTreeCtrl  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|启用或禁用的快捷菜单。|  
|[CMFCShellTreeCtrl::GetFlags](#getflags)|返回传递到的标志的组合[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)。|  
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|检索项的路径。|  
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|返回一个指向[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)与这一起使用的对象`CMFCShellTreeCtrl`对象来创建一个类似于资源管理器中的窗口。|  
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|在收到一条通知消息，将应用于此窗口时，将通过此窗口的父窗口调用此成员函数。 (重写[CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify)。)|  
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||  
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||  
|[CMFCShellTreeCtrl::Refresh](#refresh)|刷新并重新绘制当前`CMFCShellTreeCtrl`对象。|  
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|选择相应的树控件项基于提供的 PIDL 或字符串路径。|  
|[CMFCShellTreeCtrl::SetFlags](#setflags)|设置要筛选的树中上下文的标志 (类似于使用的标志`IShellFolder::EnumObjects`)。|  
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|设置当前之间创建关系`CMFCShellTreeCtrl`对象和一个`CMFCShellListCtrl`对象。|  
  
## <a name="remarks"></a>备注  
 此类扩展`CTreeCtrl`通过启用程序以将 Windows Shell 项包含在树中的类。 此类可与关联`CMFCShellListCtrl`对象以创建完整的资源管理器窗口。 然后，在树中选择一项将显示 Windows Shell 项的列表相关联的列表中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ctreectrl 类](../../mfc/reference/ctreectrl-class.md)  
  
 `CMFCShellTreeCtrl`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxshelltreeCtrl.h  
  
## <a name="example"></a>示例  
 下面的示例演示如何创建 `CMFCShellTreeCtrl` 类的对象。 此代码段属于[资源管理器示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Explorer #&4;](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer #&5;](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]  
  
##  <a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu  
 允许的快捷菜单。  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 一个布尔值，指定是否启用的快捷菜单。  
  
##  <a name="getflags"></a>CMFCShellTreeCtrl::GetFlags  
 返回为设置的标志[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)对象。  
  
```  
DWORD GetFlags() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`DWORD`值，该值指定标志的组合当前设置。  
  
### <a name="remarks"></a>备注  
 设置的标志`CMFCShellTreeCtrl`发送到此方法[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)每当刷新该对象。 您可以更改的标志[CMFCShellTreeCtrl::SetFlags](#setflags)方法。  
  
##  <a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath  
 检索中的项的路径[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)对象。  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    HTREEITEM htreeItem = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `strPath`  
 对字符串参数的引用。 该方法将写入此参数的项的路径。  
  
 [in] `htreeItem`  
 该方法检索此树控件项的路径。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果此方法失败，`strPath`包含空字符串。  
  
 如果未指定`hTreeItem`，此方法尝试获取当前选定项的字符串。 如果未不选定任何项和`hTreeItem`是`NULL`，此方法将失败。  
  
##  <a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList  
 返回一个指向[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象，它是与此关联[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象。  
  
```  
CMFCShellListCtrl* GetRelatedList() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CMFCShellListCtrl`与此树控件对象关联的对象。  
  
### <a name="remarks"></a>备注  
 通过使用`CMFCShellListCtrl`对象一起`CMFCShellTreeCtrl`对象时，您可以创建一个类似于资源管理器中的窗口。 使用方法[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)将两个类相关联。 它们是关联后，框架将自动更新`CMFCShellListCtrl`如果中的选定内容`CMFCShellTreeCtrl`更改。  
  
##  <a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnChildNotify(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* pLResult);
```  
  
### <a name="parameters"></a>参数  
 [in] `message`  
 [in] `wParam`  
 [in] `lParam`  
 [in] `pLResult`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>参数  
 [in] `pItem`  
 [in] `bSelected`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>参数  
 [in] `pItem`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="refresh"></a>CMFCShellTreeCtrl::Refresh  
 刷新并重新绘制[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)。  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>备注  
 调用此方法来刷新中显示的项的层次结构`CMFCShellTreeCtrl`。  
  
##  <a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath  
 选择中的项[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)基于提供的路径。  
  
```  
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszPath`  
 一个字符串，指定项的路径。  
  
 [in] `lpidl`  
 指定的项 PIDL  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，则，`E_FAIL`否则为。  
  
##  <a name="setflags"></a>CMFCShellTreeCtrl::SetFlags  
 设置要筛选的树中上下文的标志。  
  
```  
void SetFlags(
    DWORD dwFlags,  
    BOOL bRefresh = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwFlags`  
 要设置的标志。  
  
 [in] `bRefresh`  
 一个布尔值，指定是否`CMFCShellTreeCtrl`应立即刷新。  
  
### <a name="remarks"></a>备注  
 `CMFCShellTreeCtrl`传递所有标志设置为[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)。 有关不同标志的值的详细信息，请参阅[IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)。  
  
##  <a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList  
 将相关联[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象。  
  
```  
void SetRelatedList(CMFCShellListCtrl* pShellList);
```  
  
### <a name="parameters"></a>参数  
 [in] `pShellList`  
 一个指向`CMFCShellListCtrl`对象。  
  
### <a name="remarks"></a>备注  
 此方法将关联`CMFCShellListCtrl`与`CMFCShellTreeCtrl`。 这些对象可能会显示类似于资源管理器中的窗口为︰ 如果用户选择中的某个对象`CMFCShellTreeCtrl`、 关联中的项`CMFCShellListCtrl`将自动更新。  
  
 使用方法[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)检索`CMFCShellListCtrl`与关联`CMFCShellTreeCtrl`。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CTreeCtrl 类](../../mfc/reference/ctreectrl-class.md)   
 [CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)

