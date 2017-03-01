---
title: "CRecentFileList 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRecentFileList
dev_langs:
- C++
helpviewer_keywords:
- files [C++], most recently used
- MRU files
- CRecentFileList class
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
caps.latest.revision: 19
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
ms.openlocfilehash: 5d18daee2e4d809c750ae4654d731888df1db39e
ms.lasthandoff: 02/24/2017

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
|[CRecentFileList::GetDisplayName](#getdisplayname)|提供菜单显示 MRU 文件名的显示名称。|  
|[CRecentFileList::GetSize](#getsize)|检索 MRU 文件列表中的文件数。|  
|[CRecentFileList::ReadList](#readlist)|从注册表中读取 MRU 文件列表或。INI 文件中。|  
|[CRecentFileList::Remove](#remove)|从 MRU 文件列表中删除一个文件。|  
|[CRecentFileList::UpdateMenu](#updatemenu)|更新 MRU 文件列表的菜单显示。|  
|[CRecentFileList::WriteList](#writelist)|从注册表中写入 MRU 文件列表或。INI 文件中。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CRecentFileList::operator]](#operator_at)|返回`CString`给定位置处的对象。|  
  
## <a name="remarks"></a>备注  
 可以添加到文件，或将其从 MRU 文件列表中删除，文件列表可以读取或写入注册表或。可以更新 INI 文件和显示 MRU 文件列表菜单。  
  
 MRU 菜单项的详细信息，请参阅  
  
-   知识库文章 Q243751︰ 如何︰ 添加命令处理程序，MFC 应用程序中的 MRU 菜单项  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CRecentFileList`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxadv.h  
  
##  <a name="a-nameadda--crecentfilelistadd"></a><a name="add"></a>CRecentFileList::Add  
 将文件添加到最近使用过的 (MRU) 文件列表。  
  
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
 为应用程序指定应用程序用户模型 ID。  
  
 `pItem`  
 指定要添加到列表的命令行程序项的指针。  
  
 `pLink`  
 指定命令行程序链接到添加到列表的指针。  
  
 `pidl`  
 指定应添加到最近文档文件夹的命令行程序项 IDLIST。  
  
### <a name="remarks"></a>备注  
 文件名称将添加到 MRU 列表的顶部。 如果在 MRU 列表中已存在的文件名称，则它将移动到顶部。  
  
##  <a name="a-namecrecentfilelista--crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a>CRecentFileList::CRecentFileList  
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
 在菜单上显示的 MRU （最近使用） 文件列表中的编号的偏移量。  
  
 `lpszSection`  
 指向的注册表或应用程序的部分的名称。其中 MRU 文件列表是读取和/或写入 INI 文件中。  
  
 `lpszEntryFormat`  
 指向要用于存储在注册表或该应用程序中的数据项的名称的格式字符串。INI 文件中。  
  
 `nSize`  
 MRU 文件列表中的文件的最大数量。  
  
 `nMaxDispLen`  
 最大长度 （以字符为单位，可用于菜单显示的是 MRU 文件列表中的文件名）。  
  
### <a name="remarks"></a>备注  
 格式字符串由指向`lpszEntryFormat`应包含"%d"，它将用来替换每个 MRU 项的索引。 例如，如果格式字符串是`"file%d"`然后条目将被命名为`file0`， `file1`，依次类推。  
  
##  <a name="a-namegetdisplaynamea--crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a>CRecentFileList::GetDisplayName  
 获取文件，在 MRU 文件列表中，以便使用 MRU 列表的菜单显示中的显示名称。  
  
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
 其名称将在 MRU 文件菜单列表中显示的文件的完整路径。  
  
 `nIndex`  
 MRU 文件列表中的文件的从零开始索引。  
  
 *lpszCurDir*  
 字符串，它包含当前目录。  
  
 *nCurDir*  
 在当前目录字符串的长度。  
  
 `bAtLeastName`  
 如果非零值，指示应返回该文件的基名称，即使它超过了最大显示长度 (作为传递`nMaxDispLen`参数`CRecentFileList`构造函数)。  
  
### <a name="return-value"></a>返回值  
 **FALSE**中是否存在不没有文件名中指定索引处的最近使用过的 (MRU) 文件列表。  
  
### <a name="remarks"></a>备注  
 如果该文件位于当前目录中，该函数将保留关闭显示的目录。 如果文件名太长，目录和扩展插件将被去除。 如果文件名仍然太长，显示名称设置为空字符串中，除非`bAtLeastName`为非零值。  
  
##  <a name="a-namegetsizea--crecentfilelistgetsize"></a><a name="getsize"></a>CRecentFileList::GetSize  
 检索 MRU 文件列表中的文件数。  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 在当前的文件数最近使用 (过的 MRU) 文件列表。  
  
##  <a name="a-nameoperatorata--crecentfilelistoperator--"></a><a name="operator_at"></a>CRecentFileList::operator]  
 重载的下标 ( `[]`) 运算符将返回单个`CString`由中从零开始的索引指定`nIndex`。  
  
```  
CString& operator[ ](int nindex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 从零开始的索引`CString`在一组`CString`s。  
  
##  <a name="a-namereadlista--crecentfilelistreadlist"></a><a name="readlist"></a>CRecentFileList::ReadList  
 读取最近使用的从注册表或应用程序的 (MRU) 文件列表。INI 文件中。  
  
```  
virtual void ReadList();
```  
  
##  <a name="a-nameremovea--crecentfilelistremove"></a><a name="remove"></a>CRecentFileList::Remove  
 从 MRU 文件列表中删除一个文件。  
  
```  
virtual void Remove(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要从最近使用过的 (MRU) 文件列表中删除的文件的从零开始索引。  
  
##  <a name="a-nameupdatemenua--crecentfilelistupdatemenu"></a><a name="updatemenu"></a>CRecentFileList::UpdateMenu  
 更新 MRU 文件列表的菜单显示。  
  
```  
virtual void UpdateMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 一个指向[CCmdUI](../../mfc/reference/ccmdui-class.md)最近使用过 (的 MRU) 文件列表菜单的对象。  
  
##  <a name="a-namewritelista--crecentfilelistwritelist"></a><a name="writelist"></a>CRecentFileList::WriteList  
 写入最近使用的 (MRU) 文件列表到注册表或应用程序的。INI 文件中。  
  
```  
virtual void WriteList();
```  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)




