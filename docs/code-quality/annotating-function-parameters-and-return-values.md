---
title: 对函数参数和返回值进行交代
description: 函数参数和返回值注释的参考指南。
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Outptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
ms.openlocfilehash: c787dcfb252da1abe47251d66c46689db289cf15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328000"
---
# <a name="annotating-function-parameters-and-return-values"></a>对函数参数和返回值进行交代

本文介绍了注释对简单函数参数（scalars）和指向结构和类的指针以及大多数缓冲区的典型用途。 本文还显示了注释的常见使用模式。 有关与函数相关的其他注释，请参阅[注释函数行为](../code-quality/annotating-function-behavior.md)。

## <a name="pointer-parameters"></a>指针参数

对于下表中的注释，当对指针参数进行批注时，如果指针为空，分析器将报告错误。 此注释适用于指针和指向的任何数据项。

### <a name="annotations-and-descriptions"></a>注释和说明

- `_In_`

     对标量、结构、指向结构的指针等的输入参数进行符号。 显式可用于简单的标量。 参数必须以预状态有效，并且不会修改。

- `_Out_`

     对标量、结构、指向结构的指针等输出参数进行分出。 不要将此注释应用于无法返回值的对象，例如，由值传递的标量。 参数不必在预状态下有效，但必须在后状态中有效。

- `_Inout_`

     对函数将更改的参数进行加号。 它必须在预状态和后状态中都有效，但假定在调用之前和之后具有不同的值。 必须应用于可修改的值。

- `_In_z_`

     指向用作输入的 null 端接字符串的指针。 字符串必须以预状态有效。 首选 的`PSTR`变体，这些变体已具有正确的注释。

- `_Inout_z_`

     指向将修改的 null 终止字符数组的指针。 它必须在调用之前和之后有效，但假定该值已更改。 可以移动空终止符，但只能访问到原始空终止符的元素。

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     指向数组的指针，该指针由函数读取。 数组的大小`s`元素，所有元素都必须有效。

     该`_bytes_`变体以字节而不是元素的形式提供大小。 仅当大小不能表示为元素时，才使用此变体。 例如，`char`仅当使用`_bytes_``wchar_t`的类似函数使用时，字符串才会使用该变体。

- `_In_reads_z_(s)`

     指向为 null 终止且具有已知大小的数组的指针。 到 null 终止符的元素（或者`s`如果没有空终止符）必须在预状态下有效。 如果大小以字节为单位已知，则按元素`s`大小缩放。

- `_In_reads_or_z_(s)`

     指向为 null 终止或具有已知大小的数组的指针，或两者兼而有之。 到 null 终止符的元素（或者`s`如果没有空终止符）必须在预状态下有效。 如果大小以字节为单位已知，则按元素`s`大小缩放。 （用于`strn`家庭。

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     指向由函数写入`s`的元素数组（resp. 字节）的指针。 数组元素不必在预状态下有效，并且未指定在后状态下有效的元素数。 如果参数类型上有注释，则它们以后状态应用。 例如，考虑下面的代码。

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     在此示例中，调用方为 提供 元素的`size`缓冲区`p1`。 `MyStringCopy`使其中一些元素有效。 更重要的是，`_Null_terminated_`上的`PWSTR`注释意味着`p1`在后状态下为 null 终止。 这样，有效元素的数量仍然定义良好，但不需要特定的元素计数。

     该`_bytes_`变体以字节而不是元素的形式提供大小。 仅当大小不能表示为元素时，才使用此变体。 例如，`char`仅当使用`_bytes_``wchar_t`的类似函数使用时，字符串才会使用该变体。

- `_Out_writes_z_(s)`

     指向元素数组的`s`指针。 元素不必在预状态下有效。 在后状态中，通过 null 终止符向上的元素（必须存在）必须有效。 如果大小以字节为单位已知，则按元素`s`大小缩放。

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     指向数组的指针，该数组在函数中读取和写入。 它是大小`s`元素，在状态前和后状态有效。

     该`_bytes_`变体以字节而不是元素的形式提供大小。 仅当大小不能表示为元素时，才使用此变体。 例如，`char`仅当使用`_bytes_``wchar_t`的类似函数使用时，字符串才会使用该变体。

