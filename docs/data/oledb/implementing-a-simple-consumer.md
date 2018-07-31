---
title: 实现简单使用者 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- clients, creating
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7be7709baadff35c10cec861b4a0bca94c8cbe5f
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337159"
---
# <a name="implementing-a-simple-consumer"></a>实现简单使用者
以下主题说明如何编辑由 MFC 应用程序向导和 ATL OLE DB 使用者向导创建简单使用者创建的文件。 此示例包含以下部分：  
  
-   "检索数据使用者与"显示了如何在从数据库表中读取所有数据，表中的使用者中实现代码。  
  
-   "添加到使用者的书签支持"显示了如何将书签支持添加到使用者。  
  
-   "将 XML 支持添加到使用者"显示了如何修改输出以 XML 数据形式检索到的行集数据的使用者代码。  
  
> [!NOTE]
>  在本部分中描述的使用者应用程序可用于测试的 MyProv 和提供程序的示例提供程序。  
  
> [!NOTE]
>  若要生成使用者应用程序来测试 MyProv (相同的提供程序中所述[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md))，在"添加书签支持添加到使用者。"中所述，必须包含书签支持  
  
> [!NOTE]
>  若要生成使用者应用程序测试提供程序，在"添加书签支持向使用者"中所述的书签支持忽略并跳到"添加到使用者的 XML 支持"。  
  
## <a name="retrieving-data-with-the-consumer"></a>使用者检索数据  
  
#### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>若要修改控制台应用程序使用 OLE DB 使用者  
  
1.  MyCons.cpp 中的方法是插入的粗体文本，如下所示更改主代码：  
  
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
  
## <a name="adding-bookmark-support-to-the-consumer"></a>向使用者添加书签支持  
 书签是唯一标识表中的行的列。 通常它是键列，但并不总是;它是特定于提供程序。 本部分演示如何添加书签支持。 若要执行此操作，需要执行以下操作在用户记录类中：  
  
-   实例化的书签。 这些是类型的对象[CBookmark](../../data/oledb/cbookmark-class.md)。  
  
-   通过设置商请求书签列`DBPROP_IRowsetLocate`属性。  
  
-   通过使用列映射到添加书签条目[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)宏。  
  
 前面的步骤为您提供书签支持和书签对象可处理的。 此代码示例演示一个书签，如下所示：  
  
-   打开文件进行写入。  
  
-   输出文件的行集数据行的行。  
  
-   通过调用移到书签的行集游标[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)。  
  
-   书签的行，将其追加到文件末尾的输出。  
  
> [!NOTE]
>  如果使用此使用者应用程序来测试提供程序示例提供程序应用程序，将在本部分中所述的书签支持。  
  
#### <a name="to-instantiate-the-bookmark"></a>若要实例化该书签  
  
1.  访问器需要包含类型的对象[CBookmark](../../data/oledb/cbookmark-class.md)。 *NSize*参数指定书签缓冲区的大小以字节为单位 (通常为 32 位平台，4) 和 64 位平台为 8。 将以下声明添加到用户记录类中的列数据成员：  
  
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
  
#### <a name="to-request-a-bookmark-column-from-the-provider"></a>若要从提供程序请求书签列  
  
1.  中的以下代码添加`GetRowsetProperties`中用户记录类的方法：  
  
    ```cpp  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>若要将书签项添加到列映射  
  
1.  将以下条目添加到用户记录类中的列映射：  
  
    ```cpp  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### <a name="to-use-a-bookmark-in-your-main-code"></a>若要在主代码中使用书签  
  
1.  在 MyCons.cpp 文件从以前创建的控制台应用程序中，更改主代码读取，如下所示。 若要使用书签，主代码需要实例化它自己的书签对象 (`myBookmark`); 这是从访问器中的一个不同书签 (`m_bookmark`)。  
  
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
             myBookmark = rs.bookmark;  
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
  
## <a name="adding-xml-support-to-the-consumer"></a>向使用者添加 XML 支持  
 如中所述[访问 XML 数据](../../data/oledb/accessing-xml-data.md)，有两种方法来从数据源中检索 XML 数据： 使用[CStreamRowset](../../data/oledb/cstreamrowset-class.md)也可以使用[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。 此示例使用`CStreamRowset`，这是更有效，但要求你具有在其执行此示例应用程序在计算机上运行的 SQL Server 2000。  
  
#### <a name="to-modify-the-command-class-to-inherit-from-cstreamrowset"></a>若要修改命令类，以从 CStreamRowset 继承  
  
1.  在以前创建的使用者的应用程序的情况下，更改你`CCommand`声明，以指定`CStreamRowset`与行集类，如下所示：  
  
    ```cpp  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### <a name="to-modify-the-main-code-to-retrieve-and-output-the-xml-data"></a>若要修改主要代码，以检索和输出的 XML 数据  
  
1.  在 MyCons.cpp 文件从以前创建的控制台应用程序中，更改主代码读取，如下所示：  
  
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
  
       // Add variable declarations for the Read method to handle sequential stream data  
       CHAR buffer[1001];  // Pointer to buffer into which data stream is read  
       ULONG cbRead;       // Actual number of bytes read from the data stream  
  
       hr = rs.OpenAll();  
  
       // Open file output.txt for writing in overwrite mode  
       ofstream outfile( "C:\\output.txt", ios::out );  
  
       if (!outfile)      // Test for invalid file  
          return -1;  
  
       // The following loop reads 1000 bytes of the data stream at a time   
       // until it reaches the end of the data stream  
       for (;;)  
       {  
          // Read sequential stream data into buffer  
          HRESULT hr = rs.m_spStream->Read(buffer, 1000, &cbRead);  
          if (FAILED (hr))  
             break;  
          // Output buffer to file  
          buffer[cbRead] = 0;  
          outfile << buffer;  
          // Test for end of data stream  
          if (cbRead < 1000)  
             break;  
       }  
  
       rs.CloseAll();  
       CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## <a name="see-also"></a>请参阅  
 [使用向导创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)