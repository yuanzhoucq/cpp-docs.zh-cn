---
title: 使用 ADO.NET 的数据访问 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
- BSTRs, strings
- ADO.NET [C++], marshaling BSTR strings
- strings [C++], marshaling BSTR strings
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
ms.openlocfilehash: 896cad4d3a679cd1832b073f4b1f355a70a608d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638472"
---
# <a name="data-access-using-adonet-ccli"></a>使用 ADO.NET 的数据访问 (C++/CLI)

ADO.NET 是用于数据访问的.NET Framework API，并提供电源和易于使用的以前的数据访问解决方案。 本部分介绍的一些问题涉及 ADO.NET 独有 Visual c + + 用户，例如封送处理本机类型。

ADO.NET 在公共语言运行时 (CLR) 下运行。 因此，任何使用 ADO.NET 进行交互的应用程序还必须针对 CLR。 但是，这并不意味着本机应用程序不能使用 ADO.NET。 这些示例将演示如何使用 ADO.NET 数据库从本机代码进行交互。

## <a name="marshal_ansi"></a> ADO.NET 的封送 ANSI 字符串

演示如何添加本机字符串 (`char *`) 到数据库，以及如何封送<xref:System.String?displayProperty=fullName>从数据库到本机的字符串。

### <a name="example"></a>示例

