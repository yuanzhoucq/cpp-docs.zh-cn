---
title: "如何：为 ADO.NET 封送 SAFEARRAY (C++/CLI) | Microsoft Docs"
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
  - "ADO.NET [C++], 封送处理 SAFEARRAY 类型"
  - "SAFEARRAY, 封送处理"
ms.assetid: 1034b9d7-ecf1-40f7-a9ee-53180e87a58c
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：为 ADO.NET 封送 SAFEARRAY (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

说明如何将本机 `SAFEARRAY` 添加到数据库，以及如何将托管数组从数据库封送到本机 `SAFEARRAY`。  
  
## 示例  
 在此示例中，创建了 DatabaseClass 类以和 ADO.NET <xref:System.Data.DataTable> 对象进行交互。  请注意，此类是本机 C\+\+ `class`（与 `ref class` 或 `value class` 相比较）。  这是必要的，因为我们要从本机代码使用此类，而在本机代码中无法使用托管类型。  此类将被编译为以 CLR 为目标，如类声明前面的 `#pragma managed` 指令所指示的一样。  有关此指令的更多信息，请参见 [managed、unmanaged](../preprocessor/managed-unmanaged.md)。  
  
 请注意 DatabaseClass 类的私有成员：`gcroot<DataTable ^> table`。  由于本机类型无法包含托管类型，`gcroot` 关键字是必要的。  有关 `gcroot` 的更多信息，请参见 [如何：使用本机类型声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
 此示例中的其余代码是本机 C\+\+ 代码，如 `main` 前面的 `#pragma unmanaged` 指令所指示的一样。  在此示例中，我们将要创建 DatabaseClass 的一个新实例并调用其方法，以创建一个表并在表中填充一些行。  请注意，正在将本机 `SAFEARRAY` 类型作为数据库列 ArrayIntsCol 的值传递。  在 DatabaseClass 内，已使用 <xref:System.Runtime.InteropServices?displayProperty=fullName> 命名空间的封送功能将这些 `SAFEARRAY` 类型封送到了托管对象。  具体地说，方法 <xref:System.Runtime.InteropServices.Marshal.Copy%2A> 用于将 `SAFEARRAY` 封送到托管整数数组，而方法 <xref:System.Runtime.InteropServices.Marshal.Copy%2A> 用于将托管整数数组封送到 `SAFEARRAY`。  
  
```  
// adonet_marshal_safearray.cpp  
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
  
    void AddRow(SAFEARRAY *arrayIntsColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        int len = arrayIntsColValue->rgsabound[0].cElements;  
        array<int> ^arr = gcnew array<int>(len);  
  
        int *pData;  
        SafeArrayAccessData(arrayIntsColValue, (void **)&pData);  
        Marshal::Copy(IntPtr(pData), arr, 0, len);  
        SafeArrayUnaccessData(arrayIntsColValue);  
  
        row["ArrayIntsCol"] = arr;  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ArrayIntsCol",  
            Type::GetType("System.Int32[]"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, SAFEARRAY **values,  
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
            // Marshal each column value from a managed array  
            // of Int32s to a SAFEARRAY of type VT_I4.  
            values[i] = SafeArrayCreateVector(VT_I4, 0, 10);  
            int *pData;  
            SafeArrayAccessData(values[i], (void **)&pData);  
            Marshal::Copy((array<int> ^)rows[i][columnStr], 0,  
                IntPtr(pData), 10);  
            SafeArrayUnaccessData(values[i]);  
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
  
    // Create a standard array.  
    int originalArray[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
    // Create a SAFEARRAY.  
    SAFEARRAY *psa;  
    psa = SafeArrayCreateVector(VT_I4, 0, 10);  
  
    // Copy the data from the original array to the SAFEARRAY.  
    int *pData;  
    HRESULT hr = SafeArrayAccessData(psa, (void **)&pData);  
    memcpy(pData, &originalArray, 40);  
    SafeArrayUnaccessData(psa);  
    db->AddRow(psa);  
  
    // Now retrieve the rows and display their contents.  
    SAFEARRAY *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ArrayIntsCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        int *pData;  
        SafeArrayAccessData(values[i], (void **)&pData);  
        for (int j = 0; j < 10; j++)  
        {  
            cout << pData[j] << " ";  
        }  
        cout << endl;  
        SafeArrayUnaccessData(values[i]);  
  
        // Deallocate the memory allocated using  
        // SafeArrayCreateVector.  
        SafeArrayDestroy(values[i]);  
    }  
  
    SafeArrayDestroy(psa);  
    delete db;  
  
    return 0;  
}  
```  
  
  **0 1 2 3 4 5 6 7 8 9**   
## 编译代码  
  
-   若要从命令行编译代码，请将代码示例保存在名为 adonet\_marshal\_safearray.cpp 的文件中，并输入下面的语句：  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp  
    ```  
  
## .NET Framework 安全性  
 有关涉及 ADO.NET 安全问题的信息，请参见 [保证 ADO.NET 应用程序的安全](../Topic/Securing%20ADO.NET%20Applications.md)。  
  
## 请参阅  
 <xref:System.Runtime.InteropServices>   
 [数据访问](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](../Topic/ADO.NET.md)   
 [Interoperability](http://msdn.microsoft.com/zh-cn/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)