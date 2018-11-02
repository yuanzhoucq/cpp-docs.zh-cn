---
title: 使用者向导生成的方法
ms.date: 11/04/2016
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
ms.openlocfilehash: 4c364d0caccfc422b91a68e15704628a949ef67b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635794"
---
# <a name="consumer-wizard-generated-methods"></a>使用者向导生成的方法

**ATL OLE DB 使用者向导**并**MFC 应用程序向导**生成其中应注意某些函数。 实施某些方法以不同的方式在特性化项目中，因此有几条注意事项;下面介绍了每种情况。 有关查看插入代码的信息，请参阅 [调试插入代码](/visualstudio/debugger/how-to-debug-injected-code)。

- `OpenAll` 打开数据源，行集，并开启书签，如果它们可用。

- `CloseAll` 关闭所有打开的行集并释放所有命令执行。

- `OpenRowset` 由调用`OpenAll`打开使用者的行集或行集。

- `GetRowsetProperties` 检索指向设置的可以设置哪些属性的行集的属性。

- `OpenDataSource` 打开使用初始化字符串中指定的数据源**数据链接属性**对话框。

- `CloseDataSource` 以适当的方式关闭数据源。

## <a name="openall-and-closeall"></a>OpenAll 和 CloseAll

```cpp
HRESULT OpenAll(); 

void CloseAll();
```

以下示例演示在重复执行同一命令时如何调用 `OpenAll` 和 `CloseAll`。 比较中的代码示例[ccommand:: Close](../../data/oledb/ccommand-close.md)，它显示了调用一种变体`Close`并`ReleaseCommand`而不是`CloseAll`。

```cpp
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

### <a name="remarks"></a>备注

如果定义了`HasBookmark`方法，`OpenAll`的代码设置`DBPROP_IRowsetLocate`属性; 请确保您才这样做如果您的提供程序支持该属性。

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version: 
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` 调用此方法以在使用者中打开行集或行集。 通常情况下，您无需调用`OpenRowset`除非你想要使用多个数据源/会话/行集。 `OpenRowset` 命令或表类标头文件中声明：

```cpp
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

属性以不同方式实现此方法。 此版本需要会话对象，并默认为 db_command 中, 指定的命令字符串，尽管可以将传递一个不同的命令字符串。 如果定义了`HasBookmark`方法，`OpenRowset`的代码设置`DBPROP_IRowsetLocate`属性; 请确保您才这样做如果您的提供程序支持该属性。

```cpp
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

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet);
```

此方法检索一个指向行集的属性集;可以使用此指针设置属性，例如`DBPROP_IRowsetChange`。 `GetRowsetProperties` 可在用户记录类，如下所示。 可以修改此代码以设置其他行集属性：

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>备注

不应定义一个全局`GetRowsetProperties`方法因为它可能与其中一个冲突定义向导。 这是向导生成的方法，您可对模板化和特性化项目;属性将不插入此代码。

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource 和 CloseDataSource

```cpp
HRESULT OpenDataSource(); 

void CloseDataSource();
```

### <a name="remarks"></a>备注

该向导定义的方法`OpenDataSource`和`CloseDataSource`;`OpenDataSource`调用[cdatasource:: Openfrominitializationstring](../../data/oledb/cdatasource-openfrominitializationstring.md)。

## <a name="see-also"></a>请参阅

[使用向导创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)