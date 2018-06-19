---
title: CShellManager 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
dev_langs:
- C++
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9849ebea812ecdb98a686e140c7b9d280634938d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378351"
---
# <a name="cshellmanager-class"></a>CShellManager 类
实现可使你使用指向标识符列表 (PIDL) 的指针的几种方法。  
  
## <a name="syntax"></a>语法  
  
```  
class CShellManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CShellManager::CShellManager](#cshellmanager)|构造 `CShellManager` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CShellManager::BrowseForFolder](#browseforfolder)|显示一个对话框，使用户能够选择 shell 文件夹。|  
|[CShellManager::ConcatenateItem](#concatenateitem)|连接两个 Pidl。|  
|[CShellManager::CopyItem](#copyitem)|创建新 PIDL 并将提供的 PIDL 复制到它。|  
|[CShellManager::CreateItem](#createitem)|创建指定大小的新 PIDL。|  
|[CShellManager::FreeItem](#freeitem)|删除提供的 PIDL。|  
|[CShellManager::GetItemCount](#getitemcount)|在提供 PIDL 中返回的项数。|  
|[CShellManager::GetItemSize](#getitemsize)|返回提供 PIDL 的大小。|  
|[CShellManager::GetNextItem](#getnextitem)|从 PIDL 返回的下一项。|  
|[CShellManager::GetParentItem](#getparentitem)|检索提供的项的父项。|  
|[CShellManager::ItemFromPath](#itemfrompath)|检索由提供的路径标识的项 PIDL。|  
  
## <a name="remarks"></a>备注  
 方法`CShellManager`类 Pidl 所有处理。 PIDL 是 shell 对象的唯一标识符。  
  
 不应创建`CShellManager`手动对象。 它将由你的应用程序的框架自动创建。 但是，你应调用[CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)在初始化过程中你的应用程序。 若要获取指向 shell 管理器为你的应用程序的指针，调用[CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CShellManager](../../mfc/reference/cshellmanager-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxshellmanager.h  
  
##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder  
 显示一个对话框，使用户能够选择 shell 文件夹。  
  
```  
BOOL BrowseForFolder(
    CString& strOutFolder,  
    CWnd* pWndParent = NULL,  
    LPCTSTR lplszInitialFolder = NULL,  
    LPCTSTR lpszTitle = NULL,  
    UINT ulFlags = BIF_RETURNONLYFSDIRS,  
    LPINT piFolderImage = NULL);
```  
  
### <a name="parameters"></a>参数  
 [out] `strOutFolder`  
 该方法用于存储所选文件夹的路径的字符串。  
  
 [in] `pWndParent`  
 指向父窗口的指针。  
  
 [in] `lplszInitialFolder`  
 一个字符串，包含在显示的对话框时，默认情况下选择的文件夹。  
  
 [in] `lpszTitle`  
 对话框标题。  
  
 [in] `ulFlags`  
 指定对话框中的选项的标志。 请参阅[BROWSEINFO](http://msdn.microsoft.com/library/windows/desktop/bb773205)有关详细说明。  
  
 [out] `piFolderImage`  
 指向方法写入所选文件夹的图像索引的位置的整数值的指针。  
  
### <a name="return-value"></a>返回值  
 非零，如果用户从对话框; 选择一个文件夹否则为 0。  
  
### <a name="remarks"></a>备注  
 在调用此方法时，应用程序将创建并显示一个对话框，使用户能够选择的文件夹。 该方法将写入到的文件夹的路径`strOutFolder`参数。  
  
### <a name="example"></a>示例  
 下面的示例演示如何检索到的引用`CShellManager`通过使用对象`CWinAppEx::GetShellManager`方法以及如何使用`BrowseForFolder`方法。 此代码片段属于[资源管理器示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]  
  
##  <a name="concatenateitem"></a>  CShellManager::ConcatenateItem  
 创建包含两个 Pidl 的新列表。  
  
```  
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,  
    LPCITEMIDLIST pidl2);
