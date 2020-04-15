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
ms.openlocfilehash: 35633449c4c01f5c103dcd54b81c0d6aa7c08cdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364411"
---
# <a name="data-access-using-adonet-ccli"></a>使用 ADO.NET 的数据访问 (C++/CLI)

ADO.NET是用于数据访问的 .NET 框架 API，提供前所未有的数据访问解决方案所无法比拟的电源和易用性。 本节介绍一些涉及 Visual C++ 用户独有的ADO.NET的问题，例如封送本机类型。

ADO.NET在通用语言运行时 （CLR） 下运行。 因此，任何与ADO.NET交互的应用程序也必须针对 CLR。 但是，这并不意味着本机应用程序不能使用ADO.NET。 这些示例将演示如何与来自本机代码的ADO.NET数据库进行交互。

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>为ADO.NET的封送 ANSI 字符串

演示如何向数据库添加本机字符串 （`char *`） 以及如何将 从<xref:System.String?displayProperty=fullName>数据库封送到本机字符串。

### <a name="example"></a>示例

在此示例中，创建类 DatabaseClass 是为了与ADO.NET<xref:System.Data.DataTable>对象进行交互。 请注意，此类是本机C++（`class`与 或`ref class``value class`相比）。 这是必需的，因为我们希望从本机代码使用此类，并且不能在本机代码中使用托管类型。 此类将编译为针对 CLR，如类声明前面的`#pragma managed`指令所示。 有关此指令的详细信息，请参阅[托管、非托管](../preprocessor/managed-unmanaged.md)。

