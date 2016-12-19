---
title: "如何：为 ADO.NET 封送 BSTR 字符串 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ADO.NET [C++], 封送 BSTR 字符串"
  - "BSTR, 字符串"
  - "字符串 [C++], 封送 BSTR 字符串"
ms.assetid: 5daf4d9e-6ae8-4604-908f-855e37c8d636
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：为 ADO.NET 封送 BSTR 字符串 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

说明如何将 COM 字符串 \(`BSTR`\) 添加到数据库，以及如何将 <xref:System.String?displayProperty=fullName> 从数据库封送到 `BSTR`。  
  
## 示例  
 在此示例中，创建了 DatabaseClass 类以和 ADO.NET <xref:System.Data.DataTable> 对象进行交互。  请注意，此类是本机 C\+\+ `class`（与 `ref class` 或 `value class` 相比较）。  这是必要的，因为我们要从本机代码使用此类，而在本机代码中无法使用托管类型。  此类将被编译为以 CLR 为目标，如类声明前面的 `#pragma managed` 指令所指示的一样。  有关此指令的更多信息，请参见 [managed、unmanaged](../preprocessor/managed-unmanaged.md)。  
  
 请注意 DatabaseClass 类的私有成员：`gcroot<DataTable ^> table`。  由于本机类型无法包含托管类型，`gcroot` 关键字是必要的。  有关 `gcroot` 的更多信息，请参见 [如何：使用本机类型声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
 此示例中的其余代码是本机 C\+\+ 代码，如 `main` 前面的 `#pragma unmanaged` 指令所指示的一样。  在此示例中，我们将要创建 DatabaseClass 的一个新实例并调用其方法，以创建一个表并在表中填充一些行。  请注意，正在将 COM 字符串作为数据库列 StringCol 的值进行传递。  在 DatabaseClass 内，已使用 <xref:System.Runtime.InteropServices?displayProperty=fullName> 命名空间的封送功能将这些字符串封送到了托管字符串。  具体地说，方法 <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> 用于将 `BSTR` 封送到 <xref:System.String>，而方法 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 用于将 <xref:System.String> 封送到 `BSTR`。  
  
> [!NOTE]
>  由 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 分配的内存必须通过调用 <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> 或 `SysFreeString` 释放。  
  
```  
// adonet_marshal_string_bstr.cpp  
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll  
#include <comdef.h>  
#include <gcroot.h>  
#include <iostream>  
using namespace std;  
  
#using <System.Data.dll>  
using namespace System;  
using namespace System::Data;  
using namespace System::Runtime::InteropServices;  
  
#define MAXCOLS 100  
  
#pragma managed  
class DatabaseClass  
{  
public:  
    DatabaseClass() : table(nullptr) { }  
  
    void AddRow(BSTR stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringBSTR(  
            (IntPtr)stringColValue);  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("StringCol",  
            Type::GetType("System.String"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(BSTR dataColumn, BSTR *values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringBSTR(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a BSTR.  
            values[i] = (BSTR)Marshal::StringToBSTR(  
                (String ^)rows[i][columnStr]).ToPointer();  
        }  
  
        return len;  
    }  
  
private:  
    // Using gcroot, you can use a managed type in  
    // a native class.  
    gcroot<DataTable ^> table;  
};  
  
#pragma unmanaged  
int main()  
{  
    // Create a table and add a few rows to it.  
    DatabaseClass *db = new DatabaseClass();  
    db->CreateAndPopulateTable();  
  
    BSTR str1 = SysAllocString(L"This is string 1.");  
    db->AddRow(str1);  
  
    BSTR str2 = SysAllocString(L"This is string 2.");  
    db->AddRow(str2);  
  
    // Now retrieve the rows and display their contents.  
    BSTR values[MAXCOLS];  
    BSTR str3 = SysAllocString(L"StringCol");  
    int len = db->GetValuesForColumn(  
        str3, values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        wcout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToBSTR.  
        SysFreeString(values[i]);  
    }  
  
    SysFreeString(str1);  
    SysFreeString(str2);  
    SysFreeString(str3);  
    delete db;  
  
    return 0;  
}  
```  
  
  **StringCol: This is string 1.**  
**StringCol: This is string 2.**   
## 编译代码  
  
-   若要从命令行编译代码，请将代码示例保存到名为 adonet\_marshal\_string\_native.cpp 的文件中，并输入以下语句：  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp  
    ```  
  
## .NET Framework 安全性  
 有关涉及 ADO.NET 安全问题的信息，请参见 [保证 ADO.NET 应用程序的安全](../Topic/Securing%20ADO.NET%20Applications.md)。  
  
## 请参阅  
 <xref:System.Runtime.InteropServices>   
 [数据访问](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](../Topic/ADO.NET.md)   
 [Interoperability](http://msdn.microsoft.com/zh-cn/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)