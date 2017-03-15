---
title: "使用者向导生成的方法 | Microsoft Docs"
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
  - "特性插入的类和方法"
  - "CloseAll 方法"
  - "CloseDataSource 方法"
  - "使用者向导生成的类和方法"
  - "GetRowsetProperties 方法"
  - "方法 [C++], OLE DB 使用者向导生成的"
  - "OLE DB 使用者, 向导生成的类和方法"
  - "OpenAll 方法"
  - "OpenDataSource 方法"
  - "OpenRowset 方法"
  - "向导生成的类和方法"
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用者向导生成的方法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“ATL OLE DB 使用者向导”和“MFC 应用程序向导”生成某些应注意的函数。  请注意，某些方法在特性化项目中以不同的方式实现，因此有几个警告；下面涵盖了每种情况。  有关查看插入的代码的信息，请参见 [调试插入的代码](../Topic/How%20to:%20Debug%20Injected%20Code.md)。  
  
-   `OpenAll` 打开数据源、行集合，并且打开书签（如果书签可用）。  
  
-   `CloseAll` 关闭所有打开的行集合并且释放所有的命令执行。  
  
-   `OpenRowset` 由 OpenAll 调用以打开使用者的一个或多个行集合。  
  
-   `GetRowsetProperties` 检索指向行集合的属性集的指针，该指针可用来设置属性。  
  
-   `OpenDataSource` 使用在**“数据链接属性”**对话框中指定的初始化字符串打开数据源。  
  
-   `CloseDataSource` 以适当的方式关闭数据源。  
  
## OpenAll 和 CloseAll  
  
```  
HRESULT OpenAll();   
void CloseAll();  
```  
  
 下面的示例说明了当重复执行同一命令时如何能够调用 `OpenAll` 和 `CloseAll`。  比较 [CCommand::Close](../../data/oledb/ccommand-close.md) 中的代码示例，该示例显示了调用 **Close** 和 `ReleaseCommand` 而不是 `CloseAll` 的不同形式。  
  
```  
int main(int argc, char* argv[])  
{  
   HRESULT hr;  
  
   hr = CoInitialize(NULL);  
  
   CCustOrdersDetail rs;      // Your CCommand-derived class  
   rs.m_OrderID = 10248;      // Open order 10248  
   hr = rs.OpenAll();         // (Open also executes the command)  
   hr = rs.MoveFirst();         // Move to the first row and print it  
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );  
  
   // Close the first command execution  
   rs.Close();  
  
   rs.m_OrderID = 10249;      // Open order 10249 (a new order)  
   hr = rs.Open();            // (Open also executes the command)  
   hr = rs.MoveFirst();         // Move to the first row and print it  
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );  
  
   // Close the second command execution;  
   // Instead of rs.CloseAll() you could call  
   // rs.Close() and rs.ReleaseCommand():  
   rs.CloseAll();  
  
   CoUninitialize();  
   return 0;  
}  
```  
  
## 备注  
 请注意，如果定义 `HasBookmark` 方法，则 `OpenAll`  代码将设置 DBPROP\_IRowsetLocate 属性；请确保仅当提供程序支持该属性时才执行此操作。  
  
## OpenRowset  
  
```  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
 **OpenAll** 调用此方法以打开使用者中的一个或多个行集合。  一般情况下，除非您希望使用多个数据源\/会话\/行集，否则不需要调用 `OpenRowset`。  `OpenRowset` 在命令或表类头文件中声明：  
  
```  
// OLE DB Template version:  
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)  
{  
   HRESULT hr = Open(m_session, NULL, pPropSet);  
   #ifdef _DEBUG  
   if(FAILED(hr))  
      AtlTraceErrorRecords(hr);  
   #endif  
   return hr;  
}  
```  
  
 特性以不同方式实现此方法。  此版本采用一个会话对象和一个命令字符串，该命令字符串默认为在 db\_command 中指定的命令字符串（虽然可传递不同的字符串）。  请注意，如果定义 `HasBookmark` 方法，则 `OpenRowset` 代码将设置 DBPROP\_IRowsetLocate 属性；请确保仅在提供程序支持该属性时才执行此操作。  
  
```  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)  
{  
  
   DBPROPSET *pPropSet = NULL;  
   CDBPropSet propset(DBPROPSET_ROWSET);  
   __if_exists(HasBookmark)  
  
   {  
      propset.AddProperty(DBPROP_IRowsetLocate, true);  
      pPropSet= &propset;  
      }  
...  
}  
```  
  
## GetRowsetProperties  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet);  
```  
  
 此方法检索指向行集合的属性集的指针；可使用该指针设置属性（如 DBPROP\_IRowsetChange）。  在用户记录类中使用了 `GetRowsetProperties`，如下所示。  可以修改这些代码以设置其他行集合属性：  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## 备注  
 不应定义全局 `GetRowsetProperties` 方法，这是因为它可能与向导所定义的方法冲突。  请注意，这是在模板和特性化项目中获得的向导生成的方法；特性不插入这些代码。  
  
## OpenDataSource 和 CloseDataSource  
  
```  
HRESULT OpenDataSource();   
void CloseDataSource();  
```  
  
## 备注  
 向导定义 `OpenDataSource` 方法和 `CloseDataSource` 方法；`OpenDataSource` 调用 [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)。  
  
## 请参阅  
 [使用向导创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)