在此示例中，创建的类 DatabaseClass 是与 ADO.NET 交互<xref:System.Data.DataTable>对象。 请注意，此类是本机 c + + `class` (相比`ref class`或`value class`)。 这是必需的因为我们想要使用此类从本机代码，并且不能在本机代码中使用托管的类型。 此类将编译为面向 CLR，是由`#pragma managed`类声明前面的指令。 此指令的详细信息，请参阅[managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管的类型`gcroot`关键字是必要。 有关详细信息`gcroot`，请参阅[如何： 在本机类型中声明处理](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机 c + + 代码中，是由`#pragma unmanaged`指令前面`main`。 在此示例中，我们已创建 DatabaseClass 的新实例并调用其方法来创建一个表并填充表中的某些行。 请注意，作为 StringCol 的数据库列的值传递本机 c + + 字符串。 在 DatabaseClass，这些字符串封送到使用中的封送处理功能的托管字符串<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>用于封送`char *`到<xref:System.String>，和方法<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>用于封送<xref:System.String>到`char *`。

> [!NOTE]
>  分配的内存<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>必须通过调用释放<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>或`GlobalFree`。

```cpp
// adonet_marshal_string_native.cpp
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

    void AddRow(char *stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringAnsi(
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

    int GetValuesForColumn(char *dataColumn, char **values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringAnsi(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a char *.
            values[i] = (char *)Marshal::StringToHGlobalAnsi(
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
    db->AddRow("This is string 1.");
    db->AddRow("This is string 2.");

    // Now retrieve the rows and display their contents.
    char *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        "StringCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        cout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToHGlobalAnsi.
        GlobalFree(values[i]);
    }

    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>编译代码

- 通过命令行编译代码，将代码示例保存在一个名为 adonet_marshal_string_native.cpp 文件并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal_bstr"></a> ADO.NET 的封送 BSTR 字符串

演示如何添加 COM 字符串 (`BSTR`) 到数据库，以及如何封送<xref:System.String?displayProperty=fullName>从数据库到`BSTR`。

### <a name="example"></a>示例

在此示例中，创建的类 DatabaseClass 是与 ADO.NET 交互<xref:System.Data.DataTable>对象。 请注意，此类是本机 c + + `class` (相比`ref class`或`value class`)。 这是必需的因为我们想要使用此类从本机代码，并且不能在本机代码中使用托管的类型。 此类将编译为面向 CLR，是由`#pragma managed`类声明前面的指令。 此指令的详细信息，请参阅[managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管的类型`gcroot`关键字是必要。 有关详细信息`gcroot`，请参阅[如何： 在本机类型中声明处理](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机 c + + 代码中，是由`#pragma unmanaged`指令前面`main`。 在此示例中，我们已创建 DatabaseClass 的新实例并调用其方法来创建一个表并填充表中的某些行。 请注意，COM 字符串传递作为 StringCol 的数据库列的值。 在 DatabaseClass，这些字符串封送到使用中的封送处理功能的托管字符串<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>用于封送`BSTR`到<xref:System.String>，和方法<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>用于封送<xref:System.String>到`BSTR`。

> [!NOTE]
>  分配的内存<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>必须通过调用释放<xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A>或`SysFreeString`。

``` cpp
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

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>编译代码

- 通过命令行编译代码，将代码示例保存在一个名为 adonet_marshal_string_native.cpp 文件并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal_unicode"></a> ADO.NET 的封送 Unicode 字符串

演示如何添加本机 Unicode 字符串 (`wchar_t *`) 到数据库，以及如何封送<xref:System.String?displayProperty=fullName>从数据库到本机的 Unicode 字符串。

### <a name="example"></a>示例

在此示例中，创建的类 DatabaseClass 是与 ADO.NET 交互<xref:System.Data.DataTable>对象。 请注意，此类是本机 c + + `class` (相比`ref class`或`value class`)。 这是必需的因为我们想要使用此类从本机代码，并且不能在本机代码中使用托管的类型。 此类将编译为面向 CLR，是由`#pragma managed`类声明前面的指令。 此指令的详细信息，请参阅[managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管的类型`gcroot`关键字是必要。 有关详细信息`gcroot`，请参阅[如何： 在本机类型中声明处理](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机 c + + 代码中，是由`#pragma unmanaged`指令前面`main`。 在此示例中，我们已创建 DatabaseClass 的新实例并调用其方法来创建一个表并填充表中的某些行。 请注意，Unicode c + + 字符串传递作为 StringCol 的数据库列的值。 在 DatabaseClass，这些字符串封送到使用中的封送处理功能的托管字符串<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>用于封送`wchar_t *`到<xref:System.String>，和方法<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>用于封送<xref:System.String>到`wchar_t *`。

> [!NOTE]
>  分配的内存<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>必须通过调用释放<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>或`GlobalFree`。

```cpp
// adonet_marshal_string_wide.cpp
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

    void AddRow(wchar_t *stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringUni(
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

    int GetValuesForColumn(wchar_t *dataColumn, wchar_t **values,
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
            // Marshal each column value from a managed string
            // to a wchar_t *.
            values[i] = (wchar_t *)Marshal::StringToHGlobalUni(
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
    db->AddRow(L"This is string 1.");
    db->AddRow(L"This is string 2.");

    // Now retrieve the rows and display their contents.
    wchar_t *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        L"StringCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        wcout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToHGlobalUni.
        GlobalFree(values[i]);
    }

    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>编译代码

- 通过命令行编译代码，将代码示例保存在一个名为 adonet_marshal_string_wide.cpp 文件并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal_variant"></a> 为 ADO.NET 封送变体

演示如何将添加一个本机`VARIANT`到数据库，以及如何封送<xref:System.Object?displayProperty=fullName>从数据库到本机`VARIANT`。

### <a name="example"></a>示例

在此示例中，创建的类 DatabaseClass 是与 ADO.NET 交互<xref:System.Data.DataTable>对象。 请注意，此类是本机 c + + `class` (相比`ref class`或`value class`)。 这是必需的因为我们想要使用此类从本机代码，并且不能在本机代码中使用托管的类型。 此类将编译为面向 CLR，是由`#pragma managed`类声明前面的指令。 此指令的详细信息，请参阅[managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管的类型`gcroot`关键字是必要。 有关详细信息`gcroot`，请参阅[如何： 在本机类型中声明处理](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机 c + + 代码中，是由`#pragma unmanaged`指令前面`main`。 在此示例中，我们已创建 DatabaseClass 的新实例并调用其方法来创建一个表并填充表中的某些行。 请注意该本机`VARIANT`ObjectCol 的数据库列的值作为传递类型。 内部 DatabaseClass，这些`VARIANT`类型封送到托管对象使用的封送处理功能<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A>用于封送`VARIANT`到<xref:System.Object>，和方法<xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A>用于封送<xref:System.Object>到`VARIANT`。

```cpp
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

```Output
ObjectCol: This is a BSTR in a VARIANT.
ObjectCol: 42
```

### <a name="compiling-the-code"></a>编译代码

- 通过命令行编译代码，将代码示例保存在一个名为 adonet_marshal_variant.cpp 文件并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal_safearray"></a> 为 ADO.NET 封送 SAFEARRAY

演示如何将添加一个本机`SAFEARRAY`到数据库，以及如何封送托管的数组从数据库到本机`SAFEARRAY`。

### <a name="example"></a>示例

在此示例中，创建的类 DatabaseClass 是与 ADO.NET 交互<xref:System.Data.DataTable>对象。 请注意，此类是本机 c + + `class` (相比`ref class`或`value class`)。 这是必需的因为我们想要使用此类从本机代码，并且不能在本机代码中使用托管的类型。 此类将编译为面向 CLR，是由`#pragma managed`类声明前面的指令。 此指令的详细信息，请参阅[managed、 unmanaged](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管的类型`gcroot`关键字是必要。 有关详细信息`gcroot`，请参阅[如何： 在本机类型中声明处理](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机 c + + 代码中，是由`#pragma unmanaged`指令前面`main`。 在此示例中，我们已创建 DatabaseClass 的新实例并调用其方法来创建一个表并填充表中的某些行。 请注意该本机`SAFEARRAY`ArrayIntsCol 的数据库列的值作为传递类型。 内部 DatabaseClass，这些`SAFEARRAY`类型封送到托管对象使用的封送处理功能<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.Copy%2A>用于封送`SAFEARRAY`到托管数组的整数和方法<xref:System.Runtime.InteropServices.Marshal.Copy%2A>用于封送托管的数组的整数到`SAFEARRAY`。

```cpp
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

```Output
0 1 2 3 4 5 6 7 8 9
```

### <a name="compiling-the-code"></a>编译代码

- 通过命令行编译代码，将代码示例保存在一个名为 adonet_marshal_safearray.cpp 文件并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>.NET Framework 安全性

有关涉及 ADO.NET 的安全问题的信息，请参阅[保护 ADO.NET 应用程序](/dotnet/framework/data/adonet/securing-ado-net-applications)。

## <a name="related-sections"></a>相关章节

|节|描述|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|概述 ADO.NET 中，一组公开数据访问服务向.NET 程序员的类。|

## <a name="see-also"></a>请参阅

[使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[互操作性](/dotnet/framework/interop/index)
