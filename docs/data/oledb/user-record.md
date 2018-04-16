---
title: "用户记录 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cbb073aceaff855de700eae6d8aede148f9b8bcc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="user-record"></a>用户记录
用户记录提供表示行集列数据的代码和数据结构。 在编译时或在运行时，可以创建用户记录。 当你创建提供程序使用 ATL OLE DB 提供程序向导时，向导将创建如下所示 （假设你指定"MyProvider"的提供程序名称 [短名称]） 的默认用户记录：  
  
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
  
 OLE DB 提供程序模板处理有关与客户端交互的所有 OLE DB 细节。 若要获取所需的响应的列数据，提供程序将调用`GetColumnInfo`函数，你必须将它们放在用户记录中。 你可以显式重写`GetColumnInfo`在用户记录中，例如，由声明它.h 文件中如下所示：  
  
```  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
 这等效于：  
  
```  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
 你还必须实现`GetColumnInfo`用户记录的.cpp 文件中。  
  
 PROVIDER_COLUMN_MAP 宏帮助创建`GetColumnInfo`函数：  
  
-   BEGIN_PROVIDER_COLUMN_MAP 定义的函数原型和的静态数组**ATLCOLUMNINFO**结构。  
  
-   PROVIDER_COLUMN_ENTRY 定义和初始化一个**ATLCOLUMNINFO**。  
  
-   END_PROVIDER_COLUMN_MAP 关闭数组和函数。 它还会为数组元素计数`pcCols`参数。  
  
 在运行时，创建用户记录时**GetColumnInfo**使用`pThis`参数来接收到的行集或命令实例的指针。 命令和行集必须支持`IColumnsInfo`接口，所以可以从该指针获取列信息。  
  
 **CommandClass**和**RowsetClass**的命令和使用用户记录的行集。  
  
 有关如何重写的更多详细示例`GetColumnInfo`在用户记录中，请参阅[动态确定返回给使用者列](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)