---
title: "使用者向导生成的方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OpenAll method
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- methods [C++], OLE DB Consumer Wizard-generated
- CloseDataSource method
- consumer wizard-generated classes and methods
- OpenDataSource method
- CloseAll method
- OpenRowset method
- GetRowsetProperties method
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7be8bbf011964411431d754afa058763e70e3265
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="consumer-wizard-generated-methods"></a>使用者向导生成的方法
ATL OLE DB 使用者向导和 MFC 应用程序向导生成的你应注意某些函数。 请注意，某些方法实现以不同方式在特性化项目中，因此有几条注意事项;下面介绍了每个用例。 有关查看插入代码的信息，请参阅 [调试插入代码](/visualstudio/debugger/how-to-debug-injected-code)。  
  
-   `OpenAll`打开数据源，行集，并开启书签，它们是否可用。  
  
-   `CloseAll`关闭所有打开的行集并释放所有的命令执行。  
  
-   `OpenRowset`OpenAll 打开使用者的行集或行集由调用。  
  
-   `GetRowsetProperties`检索指向与可以设置哪些属性设置的行集的属性。  
  
-   `OpenDataSource`打开数据源使用中指定的初始化字符串**数据链接属性**对话框。  
  
-   `CloseDataSource`关闭数据源以适当的方式。  
  
## <a name="openall-and-closeall"></a>OpenAll 和 CloseAll  
  
```  
HRESULT OpenAll();   
void CloseAll();  
```  
  
 以下示例演示在重复执行同一命令时如何调用 `OpenAll` 和 `CloseAll`。 比较中的代码示例[ccommand:: Close](../../data/oledb/ccommand-close.md)，其中说明了调用变体**关闭**和`ReleaseCommand`而不是`CloseAll`。  
  
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
  
## <a name="remarks"></a>备注  
 请注意，如果你定义`HasBookmark`方法，`OpenAll`代码设置 DBPROP_IRowsetLocate 属性; 请确保你只有这样做您访问接口支持该属性。  
  
## <a name="openrowset"></a>OpenRowset  
  
```  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
 **OpenAll**调用此方法以在使用者中打开行集或行集。 通常，不需要调用`OpenRowset`除非你想要使用多个数据源/会话/行集。 `OpenRowset`在命令或表类标头文件中声明：  
  
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
  
 特性以不同方式实现此方法。 此版本使用会话对象和默认为 db_command 中, 指定的命令字符串，尽管你可以将传递一个不同的命令字符串。 请注意，如果你定义`HasBookmark`方法，`OpenRowset`代码设置 DBPROP_IRowsetLocate 属性; 请确保你只有这样做您访问接口支持该属性。  
  
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
  
## <a name="getrowsetproperties"></a>GetRowsetProperties  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet);  
```  
  
 此方法检索到的行集的属性集; 的指针此指针可用于设置属性，例如 DBPROP_IRowsetChange。 `GetRowsetProperties`用在用户记录类，如下所示。 你可以修改此代码以设置其他行集属性：  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## <a name="remarks"></a>备注  
 不应定义全局`GetRowsetProperties`方法，因为它可能与冲突定义向导。 请注意，这是模板化和特性化项目; 中获得的向导生成的方法属性不会插入此代码。  
  
## <a name="opendatasource-and-closedatasource"></a>OpenDataSource 和 CloseDataSource  
  
```  
HRESULT OpenDataSource();   
void CloseDataSource();  
```  
  
## <a name="remarks"></a>备注  
 向导定义的方法`OpenDataSource`和`CloseDataSource`;`OpenDataSource`调用[cdatasource:: Openfrominitializationstring](../../data/oledb/cdatasource-openfrominitializationstring.md)。  
  
## <a name="see-also"></a>另请参阅  
 [使用向导创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)