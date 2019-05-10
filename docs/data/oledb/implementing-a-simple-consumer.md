---
title: 实现简单使用者
ms.date: 10/12/2018
helpviewer_keywords:
- clients, creating
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 9067e8645fac9a06bd85ca5ef18fbaff45d16aae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390797"
---
# <a name="implementing-a-simple-consumer"></a>实现简单使用者

以下主题说明如何编辑创建的文件**MFC 应用程序向导**并**ATL OLE DB 使用者向导**创建简单使用者。 此示例包含以下部分：

- [使用者检索数据](#retrieve)演示如何从数据库表中读取所有数据，表中的使用者中实现代码。

- [向使用者添加书签支持](#bookmark)演示如何向使用者添加书签支持。

> [!NOTE]
> 可以使用在本部分中描述的使用者应用程序来测试`MyProv`和`Provider`示例提供程序。

> [!NOTE]
> 若要生成使用者应用程序来测试`MyProv`(相同的提供程序中所述[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md))，如中所述，必须包含书签支持[到添加书签支持使用者](#bookmark)。

## <a name="retrieve" ></a> 使用者检索数据

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>若要修改控制台应用程序使用 OLE DB 使用者

1. 在`MyCons.cpp`，更改主代码的方法是插入的粗体文本，如下所示：

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "stdafx.h"
    #include "Products.h"
    ...
    int main(int argc, char* argv[])
    {
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset
       CProducts rs;
       hr = rs.OpenAll();
       ATLASSERT(SUCCEEDED(hr ) );
       hr = rs.MoveFirst();   // Iterate through the rowset
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row
         printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",
           rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );
         hr = rs.MoveNext();   }
       rs.Close();
       rs.ReleaseCommand();
       CoUninitialize();

       return 0;
    }
    ```

## <a name="bookmark" ></a> 向使用者添加书签支持

书签是唯一标识表中的行的列。 通常它是键列，但并不总是;它是特定于提供程序。 本部分演示如何添加书签支持。 若要执行此操作，需要执行以下步骤在用户记录类：

- 实例化的书签。 这些是类型的对象[CBookmark](../../data/oledb/cbookmark-class.md)。

- 通过设置商请求书签列`DBPROP_IRowsetLocate`属性。

- 通过使用列映射到添加书签条目[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)宏。

前面的步骤为您提供书签支持和书签对象可处理的。 此代码示例演示一个书签，如下所示：

- 打开文件进行写入。

- 输出文件的行集数据行的行。

- 通过调用移到书签的行集游标[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)。

- 书签的行，将其追加到文件末尾的输出。

> [!NOTE]
> 如果您使用此使用者应用程序来测试`Provider`示例提供程序应用程序，在本部分中所述的书签支持。

### <a name="to-instantiate-the-bookmark"></a>若要实例化该书签

1. 访问器需要保留类型的对象[CBookmark](../../data/oledb/cbookmark-class.md)。 *NSize*参数指定书签缓冲区的大小以字节为单位 (通常为 32 位平台，4) 和 64 位平台为 8。 将以下声明添加到用户记录类中的列数据成员：

    ```cpp
    //////////////////////////////////////////////////////////////////////
    // Products.h
    class CProductsAccessor
    {
    public:
       CBookmark<4> m_bookmark;   // Add bookmark declaration
       LONG m_ProductID;
       ...
    ```

### <a name="to-request-a-bookmark-column-from-the-provider"></a>若要从提供程序请求书签列

1. 中的以下代码添加`GetRowsetProperties`中用户记录类的方法：

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>若要将书签项添加到列映射

1. 将以下条目添加到用户记录类中的列映射：

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>若要在主代码中使用书签

1. 在`MyCons.cpp`文件从以前创建的更改用于读取，如下所示的主要代码的控制台应用程序。 若要使用书签，主代码需要实例化它自己的书签对象 (`myBookmark`); 这是从访问器中的一个不同书签 (`m_bookmark`)。

    ```cpp
    ///////////////////////////////////////////////////////////////////////
    // MyCons.cpp : Defines the entry point for the console application.
    //

    #include "stdafx.h"
    #include "Products.h"
    #include <iostream>
    #include <fstream>
    using namespace std;

    int _tmain(int argc, _TCHAR* argv[])
    {
       HRESULT hr = CoInitialize(NULL);

       // Instantiate rowset
       CProducts rs;

       hr = rs.OpenAll();
       hr = rs.MoveFirst();

       // Cast CURRENCY m_UnitPrice to a long value
       LONGLONG lPrice = rs.m_UnitPrice.int64;

       // Open file output.txt for writing in overwrite mode
       ofstream outfile( "C:\\output.txt", ios::out );

       if (!outfile)      // Test for invalid file
          return -1;

       // Instantiate a bookmark object myBookmark for the main code
       CBookmark<4> myBookmark;
       int nCounter = 0;

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "initial row dump" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          nCounter++;
          if(nCounter == 5 )
             myBookmark = rs.m_bookmark;
          // Output the column information for each row:
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       // Move cursor to bookmark
       hr = rs.MoveToBookmark(myBookmark);

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "row dump starting from bookmarked row" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          // Output the column information for each row
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       rs.CloseAll();
       CoUninitialize();

       return 0;
    }
    ```

有关书签的详细信息，请参阅[使用书签](../../data/oledb/using-bookmarks.md)。 中显示了示例的书签[更新行集](../../data/oledb/updating-rowsets.md)。

## <a name="see-also"></a>请参阅

[使用向导创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