- `_Inout_updates_z_(s)`

     指向为 null 终止且具有已知大小的数组的指针。 通过空终止符向上的元素（必须存在）必须在前状态和后状态中有效。 假定后状态中的值与前状态中的值不同;包括空终止符的位置。 如果大小以字节为单位已知，则按元素`s`大小缩放。

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     指向元素数组的`s`指针。 元素不必在预状态下有效。 在后状态下，最多到 -th`c`元素的元素必须有效。 如果`_bytes_`大小以字节为单位（而不是元素数）已知，则可以使用该变体。

     例如：

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     指向数组的指针，该指针由函数读取和写入。 它是大小`s`元素，所有元素都必须在预状态下有效，并且`c`元素必须在后状态中有效。

     该`_bytes_`变体以字节而不是元素的形式提供大小。 仅当大小不能表示为元素时，才使用此变体。 例如，`char`仅当使用`_bytes_``wchar_t`的类似函数使用时，字符串才会使用该变体。

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     指向数组的指针，该数组由大小`s`元素的函数读取和写入。 定义为等效于：

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     换句话说，缓冲区中一直存在`s`到预状态的每个元素在预状态和后状态中都有效。

     该`_bytes_`变体以字节而不是元素的形式提供大小。 仅当大小不能表示为元素时，才使用此变体。 例如，`char`仅当使用`_bytes_``wchar_t`的类似函数使用时，字符串才会使用该变体。

- `_In_reads_to_ptr_(p)`

     指向数组的指针`p - _Curr_`（即`p`减`_Curr_`号）是有效的表达式。 之前`p`的元素必须以预状态有效。

    例如：

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     指向 null 端接数组的指针，其`p - _Curr_`表达式（即`p`减`_Curr_`号）是有效的表达式。 之前`p`的元素必须以预状态有效。

- `_Out_writes_to_ptr_(p)`

     指向数组的指针`p - _Curr_`（即`p`减`_Curr_`号）是有效的表达式。 之前`p`的元素不必在预状态中有效，并且必须在后状态中有效。

- `_Out_writes_to_ptr_z_(p)`

     指向 null 端接数组的指针`p - _Curr_`（即`p`负`_Curr_`）是有效的表达式。 之前`p`的元素不必在预状态中有效，并且必须在后状态中有效。

## <a name="optional-pointer-parameters"></a>可选指针参数

当指针参数注释包含`_opt_`时，它指示参数可能为空。 否则，注释的表示行为与不包含 的版本相同`_opt_`。 下面是指针参数注释`_opt_`的变体列表：

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>输出指针参数

输出指针参数需要特殊的表示法来消除参数和指向位置的空值。

### <a name="annotations-and-descriptions"></a>注释和说明

- `_Outptr_`

   参数不能为空，在后状态下，指向位置不能为空，并且必须有效。

- `_Outptr_opt_`

   参数可能为空，但在后状态下，指向位置不能为空，并且必须有效。

- `_Outptr_result_maybenull_`

   参数不能为空，在后状态下，指向位置可以为空。

- `_Outptr_opt_result_maybenull_`

   参数可能为空，在后状态下，指向位置可以为空。

  在下表中，其他子字符串将插入到注释名称中，以进一步限定注释的含义。 各种`_z`子字符串是 、、、`_bytebuffer_``_to_``_COM_``_buffer_`和 。

> [!IMPORTANT]
> 如果要注释的接口是 COM，请使用这些批注的 COM 形式。 不要将 COM 注释与任何其他类型接口一起使用。

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   返回的指针具有`_Null_terminated_`注释。

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   返回的指针具有 COM 语义，因此带有返回`_On_failure_`的指针为空的后条件。

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   返回的指针指向大小`s`元素或字节的有效缓冲区。

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   返回的指针指向大小`s`元素或字节的缓冲区，其中第一个`c`缓冲区有效。

某些接口约定假定输出参数在失败时无效。 除了显式 COM 代码之外，首选下表中的窗体。 对于 COM 代码，请使用上一节中列出的相应的 COM 窗体。

- `_Result_nullonfailure_`

   修改其他注释。 如果函数失败，结果将设置为 null。

- `_Result_zeroonfailure_`

   修改其他注释。 如果函数失败，结果将设置为零。

- `_Outptr_result_nullonfailure_`

   如果函数成功，返回的指针指向有效缓冲区;如果函数失败，则返回的指针指向空缓冲区。 此注释适用于非可选参数。

- `_Outptr_opt_result_nullonfailure_`

   如果函数成功，返回的指针指向有效缓冲区;如果函数失败，则返回的指针指向空缓冲区。 此注释适用于可选参数。

- `_Outref_result_nullonfailure_`

   如果函数成功，返回的指针指向有效缓冲区;如果函数失败，则返回的指针指向空缓冲区。 此注释用于参考参数。

