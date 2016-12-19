---
title: "实现简单使用者 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "客户端, 创建"
  - "OLE DB 使用者, 实现"
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 实现简单使用者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的主题显示如何编辑由“MFC 应用程序向导”和“ATL OLE DB 使用者向导”所创建的文件以创建简单的使用者。  此示例包括以下部分：  
  
-   “用使用者检索数据”说明如何实现从数据库表中逐行读取所有数据的使用者中的代码。  
  
-   “将书签支持添加到使用者”说明如何将书签支持添加到使用者。  
  
-   “将 XML 支持添加到使用者”说明如何修改使用者代码以将检索到的行集合数据作为 XML 数据输出。  
  
> [!NOTE]
>  可以使用本节中所描述的使用者应用程序来测试 MyProv 和 Provider 提供程序示例。  
  
> [!NOTE]
>  若要生成使用者应用程序来测试 MyProv（[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)中所描述的同一提供程序），则必须包含书签支持（如“将书签支持添加到使用者”中所描述）。  
  
> [!NOTE]
>  若要生成使用者应用程序来测试 Provider，则忽略书签支持（如“将书签支持添加到使用者”中所描述）并且跳到“将 XML 支持添加到使用者”。  
  
## 用使用者检索数据  
  
#### 修改控制台应用程序以使用 OLE DB 使用者  
  
1.  在 MyCons.cpp 中，通过插入如下所示的粗体文本来更改主代码：  
  
    ```  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
    #include "stdafx.h"  
    #include "Products.h"  
    ...  
    int main(int argc, char* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);        // Instantiate rowset    CProducts rs;        hr = rs.OpenAll();    ATLASSERT( SUCCEEDED( hr ) );    hr = rs.MoveFirst();        // Iterate through the rowset    while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )    {       // Print out the column information for each row       printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",              rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );       hr = rs.MoveNext();    }        rs.Close();    rs.ReleaseCommand();        CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## 将书签支持添加到使用者  
 书签是一个唯一标识表中的行的列。  它通常是键列，但不总是这样；它是提供程序特定的。  本节说明如何添加书签支持。  若要添加书签支持，需要在用户记录类中执行下面的操作：  
  
-   实例化书签。  它们是 [CBookmark](../../data/oledb/cbookmark-class.md) 类型的对象。  
  
-   通过设置 **DBPROP\_IRowsetLocate** 属性从提供程序中请求书签列。  
  
-   使用 [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md) 宏向列映射添加一个书签项。  
  
 上面的步骤提供书签支持和要使用的书签对象。  此代码示例将演示书签，如下所示：  
  
-   打开要编写的文件。  
  
-   将行集合数据逐行输出到文件。  
  
-   通过调用 [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md) 将行集合游标移动到书签。  
  
-   输出由书签标记的行，将其追加到文件的结尾。  
  
> [!NOTE]
>  如果使用此使用者应用程序来测试 Provider 提供程序应用程序示例，则忽略本节中所描述的书签支持。  
  
#### 实例化书签  
  
1.  访问器需要包含一个 [CBookmark](../../data/oledb/cbookmark-class.md) 类型的对象。  `nSize` 参数以字节为单位指定书签缓冲区的大小（通常，对于 32 位平台为 4，对于 64 位平台为 8）。  将下面的声明添加到用户记录类中的列数据成员：  
  
    ```  
    //////////////////////////////////////////////////////////////////////  
    // Products.h  
    class CProductsAccessor  
    {  
    public:  
       CBookmark<4> m_bookmark;   // Add bookmark declaration  
       LONG m_ProductID;  
       ...  
    ```  
  
#### 从提供程序中请求书签列  
  
1.  在用户记录类的 `GetRowsetProperties` 方法中添加下面的代码：  
  
    ```  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks    pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### 将书签项添加到列映射  
  
1.  将下面的项添加到用户记录类中的列映射：  
  
    ```  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### 在主代码中使用书签  
  
1.  在以前创建的控制台应用程序的 MyCons.cpp 文件中，将主代码更改为如下所示的样子。  若要使用书签，则主代码需要实例化自己的书签对象 \(`myBookmark`\)；此书签不同于访问器中的书签 \(`m_bookmark`\)。  
  
    ```  
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
       while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
       {  
          nCounter++;  
          if( nCounter == 5 )  
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
       while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
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
  
 有关书签的更多信息，请参见[使用书签](../../data/oledb/using-bookmarks.md)。  在[更新行集合](../../data/oledb/updating-rowsets.md)中也显示书签的示例。  
  
## 将 XML 支持添加到使用者  
 如[访问 XML 数据](../../data/oledb/accessing-xml-data.md)中所讨论的，有两种从数据源中检索 XML 数据的方法：使用 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 或使用 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。  此示例使用 `CStreamRowset`，它更有效，但是要求在执行此应用程序示例的计算机上运行 SQL Server 2000。  
  
#### 修改命令类以从 CStreamRowset 继承  
  
1.  在以前创建的使用者应用程序中，更改 `CCommand` 声明以将 `CStreamRowset` 指定为行集合类，如下所示：  
  
    ```  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### 修改主代码以检索并输出 XML 数据  
  
1.  在以前创建的控制台应用程序的 MyCons.cpp 文件中，将主代码更改为如下所示的样子：  
  
    ```  
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
  
## 请参阅  
 [使用向导创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)