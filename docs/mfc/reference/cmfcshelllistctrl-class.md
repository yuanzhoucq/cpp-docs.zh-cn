---
title: "CMFCShellListCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
dev_langs:
- C++
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4b5204fe92685431ccdd2c6735553c9b7ce85bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl 类
`CMFCShellListCtrl`类提供 Windows 列表控件功能，并通过包含显示 shell 项列表的功能进行扩展。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|显示提供文件夹中包含的项的列表。|  
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|显示当前所显示的文件夹的父文件夹中包含的项的列表。|  
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|启用或禁用的快捷菜单。|  
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|检索当前文件夹的路径。|  
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|检索当前文件夹的名称。|  
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|返回当前列表控件项的 PIDL。|  
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|将指针返回到当前的 Shell 文件夹。|  
|[CMFCShellListCtrl::GetItemPath](#getitempath)|返回一个项的文本路径。|  
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|返回由列表控件显示 Shell 项类型。|  
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|检查当前所选的文件夹是否桌面文件夹。|  
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|它比较两个项时，框架将调用此方法。 (重写[CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems)。)|  
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|当框架检索列表控件显示的文件日期时调用。|  
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|调用时的框架会将一个列表控件的文件大小。|  
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|当框架检索列表控件项的图标时调用。|  
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|当框架会将列表控件项的文本时调用。|  
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|它将设置列的名称时，由框架调用。|  
|[CMFCShellListCtrl::Refresh](#refresh)|刷新并重新绘制列表控件。|  
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|设置的列表控件显示的项的类型。|  
  
## <a name="remarks"></a>备注  
 `CMFCShellListCtrl`类扩展的功能[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)通过使程序能够列出 Windows shell 项。 使用的显示格式是类似的浏览器窗口的列表视图。  
  
 A [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象可以与关联`CMFCShellListCtrl`对象以创建完整的资源管理器窗口。 然后，选择中的项`CMFCShellTreeCtrl`将导致`CMFCShellListCtrl`要列出的选定项的内容对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何创建的对象`CMFCShellListCtrl`类以及如何显示当前所显示的文件夹的父文件夹。 此代码片段属于[资源管理器示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
 `CMFCShellListCtrl`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxshelllistCtrl.h  
  
##  <a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder  
 显示提供的文件夹中包含的项的列表。  
  
```  
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszPath`  
 包含输入文件夹的路径的字符串。  
  
 [in] `lpItemInfo`  
 指向的指针`LPAFX_SHELLITEMINFO`描述要显示的文件夹结构。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，则，`E_FAIL`否则为。  
  
##  <a name="displayparentfolder"></a>CMFCShellListCtrl::DisplayParentFolder  
 更新[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象，以显示当前所显示的文件夹的父文件夹。  
  
```  
virtual HRESULT DisplayParentFolder();
```  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，则，`E_FAIL`否则为。  
  
##  <a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu  
 启用的快捷菜单。  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 一个布尔值，指定是否使用 framework，快捷菜单。  
  
##  <a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder  
 检索当前所选文件夹中的路径[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象。  
  
```  
BOOL GetCurrentFolder(CString& strPath) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `strPath`  
 对该方法将路径的输出一个字符串参数的引用。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法失败，如果没有在所选没有文件夹`CMFCShellListCtrl`。  
  
##  <a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName  
 检索当前所选文件夹中的名称[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象。  
  
```  
BOOL GetCurrentFolderName(CString& strName) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `strName`  
 对该方法将名称的写入一个字符串参数的引用。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法失败，如果没有在所选没有文件夹`CMFCShellListCtrl`。  
  
##  <a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList  
 返回当前选定项的 PIDL。  
  
```  
LPITEMIDLIST GetCurrentItemIdList() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前项 PIDL。  
  
##  <a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder  
 获取一个指针指向中的当前选定项[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象。  
  
```  
const IShellFolder* GetCurrentShellFolder() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[IShellFolder 接口](http://msdn.microsoft.com/library/windows/desktop/bb775075)为所选对象。  
  
### <a name="remarks"></a>备注  
 此方法返回`NULL`如果没有任何对象当前所选。  
  
##  <a name="getitempath"></a>CMFCShellListCtrl::GetItemPath  
 检索项的路径。  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    int iItem) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `strPath`  
 对接收路径的字符串的引用。  
  
 [in] `iItem`  
 列表项的索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 由提供的索引`iItem`基于当前显示的项[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象。  
  
##  <a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes  
 返回的项显示的类型[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象。  
  
```  
SHCONTF GetItemTypes() const;  
```  
  
### <a name="return-value"></a>返回值  
 A [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539)包含的项中列出的类型的值`CMFCShellListCtrl`。  
  
### <a name="remarks"></a>备注  
 若要设置的项中列出的类型`CMFCShellListCtrl`，调用[CMFCShellListCtrl::SetItemTypes](#setitemtypes)。  
  
##  <a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop  
 确定文件夹是否显示在[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象是桌面的文件夹。  
  
```  
BOOL IsDesktop() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果显示的文件夹是桌面文件夹中。`FALSE`否则为。  
  
##  <a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>参数  
 [in] `lParam1`  
 [in] `lParam2`  
 [in] `iColumn`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate  
 它必须转换相关联的对象转换为字符串的日期时，框架将调用此方法。  
  
```  
virtual void OnFormatFileDate(
    const CTime& tmFile,  
    CString& str);
```  
  
### <a name="parameters"></a>参数  
 [in] `tmFile`  
 与文件相关联的日期。  
  
 [out] `str`  
 包含格式化的文件日期的字符串。  
  
### <a name="remarks"></a>备注  
 当[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象显示与文件相关联的日期时，它必须将该日期转换为字符串格式。 `CMFCShellListCtrl`使用此方法来使该转换。 默认情况下，此方法使用当前区域设置来设置日期格式转换为字符串。  
  
##  <a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize  
 对象大小转换为字符串时，框架将调用此方法。  
  
```  
virtual void OnFormatFileSize(
    long lFileSize,  
    CString& str);
```  
  
### <a name="parameters"></a>参数  
 [in] `lFileSize`  
 框架将显示文件的大小。  
  
 [out] `str`  
 一个字符串，包含格式的文件大小。  
  
### <a name="remarks"></a>备注  
 当[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)显示文件的大小所需要的对象，它必须转换为字符串格式的文件大小。 `CMFCShellListCtrl`使用此方法来使该转换。 默认情况下，此方法将文件大小从字节转换为千字节为单位，然后使用当前区域设置来格式化为字符串的大小。  
  
##  <a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon  
 框架调用此方法来检索与 shell 列表项关联的图标。  
  
```  
virtual int OnGetItemIcon(
    int iItem,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>参数  
 [in] `iItem`  
 项的索引。  
  
 [in] `pItem`  
 A`LPAFX_SHELLITEMINFO`描述的项的参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则此图标图像的索引如果函数失败，则为-1。  
  
### <a name="remarks"></a>备注  
 图标图像索引基于系统映像列表。  
  
 默认情况下，此方法依赖于`pItem`参数。 值`iItem`中的默认实现不使用。 你可以使用`iItem`来实现自定义行为。  
  
##  <a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText  
 它必须检索 shell 项的文本时，框架将调用此方法。  
  
```  
virtual CString OnGetItemText(
    int iItem,  
    int iColumn,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>参数  
 [in] `iItem`  
 项的索引。  
  
 [in] `iColumn`  
 感兴趣的列。  
  
 [in] `pItem`  
 A`LPAFX_SHELLITEMINFO`描述的项的参数。  
  
### <a name="return-value"></a>返回值  
 A `CString` ，其中包含与项关联的文本。  
  
### <a name="remarks"></a>备注  
 在每个项`CMFCShellListCtrl`对象可能具有一个或多个列中的文本。 当框架调用此方法时，它指定对感兴趣的列。 如果手动调用此函数，还必须指定你感兴趣的列。  
  
 默认情况下，此方法依赖于`pItem`参数，以确定哪一项到进程。 值`iItem`中的默认实现不使用。  
  
##  <a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns  
 它将设置列的名称时，框架将调用此方法。  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>备注  
 默认情况下，框架将创建四列中的`CMFCShellListCtrl`对象。 这些列的名称是`Name`， `Size`， `Type`，和`Modified`。 你可以重写此方法以自定义其名称和列数。  
  
##  <a name="refresh"></a>CMFCShellListCtrl::Refresh  
 刷新并重新绘制[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象。  
  
```  
virtual HRESULT Refresh();
```  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，则，否则为一个错误值。  
  
### <a name="remarks"></a>备注  
 调用此方法以刷新显示的项列表`CMFCShellListCtrl`对象。  
  
##  <a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes  
 设置中列出的项的类型[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象。  
  
```  
void SetItemTypes(SHCONTF nTypes);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTypes`  
 项的列表类型`CMFCShellListCtrl`对象支持。  
  
### <a name="remarks"></a>备注  
 项类型的列表的详细信息，请参阅[SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539)。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)   
 [CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)
