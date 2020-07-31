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
ms.openlocfilehash: 3f3980c98890382e77d9d89db2944bebf7b12319
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211055"
---
# <a name="data-access-using-adonet-ccli"></a>使用 ADO.NET 的数据访问 (C++/CLI)

ADO.NET 是用于数据访问的 .NET Framework API，可通过以前的数据访问解决方案提供强大的功能和易用性。 本部分介绍一些涉及 ADO.NET 的问题，这些问题对 Visual C++ 用户是唯一的，例如封送本机类型。

ADO.NET 在公共语言运行时（CLR）下运行。 因此，与 ADO.NET 交互的任何应用程序也必须以 CLR 为目标。 但这并不意味着本机应用程序不能使用 ADO.NET。 这些示例将演示如何从本机代码与 ADO.NET 数据库交互。

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>为 ADO.NET 封送 ANSI 字符串

演示如何将本机字符串（）添加 `char *` 到数据库，以及如何将数据库中的封送 <xref:System.String?displayProperty=fullName> 到本机字符串。

### <a name="example"></a>示例

在此示例中，创建了类 DatabaseClass 来与 ADO.NET 对象进行交互 <xref:System.Data.DataTable> 。 请注意，此类为本机 c + + **`class`** （与 **`ref class`** 或相比 **`value class`** ）。 这是必需的，因为我们希望使用本机代码中的此类，并且不能在本机代码中使用托管类型。 此类将编译为面向 CLR，如类声明之前的指令所指示的那样 `#pragma managed` 。 有关此指令的详细信息，请参阅[托管和非托管](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table` 。 由于本机类型不能包含托管类型，因此 `gcroot` 关键字是必需的。 有关的详细信息 `gcroot` ，请参阅[如何：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

在此示例中，代码的其余部分为本机 c + + 代码，如前面的指令所示 `#pragma unmanaged` `main` 。 在此示例中，我们将创建 DatabaseClass 的新实例，并调用其方法来创建表，并在表中填充一些行。 请注意，本机 c + + 字符串将作为数据库列 StringCol 的值进行传递。 在 DatabaseClass 中，使用在命名空间中找到的封送处理功能将这些字符串封送到托管字符串 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具体而言，方法 <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> 用于将封送 `char *` 到 <xref:System.String> ，并使用方法将 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 封送 <xref:System.String> 到 `char *` 。

> [!NOTE]
> 分配的内存 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 必须通过调用 <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> 或释放 `GlobalFree` 。

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

- 若要从命令行编译代码，请将代码示例保存在名为 adonet_marshal_string_native 的文件中，然后输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>为 ADO.NET 封送 BSTR 字符串

演示如何将 COM 字符串（）添加 `BSTR` 到数据库，以及如何将数据库中的封送处理 <xref:System.String?displayProperty=fullName> `BSTR` 。

### <a name="example"></a>示例

在此示例中，创建了类 DatabaseClass 来与 ADO.NET 对象进行交互 <xref:System.Data.DataTable> 。 请注意，此类为本机 c + + **`class`** （与 **`ref class`** 或相比 **`value class`** ）。 这是必需的，因为我们希望使用本机代码中的此类，并且不能在本机代码中使用托管类型。 此类将编译为面向 CLR，如类声明之前的指令所指示的那样 `#pragma managed` 。 有关此指令的详细信息，请参阅[托管和非托管](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table` 。 由于本机类型不能包含托管类型，因此 `gcroot` 关键字是必需的。 有关的详细信息 `gcroot` ，请参阅[如何：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

在此示例中，代码的其余部分为本机 c + + 代码，如前面的指令所示 `#pragma unmanaged` `main` 。 在此示例中，我们将创建 DatabaseClass 的新实例，并调用其方法来创建表，并在表中填充一些行。 请注意，COM 字符串将作为数据库列 StringCol 的值进行传递。 在 DatabaseClass 中，使用在命名空间中找到的封送处理功能将这些字符串封送到托管字符串 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具体而言，方法 <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> 用于将封送 `BSTR` 到 <xref:System.String> ，并使用方法将 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 封送 <xref:System.String> 到 `BSTR` 。

> [!NOTE]
> 分配的内存 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 必须通过调用 <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> 或释放 `SysFreeString` 。

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

- 若要从命令行编译代码，请将代码示例保存在名为 adonet_marshal_string_native 的文件中，然后输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>ADO.NET 的封送 Unicode 字符串

演示如何将本机 Unicode 字符串（）添加 `wchar_t *` 到数据库，以及如何将数据库中的封送 <xref:System.String?displayProperty=fullName> 到本机 unicode 字符串。

### <a name="example"></a>示例

在此示例中，创建了类 DatabaseClass 来与 ADO.NET 对象进行交互 <xref:System.Data.DataTable> 。 请注意，此类为本机 c + + **`class`** （与 **`ref class`** 或相比 **`value class`** ）。 这是必需的，因为我们希望使用本机代码中的此类，并且不能在本机代码中使用托管类型。 此类将编译为面向 CLR，如类声明之前的指令所指示的那样 `#pragma managed` 。 有关此指令的详细信息，请参阅[托管和非托管](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table` 。 由于本机类型不能包含托管类型，因此 `gcroot` 关键字是必需的。 有关的详细信息 `gcroot` ，请参阅[如何：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

在此示例中，代码的其余部分为本机 c + + 代码，如前面的指令所示 `#pragma unmanaged` `main` 。 在此示例中，我们将创建 DatabaseClass 的新实例，并调用其方法来创建表，并在表中填充一些行。 请注意，Unicode c + + 字符串将作为数据库列 StringCol 的值进行传递。 在 DatabaseClass 中，使用在命名空间中找到的封送处理功能将这些字符串封送到托管字符串 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具体而言，方法 <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> 用于将封送 `wchar_t *` 到 <xref:System.String> ，并使用方法将 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> 封送 <xref:System.String> 到 `wchar_t *` 。

> [!NOTE]
> 分配的内存 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> 必须通过调用 <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> 或释放 `GlobalFree` 。

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

- 若要从命令行编译代码，请将代码示例保存在名为 adonet_marshal_string_wide 的文件中，然后输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>封送变量 ADO.NET

演示如何将本机添加 `VARIANT` 到数据库，以及如何将数据库中的封送 <xref:System.Object?displayProperty=fullName> 到本机 `VARIANT` 。

### <a name="example"></a>示例

在此示例中，创建了类 DatabaseClass 来与 ADO.NET 对象进行交互 <xref:System.Data.DataTable> 。 请注意，此类为本机 c + + **`class`** （与 **`ref class`** 或相比 **`value class`** ）。 这是必需的，因为我们希望使用本机代码中的此类，并且不能在本机代码中使用托管类型。 此类将编译为面向 CLR，如类声明之前的指令所指示的那样 `#pragma managed` 。 有关此指令的详细信息，请参阅[托管和非托管](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table` 。 由于本机类型不能包含托管类型，因此 `gcroot` 关键字是必需的。 有关的详细信息 `gcroot` ，请参阅[如何：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

在此示例中，代码的其余部分为本机 c + + 代码，如前面的指令所示 `#pragma unmanaged` `main` 。 在此示例中，我们将创建 DatabaseClass 的新实例，并调用其方法来创建表，并在表中填充一些行。 请注意，本机 `VARIANT` 类型作为数据库列 ObjectCol 的值进行传递。 在 DatabaseClass 中， `VARIANT` 将使用在命名空间中找到的封送处理功能将这些类型封送到托管对象 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具体而言，方法 <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> 用于将封送 `VARIANT` 到 <xref:System.Object> ，并使用方法将 <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> 封送 <xref:System.Object> 到 `VARIANT` 。

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

- 若要从命令行编译代码，请将代码示例保存在名为 adonet_marshal_variant 的文件中，然后输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>封送用于 ADO.NET 的 SAFEARRAY

演示如何将本机添加 `SAFEARRAY` 到数据库，以及如何将托管数组从数据库封送到本机 `SAFEARRAY` 。

### <a name="example"></a>示例

在此示例中，创建了类 DatabaseClass 来与 ADO.NET 对象进行交互 <xref:System.Data.DataTable> 。 请注意，此类为本机 c + + **`class`** （与 **`ref class`** 或相比 **`value class`** ）。 这是必需的，因为我们希望使用本机代码中的此类，并且不能在本机代码中使用托管类型。 此类将编译为面向 CLR，如类声明之前的指令所指示的那样 `#pragma managed` 。 有关此指令的详细信息，请参阅[托管和非托管](../preprocessor/managed-unmanaged.md)。

请注意 DatabaseClass 类的私有成员： `gcroot<DataTable ^> table` 。 由于本机类型不能包含托管类型，因此 `gcroot` 关键字是必需的。 有关的详细信息 `gcroot` ，请参阅[如何：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)。

在此示例中，代码的其余部分为本机 c + + 代码，如前面的指令所示 `#pragma unmanaged` `main` 。 在此示例中，我们将创建 DatabaseClass 的新实例，并调用其方法来创建表，并在表中填充一些行。 请注意，本机 `SAFEARRAY` 类型作为数据库列 ArrayIntsCol 的值进行传递。 在 DatabaseClass 中， `SAFEARRAY` 将使用在命名空间中找到的封送处理功能将这些类型封送到托管对象 <xref:System.Runtime.InteropServices?displayProperty=fullName> 。 具体而言，方法 <xref:System.Runtime.InteropServices.Marshal.Copy%2A> 用于将一个封送 `SAFEARRAY` 到托管整数数组，方法 <xref:System.Runtime.InteropServices.Marshal.Copy%2A> 用于将托管的整数数组封送到 `SAFEARRAY` 。

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

- 若要从命令行编译代码，请将代码示例保存在名为 adonet_marshal_safearray 的文件中，然后输入以下语句：

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>.NET Framework 安全性

有关涉及 ADO.NET 的安全问题的信息，请参阅[保护 ADO.NET 应用程序](/dotnet/framework/data/adonet/securing-ado-net-applications)。

## <a name="related-sections"></a>相关章节

|部分|说明|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|概述 ADO.NET，这是一组向 .NET 程序员公开数据访问服务的类。|

## <a name="see-also"></a>另请参阅

[用 c + +/CLI 进行 .NET 编程（Visual C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[本机和 .NET 互操作性](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[互操作性](/dotnet/framework/interop/index)