## <a name="output-reference-parameters"></a>输出参考参数

参考参数的常见用途是输出参数。 对于简单的输出引用参数，如`int&`，`_Out_`提供了正确的语义。 但是，当输出值是指针（如`int *&`）时，等效指针注释（如`_Outptr_ int **`）不提供正确的语义。 要简洁地表示指针类型的输出引用参数的语义，请使用以下复合注释：

### <a name="annotations-and-descriptions"></a>注释和说明

- `_Outref_`

     结果必须在后状态中有效，并且不能为 null。

- `_Outref_result_maybenull_`

     结果必须在后状态中有效，但在后状态时可能为空。

- `_Outref_result_buffer_(s)`

     结果必须在后状态中有效，并且不能为 null。 指向大小`s`元素的有效缓冲区。

- `_Outref_result_bytebuffer_(s)`

     结果必须在后状态中有效，并且不能为 null。 指向大小`s`字节的有效缓冲区。

- `_Outref_result_buffer_to_(s, c)`

     结果必须在后状态中有效，并且不能为 null。 指向元素的`s`缓冲区，其中第一个`c`有效。

- `_Outref_result_bytebuffer_to_(s, c)`

     结果必须在后状态中有效，并且不能为 null。 指向第一个`s``c`有效字节的缓冲区。

- `_Outref_result_buffer_all_(s)`

     结果必须在后状态中有效，并且不能为 null。 指向大小`s`有效元素的有效缓冲区。

- `_Outref_result_bytebuffer_all_(s)`

     结果必须在后状态中有效，并且不能为 null。 指向有效元素`s`字节的有效缓冲区。

- `_Outref_result_buffer_maybenull_(s)`

     结果必须在后状态中有效，但在后状态时可能为空。 指向大小`s`元素的有效缓冲区。

- `_Outref_result_bytebuffer_maybenull_(s)`

     结果必须在后状态中有效，但在后状态时可能为空。 指向大小`s`字节的有效缓冲区。

- `_Outref_result_buffer_to_maybenull_(s, c)`

     结果必须在后状态中有效，但在后状态时可能为空。 指向元素的`s`缓冲区，其中第一个`c`有效。

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     结果必须在后状态中有效，但在后状态时可能为空。 指向第一个`s``c`有效字节的缓冲区。

- `_Outref_result_buffer_all_maybenull_(s)`

     结果必须在后状态中有效，但在后状态时可能为空。 指向大小`s`有效元素的有效缓冲区。

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     结果必须在后状态中有效，但在后状态时可能为空。 指向有效元素`s`字节的有效缓冲区。

## <a name="return-values"></a>返回值

函数的返回值类似于`_Out_`参数，但处于不同的去引用级别，您不必考虑指向结果的指针的概念。 对于以下注释，返回值是注释的对象 - 标量、指向结构的指针或指向缓冲区的指针。 这些注释的语义与相应的`_Out_`注释相同。

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>格式化字符串参数

- `_Printf_format_string_`指示参数是用于表达式的`printf`格式字符串。

     **示例**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_`指示参数是用于表达式的`scanf`格式字符串。

     **示例**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_`指示参数是用于表达式的`scanf_s`格式字符串。

     **示例**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>其他常见注释

### <a name="annotations-and-descriptions"></a>注释和说明

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     参数、字段或结果在 从`low`到`hi`的范围（包括）中。 等效于`_Satisfies_(_Curr_ >= low && _Curr_ <= hi)`该对象应用于带标的对象以及适当的前状态或后状态条件。

    > [!IMPORTANT]
    > 尽管名称包含"in"和"out"，但 和`_In_``_Out_`的语义**不适用于**这些注释。

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     已用的已用值正是`expr`。 等效于`_Satisfies_(_Curr_ == expr)`该对象应用于带标的对象以及适当的前状态或后状态条件。

- `_Struct_size_bytes_(size)`

     应用于结构或类声明。 指示该类型的有效对象可能大于声明的类型，由 给出`size`的字节数。 例如：

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     然后，以类型`pM``MyStruct *`参数的字节为单位的缓冲区大小将采用：

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>相关资源

[代码分析团队博客](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>另请参阅

- [使用 SAL 批注以减少 C/C++ 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [了解 SAL](../code-quality/understanding-sal.md)
- [对函数行为进行批注](../code-quality/annotating-function-behavior.md)
- [批注结构和类](../code-quality/annotating-structs-and-classes.md)
- [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)
- [指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [内在函数](../code-quality/intrinsic-functions.md)
- [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)
