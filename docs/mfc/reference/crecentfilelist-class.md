---
title: "CRecentFileList 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
dev_langs:
- C++
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 968c15b1382233dc166a174e4ef074033c76619c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crecentfilelist-class"></a>CRecentFileList 类
支持最近使用的 (MRU) 文件列表的控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CRecentFileList  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CRecentFileList::CRecentFileList](#crecentfilelist)|构造 `CRecentFileList` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRecentFileList::Add](#add)|将文件添加到 MRU 文件列表。|  
|[CRecentFileList::GetDisplayName](#getdisplayname)|提供的 MRU filename 菜单显示的显示名称。|  
|[CRecentFileList::GetSize](#getsize)|检索 MRU 文件列表中的文件数。|  
|[CRecentFileList::ReadList](#readlist)|从注册表中读取 MRU 文件列表或。INI 文件。|  
|[CRecentFileList::Remove](#remove)|从 MRU 文件列表中移除的文件。|  
|[CRecentFileList::UpdateMenu](#updatemenu)|更新 MRU 文件列表的菜单显示。|  
|[CRecentFileList::WriteList](#writelist)|从注册表中写入 MRU 文件列表或。INI 文件。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CRecentFileList::operator]](#operator_at)|返回`CString`位于给定位置的对象。|  
  
## <a name="remarks"></a>备注  
 可以添加到文件，或将其从 MRU 文件列表中删除，可以读取或写入注册表的文件列表或。可以更新 INI 文件，并显示 MRU 文件列表的菜单。  
  
 有关 MRU 菜单项的详细信息，请参阅  
  
-   知识库文章 Q243751： 如何： 针对 MRU 菜单项的 MFC 应用程序中添加命令处理程序  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CRecentFileList`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxadv.h  
  
##  <a name="add"></a>CRecentFileList::Add  
 将文件添加到最近使用的 (MRU) 文件列表。  
  
```  
virtual void Add(LPCTSTR lpszPathName);

 
virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

 
void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

 
void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

 
void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 指定要添加到列表的路径名。  
  
 `lpszAppID`  
 指定应用程序的应用程序用户模型 ID。  
  
 `pItem`  
 指定指向要添加到列表 Shell 项的指针。  
  
 `pLink`  
 指定命令行程序链接到添加到列表的指针。  
  
 `pidl`  
 指定应添加到新的文档文件夹 shell 项 IDLIST。  
  
### <a name="remarks"></a>备注  
 文件名称将添加到 MRU 列表的顶部。 如果 MRU 列表中已存在的文件名称，则它将移动到顶部。  
  
##  <a name="crecentfilelist"></a>CRecentFileList::CRecentFileList  
 构造 `CRecentFileList` 对象。  
  
```  
CRecentFileList(
    UINT nStart,  
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntryFormat,  
    int nSize,  
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```  
  
### <a name="parameters"></a>参数  
 `nStart`  
 偏移量 MRU （最近使用） 的文件列表的菜单显示的编号。  
  
 `lpszSection`  
 指向的注册表或应用程序的部分的名称。其中 MRU 文件列表是读取和/或写入 INI 文件。  
  
 `lpszEntryFormat`  
 指向一个格式字符串要用于存储在注册表或应用程序的条目的名称。INI 文件。  
  
 `nSize`  
 MRU 文件列表中的文件的最大数量。  
  
 `nMaxDispLen`  
 最大长度 （以字符为单位，可用于菜单显示的是 MRU 文件列表中的文件名）。  
  
### <a name="remarks"></a>备注  
 格式字符串指向的`lpszEntryFormat`应包含"%d"，它将用来替换每个 MRU 项的索引。 例如，如果格式字符串为`"file%d"`然后条目将被命名为`file0`， `file1`，依次类推。  
  
##  <a name="getdisplayname"></a>CRecentFileList::GetDisplayName  
 获取在 MRU 文件列表中，在 MRU 列表的菜单显示中使用的文件的显示名称。  
  
```  
virtual BOOL GetDisplayName(
    CString& strName,  
    int nIndex,  
    LPCTSTR lpszCurDir,  
    int nCurDir,  
    BOOL bAtLeastName = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 `strName`  
 要在 MRU 文件菜单列表中显示其名称的文件的完整路径。  
  
 `nIndex`  
 MRU 文件列表中的文件的从零开始索引。  
  
 *lpszCurDir*  
 字符串，它包含当前目录。  
  
 *nCurDir*  
 当前目录字符串的长度。  
  
 `bAtLeastName`  
 如果非零值，指示应返回文件的基名称，即使它超过了最大显示长度 (作为传递`nMaxDispLen`参数`CRecentFileList`构造函数)。  
  
### <a name="return-value"></a>返回值  
 **FALSE**中是否存在任何 filename 中指定索引处最近使用的 (MRU) 文件列表。  
  
### <a name="remarks"></a>备注  
 如果该文件位于当前目录中，该函数将离开停止显示的目录。 如果文件名太长，被剥离的目录和扩展。 如果文件名仍然太长，显示名称设置为空字符串中，除非`bAtLeastName`为非零值。  
  
##  <a name="getsize"></a>CRecentFileList::GetSize  
 检索 MRU 文件列表中的文件数。  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 在当前的文件数个最近使用 (过的 MRU) 文件列表。  
  
##  <a name="operator_at"></a>CRecentFileList::operator]  
 重载的下标 ( `[]`) 运算符将返回单个`CString`由中从零开始的索引指定`nIndex`。  
  
```  
CString& operator[ ](int nindex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 从零开始的索引`CString`中的一组`CString`s。  
  
##  <a name="readlist"></a>CRecentFileList::ReadList  
 读取最近使用的从注册表或应用程序的 (MRU) 文件列表。INI 文件。  
  
```  
virtual void ReadList();
```  
  
##  <a name="remove"></a>CRecentFileList::Remove  
 从 MRU 文件列表中移除的文件。  
  
```  
virtual void Remove(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要从最近使用的 (MRU) 文件列表中删除的文件的从零开始索引。  
  
##  <a name="updatemenu"></a>CRecentFileList::UpdateMenu  
 更新 MRU 文件列表的菜单显示。  
  
```  
virtual void UpdateMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向的指针[CCmdUI](../../mfc/reference/ccmdui-class.md)的最近使用的 (MRU) 文件列表菜单对象。  
  
##  <a name="writelist"></a>CRecentFileList::WriteList  
 将最近使用的 (MRU) 文件列表到注册表或应用程序的。INI 文件。  
  
```  
virtual void WriteList();
```  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)



