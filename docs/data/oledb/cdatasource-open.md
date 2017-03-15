---
title: "CDataSource::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDataSource::Open"
  - "ATL.CDataSource.Open"
  - "CDataSource::Open"
  - "CDataSource.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CDataSource::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 **CLSID**、**ProgID** 或 `CEnumerator` 名字对象打开到数据源的连接，或通过一个定位器对话框提示用户。  
  
## 语法  
  
```  
  
        HRESULT Open(  
   const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   HWND hWnd = GetActiveWindow( ),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET   
) throw( );  
HRESULT Open(   
   LPCWSTR szProgID,   
   DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(   
   LPCSTR szProgID,   
   LPCTSTR pName,   
   LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0   
) throw( );  
```  
  
#### 参数  
 `clsid`  
 \[in\] 数据提供程序的 **CLSID**。  
  
 *pPropSet*  
 \[in\] 指向一个 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构的数组的指针，该结构包含要设置的属性和值。  请参阅 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中 *OLE DB 程序员参考*中的[属性设置和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)。  
  
 *nPropertySets*  
 \[in\] 传入 *pPropSet* 参数的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构的数目。  
  
 *pName*  
 \[in\] 要连接的数据库的名称。  
  
 *pUserName*  
 \[in\] 用户的名称。  
  
 *pPassword*  
 \[in\] 用户的密码。  
  
 `nInitMode`  
 \[in\] 数据库初始化模式。  请参阅 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中 *OLE DB 程序员参考*中的[初始化属性](https://msdn.microsoft.com/en-us/library/ms723127.aspx)，查看有效初始化模式的列表。  如果 `nInitMode` 是零，则用于打开连接的属性集中不包含初始化模式。  
  
 `szProgID`  
 \[in\] 一个程序标识符。  
  
 `enumerator`  
 \[in\] 一个 [CEnumerator](../../data/oledb/cenumerator-class.md) 对象，用于获取在调用方不指定 **CLSID** 时打开连接的名字对象。  
  
 `hWnd`  
 \[in\] 将成为对话框父级的窗口的句柄。  使用函数重载（该函数重载使用 `hWnd` 参数）将自动调用服务组件；请参见备注了解详细信息。  
  
 `dwPromptOptions`  
 \[in\] 确定要显示的定位器对话框的样式。  请参阅 Msdasc.h 了解可能的值。  
  
## 返回值  
 一个标准 `HRESULT`。  
  
## 备注  
 使用 `hWnd` 参数的方法重载使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。  有关详细信息，请访问 [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)，参阅“OLE DB 程序员参考”中的“OLE DB 服务”。  
  
 不使用 `hWnd` 参数的方法重载无需使用 oledb32.dll 中的服务组件即可打开数据源对象。  使用这些函数重载打开的 [CDataSource](../../data/oledb/cdatasource-class.md) 对象将无法利用服务组件的任何功能。  
  
## 示例  
 下面的代码演示如何使用 OLE DB 模板打开 Jet 4.0 数据源。  你将 Jet 数据源视为 OLE DB 数据源。  但是，对 **Open** 的调用需要两个属性集：一个用于 **DBPROPSET\_DBINIT**，另一个用于 **DBPROPSET\_JETOLEDB\_DBINIT**，以便你可以设置 **DBPROP\_JETOLEDB\_DATABASEPASSWORD**。  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/CPP/cdatasource-open_1.cpp)]  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)