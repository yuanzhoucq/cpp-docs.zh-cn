---
title: "CDaoDatabaseInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoDatabaseInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoDatabaseInfo 结构"
  - "DAO（数据访问对象）, 数据库集合"
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoDatabaseInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoDatabaseInfo` 结构包含有关数据访问对象（DAO）定义的数据库对象的信息 。  
  
## 语法  
  
```  
  
      struct CDaoDatabaseInfo  
{  
   CString m_strName;       // Primary  
   BOOL m_bUpdatable;       // Primary  
   BOOL m_bTransactions;    // Primary  
   CString m_strVersion;    // Secondary  
   long m_lCollatingOrder;  // Secondary  
   short m_nQueryTimeout;   // Secondary  
   CString m_strConnect;    // All  
};  
```  
  
#### 参数  
 `m_strName`  
 唯一地命名单个数据库对象。  直接检索此属性，调用 [CDaoDatabase::GetName](../Topic/CDaoDatabase::GetName.md)。  有关详细信息，请参见主题“名称属性”在DAO 帮助中。  
  
 `m_bUpdatable`  
 指示更改是否可以更改数据库。  直接检索此属性，调用 [CDaoDatabase::CanUpdate](../Topic/CDaoDatabase::CanUpdate.md)。  有关详细信息，请参见主题“可更新属性”在DAO 帮助中。  
  
 *m\_bTransactions*  
 指示数据源是否支持事务 \- 可能后回滚一系列更改的记录 \(取消\) 或提交 \(保存\)。  如果数据库基于 Microsoft Jet 数据库引擎，事务属性不为零，并且可以使用事务。  其他数据库引擎可能不支持事务。  直接检索此属性，调用 [CDaoDatabase::CanTransact](../Topic/CDaoDatabase::CanTransact.md)。  有关详细信息，请参见主题“事务属性”在DAO 帮助中。  
  
 *m\_strVersion*  
 表示 Microsoft Jet 数据库引擎的版本。  若要直接检索此属性的值，则调用数据库对象的[GetVersion](../Topic/CDaoDatabase::GetVersion.md)成员函数。  有关详细信息，请参见主题“版本属性”在DAO 帮助中。  
  
 `m_lCollatingOrder`  
 文本中指定用于字符串比较或排序的排序顺序的序列。  可能的值包括：  
  
-   **dbSortGeneral** 使用常规 \(英语，法语，德语，葡萄牙语，意大利语和现代西班牙语\) 排序顺序。  
  
-   **dbSortArabic** 用阿拉伯语排序顺序。  
  
-   **dbSortCyrillic** 使用俄国排序顺序。  
  
-   **dbSortCzech** 使用捷克排序顺序。  
  
-   **dbSortDutch** 使用荷兰语排序顺序。  
  
-   **dbSortGreek**使用奥地利排序顺序。  
  
-   **dbSortHebrew** 使用希伯来排序顺序。  
  
-   **dbSortHungarian** 使用匈牙利排序顺序。  
  
-   使用**dbSortIcelandic** 冰岛排序顺序。  
  
-   **dbSortNorwdan** 用挪威丹麦或排序顺序。  
  
-   使用**dbSortPDXIntl** 冲突国际排序顺序。  
  
-   使用**dbSortPDXNor** 冲突挪威丹麦或排序顺序。  
  
-   **dbSortPDXSwe** 使用冲突瑞典语芬兰或排序顺序。  
  
-   **dbSortPolish** 使用波兰排序顺序。  
  
-   **dbSortSpanish** 使用西班牙排序顺序。  
  
-   **dbSortSwedFin** 用瑞典语或芬兰排序顺序。  
  
-   **dbSortTurkish** 用土耳其排序顺序。  
  
-   **dbSortUndefined** 排序顺序是未定义的或未知的。  
  
 有关更多信息，请参见主题“自定义 Windows 数据访问的注册表设置”DAO 帮助。  
  
 *m\_nQueryTimeout*  
 Microsoft Jet 数据库引擎等待的秒数，在超时错误之前，在ODBC 数据库之上运行一个查询时。  默认超时值为 60 秒。  当 QueryTimeout 设置为 0 后，超时值不发生；这可能导致程序停止响应。  若要直接检索此属性的值，则调用数据库对象的[GetQueryTimeout](../Topic/CDaoDatabase::GetQueryTimeout.md)成员函数。  有关详细信息，请参见主题“查询超时属性”在DAO 帮助中。  
  
 `m_strConnect`  
 提供有关开源数据库中的资源的信息。  有关连接字符串和直接检索属性值的信息，请参见 [CDaoDatabase::GetConnect](../Topic/CDaoDatabase::GetConnect.md) 成员函数。  有关更多信息，请参见DAO帮助中的中的“连接”主题。  
  
## 备注  
 数据库是类 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)的 MFC 对象的基础的DAO 对象。  为 Main，附属的引用和所有的指示信息如何由 [CDaoWorkspace::GetDatabaseInfo](../Topic/CDaoWorkspace::GetDatabaseInfo.md) 成员函数返回。  
  
 [CDaoWorkspace::GetDatabaseInfo](../Topic/CDaoWorkspace::GetDatabaseInfo.md) 成员函数检索的信息在 `CDaoDatabaseInfo` 结构存储。  数据库集合数据库对象中存储的 `CDaoWorkspace` 对象的调用 `GetDatabaseInfo`。  `CDaoDatabaseInfo` 还定义了函数调试版本的 `Dump` 成员。  您可以使用`Dump` 显示`CDaoDatabaseInfo`对象的内容。  
  
## 要求  
 **页眉：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoWorkspace::GetDatabaseCount](../Topic/CDaoWorkspace::GetDatabaseCount.md)