请注意数据库类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管类型，`gcroot`因此关键字是必需的。 有关 的详细信息`gcroot`，请参阅[：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机C++代码，如 前面的`#pragma unmanaged``main`指令所示。 在此示例中，我们正在创建一个新的 DatabaseClass 实例，并调用其方法来创建表并填充表中的某些行。 请注意，本机C++字符串作为数据库列 StringCol 的值传递。 在 DatabaseClass 中，这些字符串使用<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间中的封送功能将封送到托管字符串。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>用于将 a`char *`封送<xref:System.String>到 ，<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>并且该方法用于将<xref:System.String>a`char *`封送到 。

> [!NOTE]
> 分配的<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>内存必须通过调用 或<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>`GlobalFree`进行分配。

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

- 要从命令行编译代码，请在名为 adonet_marshal_string_native.cpp 的文件中保存代码示例，并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>ADO.NET的 BSTR 字符串

演示如何向数据库添加 COM 字符串`BSTR`（ ， 以及如何将 从<xref:System.String?displayProperty=fullName>数据库封送 到`BSTR`。

### <a name="example"></a>示例

在此示例中，创建类 DatabaseClass 是为了与ADO.NET<xref:System.Data.DataTable>对象进行交互。 请注意，此类是本机C++（`class`与 或`ref class``value class`相比）。 这是必需的，因为我们希望从本机代码使用此类，并且不能在本机代码中使用托管类型。 此类将编译为针对 CLR，如类声明前面的`#pragma managed`指令所示。 有关此指令的详细信息，请参阅[托管、非托管](../preprocessor/managed-unmanaged.md)。

请注意数据库类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管类型，`gcroot`因此关键字是必需的。 有关 的详细信息`gcroot`，请参阅[：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机C++代码，如 前面的`#pragma unmanaged``main`指令所示。 在此示例中，我们正在创建一个新的 DatabaseClass 实例，并调用其方法来创建表并填充表中的某些行。 请注意，COM 字符串作为数据库列 StringCol 的值传递。 在 DatabaseClass 中，这些字符串使用<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间中的封送功能将封送到托管字符串。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>用于将 a`BSTR`封送<xref:System.String>到 ，<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>并且该方法用于将<xref:System.String>a`BSTR`封送到 。

> [!NOTE]
> 分配的<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>内存必须通过调用 或<xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A>`SysFreeString`进行分配。

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

- 要从命令行编译代码，请在名为 adonet_marshal_string_native.cpp 的文件中保存代码示例，并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>为ADO.NET而封送 Unicode 字符串

演示如何将本机 Unicode 字符串 （`wchar_t *`） 添加到数据库以及如何将 从<xref:System.String?displayProperty=fullName>数据库封送到本机 Unicode 字符串。

### <a name="example"></a>示例

在此示例中，创建类 DatabaseClass 是为了与ADO.NET<xref:System.Data.DataTable>对象进行交互。 请注意，此类是本机C++（`class`与 或`ref class``value class`相比）。 这是必需的，因为我们希望从本机代码使用此类，并且不能在本机代码中使用托管类型。 此类将编译为针对 CLR，如类声明前面的`#pragma managed`指令所示。 有关此指令的详细信息，请参阅[托管、非托管](../preprocessor/managed-unmanaged.md)。

请注意数据库类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管类型，`gcroot`因此关键字是必需的。 有关 的详细信息`gcroot`，请参阅[：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机C++代码，如 前面的`#pragma unmanaged``main`指令所示。 在此示例中，我们正在创建一个新的 DatabaseClass 实例，并调用其方法来创建表并填充表中的某些行。 请注意，Unicode C++字符串作为数据库列 StringCol 的值传递。 在 DatabaseClass 中，这些字符串使用<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间中的封送功能将封送到托管字符串。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>用于将 a`wchar_t *`封送<xref:System.String>到 ，<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>并且该方法用于将<xref:System.String>a`wchar_t *`封送到 。

> [!NOTE]
> 分配的<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>内存必须通过调用 或<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>`GlobalFree`进行分配。

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

- 要从命令行编译代码，请在名为 adonet_marshal_string_wide.cpp 的文件中保存代码示例，并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>为ADO.NET编送一个 VARIANT

演示如何将本机`VARIANT`添加到数据库以及如何将 从<xref:System.Object?displayProperty=fullName>数据库封送到本机`VARIANT`。

### <a name="example"></a>示例

在此示例中，创建类 DatabaseClass 是为了与ADO.NET<xref:System.Data.DataTable>对象进行交互。 请注意，此类是本机C++（`class`与 或`ref class``value class`相比）。 这是必需的，因为我们希望从本机代码使用此类，并且不能在本机代码中使用托管类型。 此类将编译为针对 CLR，如类声明前面的`#pragma managed`指令所示。 有关此指令的详细信息，请参阅[托管、非托管](../preprocessor/managed-unmanaged.md)。

请注意数据库类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管类型，`gcroot`因此关键字是必需的。 有关 的详细信息`gcroot`，请参阅[：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机C++代码，如 前面的`#pragma unmanaged``main`指令所示。 在此示例中，我们正在创建一个新的 DatabaseClass 实例，并调用其方法来创建表并填充表中的某些行。 请注意，本机`VARIANT`类型作为数据库列 ObjectCol 的值传递。 在 DatabaseClass`VARIANT`中，使用<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间中的封送功能将这些类型的封送到托管对象。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A>用于将 a`VARIANT`封送<xref:System.Object>到 ，<xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A>并且该方法用于将<xref:System.Object>. `VARIANT`

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

- 要从命令行编译代码，请在名为 adonet_marshal_variant.cpp 的文件中保存代码示例，并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>为ADO.NET封送 SAFEARRAY

演示如何将本机`SAFEARRAY`添加到数据库以及如何将托管数组从数据库封送到本机`SAFEARRAY`。

### <a name="example"></a>示例

在此示例中，创建类 DatabaseClass 是为了与ADO.NET<xref:System.Data.DataTable>对象进行交互。 请注意，此类是本机C++（`class`与 或`ref class``value class`相比）。 这是必需的，因为我们希望从本机代码使用此类，并且不能在本机代码中使用托管类型。 此类将编译为针对 CLR，如类声明前面的`#pragma managed`指令所示。 有关此指令的详细信息，请参阅[托管、非托管](../preprocessor/managed-unmanaged.md)。

请注意数据库类的私有成员： `gcroot<DataTable ^> table`。 由于本机类型不能包含托管类型，`gcroot`因此关键字是必需的。 有关 的详细信息`gcroot`，请参阅[：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

此示例中的代码的其余部分是本机C++代码，如 前面的`#pragma unmanaged``main`指令所示。 在此示例中，我们正在创建一个新的 DatabaseClass 实例，并调用其方法来创建表并填充表中的某些行。 请注意，本机`SAFEARRAY`类型作为数据库列 ArrayIntsCol 的值传递。 在 DatabaseClass`SAFEARRAY`中，使用<xref:System.Runtime.InteropServices?displayProperty=fullName>命名空间中的封送功能将这些类型的封送到托管对象。 具体而言，该方法<xref:System.Runtime.InteropServices.Marshal.Copy%2A>用于将 a`SAFEARRAY`整理到由整数组成的托管数组，该方法<xref:System.Runtime.InteropServices.Marshal.Copy%2A>用于将管理整数数组封送到 。 `SAFEARRAY`

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

- 要从命令行编译代码，请在名为 adonet_marshal_safearray.cpp 的文件中保存代码示例，并输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>.NET Framework 安全性

有关涉及ADO.NET的安全问题的信息，请参阅[保护ADO.NET应用程序](/dotnet/framework/data/adonet/securing-ado-net-applications)。

## <a name="related-sections"></a>相关章节

|部分|说明|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|提供ADO.NET的概述，这是一组向 .NET 程序员公开数据访问服务的类。|

## <a name="see-also"></a>另请参阅

[.NET 编程，带C++/CLI（视觉C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[互操作性](/dotnet/framework/interop/index)
