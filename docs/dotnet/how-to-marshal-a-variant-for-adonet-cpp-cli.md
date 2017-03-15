---
title: "如何：为 ADO.NET 封送 VARIANT (C++/CLI) | Microsoft Docs"
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
  - "ADO.NET [C++], 封送处理 VARIANT 类型"
  - "VARIANT"
  - "VARIANT, 封送处理"
ms.assetid: 67a180a7-5691-48ab-8d85-7f75a68dde91
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：为 ADO.NET 封送 VARIANT (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

说明如何将本机 `VARIANT` 添加到数据库，以及如何将 <xref:System.Object?displayProperty=fullName> 从数据库封送到本机 `VARIANT`。  
  
## 示例  
 在此示例中，创建了 DatabaseClass 类以和 ADO.NET <xref:System.Data.DataTable> 对象进行交互。  请注意，此类是本机 C\+\+ `class`（与 `ref class` 或 `value class` 相比较）。  这是必要的，因为我们要从本机代码使用此类，而在本机代码中无法使用托管类型。  此类将被编译为以 CLR 为目标，如类声明前面的 `#pragma managed` 指令所指示的一样。  有关此指令的更多信息，请参见 [managed、unmanaged](../preprocessor/managed-unmanaged.md)。  
  
 请注意 DatabaseClass 类的私有成员：`gcroot<DataTable ^> table`。  由于本机类型无法包含托管类型，`gcroot` 关键字是必要的。  有关 `gcroot` 的更多信息，请参见 [如何：使用本机类型声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
 此示例中的其余代码是本机 C\+\+ 代码，如 `main` 前面的 `#pragma unmanaged` 指令所指示的一样。  在此示例中，我们将要创建 DatabaseClass 的一个新实例并调用其方法，以创建一个表并在表中填充一些行。  请注意，正在将本机 `VARIANT` 类型作为数据库列 ObjectCol 进行传递。  在 DatabaseClass 内，已使用 <xref:System.Runtime.InteropServices?displayProperty=fullName> 命名空间中的封送功能将这些 `VARIANT` 类型封送到了托管对象。  具体地说，方法 <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> 用于将 `VARIANT` 封送到 <xref:System.Object>，而方法 <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> 用于将 <xref:System.Object> 封送到 `VARIANT`。  
  
```  
// adonet_marshal_variant.cpp  
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
  
    void AddRow(VARIANT *objectColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["ObjectCol"] = Marshal::GetObjectForNativeVariant(  
            IntPtr(objectColValue));  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ObjectCol",  
            Type::GetType("System.Object"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, VARIANT *values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringUni(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed object  
            // to a VARIANT.  
            Marshal::GetNativeVariantForObject(  
                rows[i][columnStr], IntPtr(&values[i]));  
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
  
    BSTR bstr1 = SysAllocString(L"This is a BSTR in a VARIANT.");  
    VARIANT v1;  
    v1.vt = VT_BSTR;  
    v1.bstrVal = bstr1;  
    db->AddRow(&v1);  
  
    int i = 42;  
    VARIANT v2;  
    v2.vt = VT_I4;  
    v2.lVal = i;  
    db->AddRow(&v2);  
  
    // Now retrieve the rows and display their contents.  
    VARIANT values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ObjectCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        switch (values[i].vt)  
        {  
            case VT_BSTR:  
                wcout << L"ObjectCol: " << values[i].bstrVal << endl;  
                break;  
            case VT_I4:  
                cout << "ObjectCol: " << values[i].lVal << endl;  
                break;  
            default:  
                break;  
        }  
  
    }  
  
    SysFreeString(bstr1);  
    delete db;  
  
    return 0;  
}  
```  
  
  **ObjectCol: This is a BSTR in a VARIANT.**  
**ObjectCol: 42**   
## 编译代码  
  
-   若要从命令行编译代码，请将该代码示例保存到名为 adonet\_marshal\_variant.cpp 的文件中，并输入以下语句：  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  
  
## .NET Framework 安全性  
 有关涉及 ADO.NET 安全问题的信息，请参见 [保证 ADO.NET 应用程序的安全](../Topic/Securing%20ADO.NET%20Applications.md)。  
  
## 请参阅  
 <xref:System.Runtime.InteropServices>   
 [数据访问](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](../Topic/ADO.NET.md)   
 [Interoperability](http://msdn.microsoft.com/zh-cn/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)