```  
  
### <a name="parameters"></a>参数  
 [in] `pidl1`  
 第一项。  
  
 [in] `pidl2`  
 第二个项。  
  
### <a name="return-value"></a>返回值  
 指向新的项列表，如果函数成功，否则`NULL`。  
  
### <a name="remarks"></a>备注  
 此方法创建一个新[ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321)足够大，使之同时包含`pidl1`和`pidl2`。 然后将它复制`pidl1`和`pidl2`到新列表。  
  
##  <a name="copyitem"></a>  CShellManager::CopyItem  
 将复制的项列表。  
  
```  
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```  
  
### <a name="parameters"></a>参数  
 [in] `pidlSource`  
 原始的项列表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则新创建的项列表指向的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 新创建的项列表包含与源项列表的大小相同。  
  
##  <a name="createitem"></a>  CShellManager::CreateItem  
 创建新 PIDL。  
  
```  
LPITEMIDLIST CreateItem(UINT cbSize);
```  
  
### <a name="parameters"></a>参数  
 [in] `cbSize`  
 项列表的大小。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建的项列表指向的指针否则为`NULL`。  
  
##  <a name="cshellmanager"></a>  CShellManager::CShellManager  
 构造 `CShellManager` 对象。  
  
```  
CShellManager();
```  
  
### <a name="remarks"></a>备注  
 在大多数情况下，你不必创建`CShellManager`直接。 默认情况下，框架会自动进行创建。 若要获取指向的指针`CShellManager`，调用[CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。 如果创建`CShellManager`手动，必须使用该方法初始化它[CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)。  
  
##  <a name="freeitem"></a>  CShellManager::FreeItem  
 删除的项列表。  
  
```  
void FreeItem(LPITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>参数  
 [in] `pidl`  
 若要删除项列表。  
  
##  <a name="getitemcount"></a>  CShellManager::GetItemCount  
 在项列表中返回的项数。  
  
```  
UINT GetItemCount(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>参数  
 [in] `pidl`  
 指向的项列表的指针。  
  
### <a name="return-value"></a>返回值  
 在项列表中的项的数目。  
  
##  <a name="getitemsize"></a>  CShellManager::GetItemSize  
 返回的项列表的大小。  
  
```  
UINT GetItemSize(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>参数  
 [in] `pidl`  
 指向的项列表的指针。  
  
### <a name="return-value"></a>返回值  
 项列表的大小。  
  
##  <a name="getnextitem"></a>  CShellManager::GetNextItem  
 检索的项标识符列表 (PIDL) 从指针的下一项。  
  
```  
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>参数  
 [in] `pidl`  
 要循环的项列表。  
  
### <a name="return-value"></a>返回值  
 指向列表中的下一项的指针。  
  
### <a name="remarks"></a>备注  
 如果列表没有更多的项，此方法返回`NULL`。  
  
##  <a name="getparentitem"></a>  CShellManager::GetParentItem  
 检索到的项标识符列表 (PIDL) 的指针的父级。  
  
```  
int GetParentItem(
    LPCITEMIDLIST lpidl,  
    LPITEMIDLIST& lpidlParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpidl`  
 将检索其父 PIDL。  
  
 [out] `lpidlParent`  
 对该方法将在其中存储结果 PIDL 的引用。  
  
### <a name="return-value"></a>返回值  
 父 PIDL 的级别。  
  
### <a name="remarks"></a>备注  
 PIDL 的级别是相对于桌面。 桌面 PIDL 被视为具有 0 的级别。  
  
##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath  
 检索到的项标识符列表 (PIDL) 从由字符串路径标识的项的指针。  
  
```  
HRESULT ItemFromPath(
    LPCTSTR lpszPath,  
    LPITEMIDLIST& pidl);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszPath`  
 一个字符串，指定项的路径。  
  
 [out] `pidl`  
 对 PIDL 的引用。 该方法使用此 PIDL 存储指向其返回值的指针。  
  
### <a name="return-value"></a>返回值  
 返回`NOERROR`如果成功，则 OLE 定义的错误值。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
