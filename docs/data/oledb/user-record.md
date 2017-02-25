---
title: "用户记录 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序, 用户记录"
  - "记录, 用户"
  - "行集合, 用户记录"
  - "用户记录"
  - "用户记录, 描述"
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 用户记录
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用户记录提供代码和数据结构来表示行集合的列数据。  用户记录可在编译时或运行时创建。  当您使用“ATL OLE DB 提供程序向导”创建提供程序时，该向导会创建一个类似下面这样的默认用户记录（假设您将提供程序名称 \[简称\] 指定为“MyProvider”）：  
  
```  
class CWindowsFile:  
   public WIN32_FIND_DATA  
{  
public:  
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)  
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)  
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)  
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)  
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)  
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)  
END_PROVIDER_COLUMN_MAP()  
  
};  
```  
  
 OLE DB 提供程序模板处理与客户端交互有关的所有 OLE DB 细节。  为获取响应所需的列数据，提供程序调用 `GetColumnInfo` 函数，您必须将该函数放在用户记录中。  可以在用户记录中显式重写 `GetColumnInfo`，例如，在 .h 文件中声明它，如下所示：  
  
```  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
 这等效于：  
  
```  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
 还必须在用户记录的 .cpp 文件中实现 `GetColumnInfo`。  
  
 PROVIDER\_COLUMN\_MAP 宏帮助创建 `GetColumnInfo` 函数：  
  
-   BEGIN\_PROVIDER\_COLUMN\_MAP 定义函数原型和一个静态 **ATLCOLUMNINFO** 结构数组。  
  
-   PROVIDER\_COLUMN\_ENTRY 定义和初始化单个 **ATLCOLUMNINFO**。  
  
-   END\_PROVIDER\_COLUMN\_MAP 关闭数组和函数。  它还将数组元素计数放在 `pcCols` 参数中。  
  
 当在运行时创建用户记录时，**GetColumnInfo** 使用 `pThis` 参数接收指向行集合或命令实例的指针。  命令和行集合必须支持 `IColumnsInfo` 接口，以便可从该指针获得列信息。  
  
 **CommandClass** 和 **RowsetClass** 是使用用户记录的命令和行集合。  
  
 有关如何在用户记录中重写 `GetColumnInfo` 的更多详细信息，请参见[动态确定返回给使用者的列](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## 请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)