---
title: CStringT 类
ms.date: 03/27/2019
f1_keywords:
- CStringT
- ATLSTR/ATL::CStringT
- ATLSTR/ATL::CStringT::CStringT
- ATLSTR/ATL::CStringT::AllocSysString
- ATLSTR/ATL::CStringT::AnsiToOem
- ATLSTR/ATL::CStringT::AppendFormat
- ATLSTR/ATL::CStringT::Collate
- ATLSTR/ATL::CStringT::CollateNoCase
- ATLSTR/ATL::CStringT::Compare
- ATLSTR/ATL::CStringT::CompareNoCase
- ATLSTR/ATL::CStringT::Delete
- ATLSTR/ATL::CStringT::Find
- ATLSTR/ATL::CStringT::FindOneOf
- ATLSTR/ATL::CStringT::Format
- ATLSTR/ATL::CStringT::FormatMessage
- ATLSTR/ATL::CStringT::FormatMessageV
- ATLSTR/ATL::CStringT::FormatV
- ATLSTR/ATL::CStringT::GetEnvironmentVariable
- ATLSTR/ATL::CStringT::Insert
- ATLSTR/ATL::CStringT::Left
- ATLSTR/ATL::CStringT::LoadString
- ATLSTR/ATL::CStringT::MakeLower
- ATLSTR/ATL::CStringT::MakeReverse
- ATLSTR/ATL::CStringT::MakeUpper
- ATLSTR/ATL::CStringT::Mid
- ATLSTR/ATL::CStringT::OemToAnsi
- ATLSTR/ATL::CStringT::Remove
- ATLSTR/ATL::CStringT::Replace
- ATLSTR/ATL::CStringT::ReverseFind
- ATLSTR/ATL::CStringT::Right
- ATLSTR/ATL::CStringT::SetSysString
- ATLSTR/ATL::CStringT::SpanExcluding
- ATLSTR/ATL::CStringT::SpanIncluding
- ATLSTR/ATL::CStringT::Tokenize
- ATLSTR/ATL::CStringT::Trim
- ATLSTR/ATL::CStringT::TrimLeft
- ATLSTR/ATL::CStringT::TrimRight
- CSTRINGT/CStringT
- CSTRINGT/CStringT::CStringT
- CSTRINGT/CStringT::AllocSysString
- CSTRINGT/CStringT::AnsiToOem
- CSTRINGT/CStringT::AppendFormat
- CSTRINGT/CStringT::Collate
- CSTRINGT/CStringT::CollateNoCase
- CSTRINGT/CStringT::Compare
- CSTRINGT/CStringT::CompareNoCase
- CSTRINGT/CStringT::Delete
- CSTRINGT/CStringT::Find
- CSTRINGT/CStringT::FindOneOf
- CSTRINGT/CStringT::Format
- CSTRINGT/CStringT::FormatMessage
- CSTRINGT/CStringT::FormatMessageV
- CSTRINGT/CStringT::FormatV
- CSTRINGT/CStringT::GetEnvironmentVariable
- CSTRINGT/CStringT::Insert
- CSTRINGT/CStringT::Left
- CSTRINGT/CStringT::LoadString
- CSTRINGT/CStringT::MakeLower
- CSTRINGT/CStringT::MakeReverse
- CSTRINGT/CStringT::MakeUpper
- CSTRINGT/CStringT::Mid
- CSTRINGT/CStringT::OemToAnsi
- CSTRINGT/CStringT::Remove
- CSTRINGT/CStringT::Replace
- CSTRINGT/CStringT::ReverseFind
- CSTRINGT/CStringT::Right
- CSTRINGT/CStringT::SetSysString
- CSTRINGT/CStringT::SpanExcluding
- CSTRINGT/CStringT::SpanIncluding
- CSTRINGT/CStringT::Tokenize
- CSTRINGT/CStringT::Trim
- CSTRINGT/CStringT::TrimLeft
- CSTRINGT/CStringT::TrimRight
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
ms.openlocfilehash: 90f63b474f509b4d1a15ad6fe11bda61c343f483
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317592"
---
# <a name="cstringt-class"></a>CStringT 类

此类表示对象`CStringT`。

## <a name="syntax"></a>语法

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>参数

*BaseType*<br/>
字符串类的字符类型。 可以是以下值之一：

- **字符**（用于 ANSI 字符串）。

- **wchar_t（** 对于 Unicode 字符串）。

- TCHAR（适用于 ANSI 和 Unicode 字符串）。

*弦乐*<br/>
确定字符串类是否需要 C 运行时 （CRT） 库支持以及字符串资源的位置。 可以是以下值之一：

- **斯特尔特拉特<wchar_t &#124;&#124;****查尔、查克拉茨克拉特 wchar_t<&#124;&#124;** 的 **&#124;&#124;****的查尔**&#124;**查尔 > >**

   该类需要 CRT 支持并搜索由（`m_hInstResource`应用程序模块类的成员）指定的模块中的资源字符串。

- **斯特尔特拉特< wchar_t&#124;&#124;****查尔&#124;&#124;，ChTraitsos<wchar_t&#124;&#124;****查尔**&#124;**查尔 > >** **char**

   该类不需要 CRT 支持并搜索由（`m_hInstResource`应用程序模块类的成员）指定的模块中的资源字符串。

- **斯特特拉特姆足球俱乐部<wchar_t&#124;&#124;****查尔****&#124;，ChTraitsCRT<wchar_t&#124;&#124;****查尔****&#124;查尔 > >**

   该类需要 CRT 支持并使用标准 MFC 搜索算法搜索资源字符串。

- **斯特特拉特姆足球俱乐部<wchar_t&#124;&#124;****查尔、ChTraitsos<wchar_t&#124;&#124;****查尔****&#124;TCHAR > >** **char**

   该类不需要 CRT 支持并使用标准 MFC 搜索算法搜索资源字符串。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[弦乐：：CStringT](#cstringt)|以各种方式构造`CStringT`对象。|
|[弦乐：：*CStringT](#_dtorcstringt)|销毁 `CStringT` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CStringT：allocSysString](#allocsysstring)|从`CStringT`数据分配 BSTR。|
|[弦乐：：安西托姆](#ansitooem)|从 ANSI 字符集到 OEM 字符集进行就地转换。|
|[CStringT：：附加格式](#appendformat)|将格式化的数据追加到现有`CStringT`对象。|
|[CStringT：：整理](#collate)|比较两个字符串（区分大小写，使用特定于区域设置的信息）。|
|[CStringT：：克拉特诺凯斯](#collatenocase)|比较两个字符串（区分大小写，使用特定于区域设置的信息）。|
|[CStringT：比较](#compare)|比较两个字符串（区分大小写）。|
|[CStringT：比较无案例](#comparenocase)|比较两个字符串（不区分大小写）。|
|[CStringT：:D埃莱特](#delete)|从字符串中删除字符或字符。|
|[CStringT：查找](#find)|在较大的字符串中查找字符或子字符串。|
|[弦乐：：查找](#findoneof)|从集中查找第一个匹配字符。|
|[CStringT：格式](#format)|使字符串的格式`sprintf`与字符串一样。|
|[CStringT：：格式消息](#formatmessage)|设置消息字符串的格式。|
|[CStringT：：格式消息V](#formatmessagev)|使用变量参数列表设置消息字符串的格式。|
|[CStringT：：格式V](#formatv)|使用参数的变量列表设置字符串的格式。|
|[CStringT：获取环境变量](#getenvironmentvariable)|将字符串设置为指定环境变量的值。|
|[CStringT：插入](#insert)|在字符串中的给定索引上插入单个字符或子字符串。|
|[CStringT：左](#left)|提取字符串的左侧部分。|
|[CStringT：：加载字符串](#loadstring)|从 Windows`CStringT`资源加载现有对象。|
|[CStringT：：制作下](#makelower)|将此字符串中的所有字符转换为小写字符。|
|[CStringT：：使反向](#makereverse)|反转字符串。|
|[CStringT：：制作上](#makeupper)|将此字符串中的所有字符转换为大写字符。|
|[CStringT：中](#mid)|提取字符串的中间部分。|
|[弦乐：：OemToansi](#oemtoansi)|从 OEM 字符集到 ANSI 字符集进行就地转换。|
|[CStringT：：删除](#remove)|从字符串中删除指示的字符。|
|[CStringT：替换](#replace)|将指示的字符替换为其他字符。|
|[CStringT：：反向查找](#reversefind)|在较大的字符串中查找字符;从结束开始。|
|[CStringT：右](#right)|提取字符串的右侧部分。|
|[CStringT：：SetSysString](#setsysstring)|使用`CStringT`来自对象的数据设置现有的 BSTR 对象。|
|[CStringT：：范围排除](#spanexcluding)|从字符串中提取字符，从第一个字符开始，这些字符不在 标识`pszCharSet`的字符集中。|
|[CStringT：：跨栏包括](#spanincluding)|提取仅包含集中字符的子字符串。|
|[CStringT：：令牌化](#tokenize)|提取目标字符串中指定的令牌。|
|[CStringT：修剪](#trim)|从字符串中修剪所有前导和尾随空格字符。|
|[CStringT：：修剪左](#trimleft)|修剪字符串中领先的空格字符。|
|[CStringT：：修剪权](#trimright)|修剪字符串中尾随空格字符。|

### <a name="operators"></a>运算符

|||
|-|-|
|[CStringT：：运算符 |](#operator_eq)|为`CStringT`对象分配新值。|
|[CStringT：运算符 |](#operator_add)|串联两个字符串或一个字符和一个字符串。|
|[CStringT：：运算符 |](#operator_add_eq)|将新字符串串联到现有字符串的末尾。|
|[CStringT：：运算符 |](#operator_eq_eq)|确定两个字符串在逻辑上是否相等。|
|[CStringT：：操作员！]](#operator_neq)|确定两个字符串在逻辑上是否不相等。|
|[CStringT：：运算符&lt;](#operator_lt)|确定运算符左侧的字符串是否小于右侧的字符串。|
|[CStringT：：运算符&gt;](#operator_gt)|确定运算符左侧的字符串是否大于右侧的字符串。|
|[CStringT：：运算符&lt;=](#operator_lt_eq)|确定运算符左侧的字符串是否小于或等于右侧的字符串。|
|[CStringT：：运算符&gt;=](#operator_gt_eq)|确定运算符左侧的字符串是否大于或等于右侧的字符串。|

## <a name="remarks"></a>备注

`CStringT`继承自[CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)。 高级功能（如字符操作、排序和搜索）由 实现`CStringT`。

> [!NOTE]
> `CStringT`对象能够引发异常。 当`CStringT`对象由于任何原因耗尽内存时，就会发生这种情况。

对象`CStringT`由可变长度的字符序列组成。 `CStringT`使用类似于 Basic 的语法提供函数和运算符。 串联和比较运算符，以及简化的内存管理，使`CStringT`对象比普通字符数组更易于使用。

> [!NOTE]
> 尽管可以创建`CStringT`包含嵌入的空字符的实例，但我们建议不要这样做。 对`CStringT`包含嵌入的空字符的对象调用方法和运算符可以产生意外的结果。

通过使用`BaseType`和`StringTraits`参数的不同组合，`CStringT`对象可以采用以下类型，这些类型已由 ATL 库预定义。

如果在 ATL 应用程序中使用：

`CString``CStringA`，`CStringW`并从 MFC DLL （MFC90） 导出。DLL），从不从用户 DLL。 这样做是为了防止`CStringT`被乘以定义。

> [!NOTE]
> 如果代码包含[使用 CStringT 导出字符串类](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)中所述的链接器错误的解决方法，则应删除该代码。 不再需要它。

以下字符串类型在基于 MFC 的应用程序中可用：

|CStringT 类型|声明|
|-------------------|-----------------|
|`CStringA`|支持 CRT 的 ANSI 字符类型字符串。|
|`CStringW`|支持 CRT 的 Unicode 字符类型字符串。|
|`CString`|支持 CRT 的 ANSI 和 Unicode 字符类型。|

定义ATL_CSTRING_NO_CRT的项目中可以使用以下字符串类型：

|CStringT 类型|声明|
|-------------------|-----------------|
|`CAtlStringA`|不支持 CRT 的 ANSI 字符类型字符串。|
|`CAtlStringW`|不支持 CRT 的 Unicode 字符类型字符串。|
|`CAtlString`|ANSI 和 Unicode 字符类型均无 CRT 支持。|

未定义ATL_CSTRING_NO_CRT的项目中可以使用以下字符串类型：

|CStringT 类型|声明|
|-------------------|-----------------|
|`CAtlStringA`|支持 CRT 的 ANSI 字符类型字符串。|
|`CAtlStringW`|支持 CRT 的 Unicode 字符类型字符串。|
|`CAtlString`|支持 CRT 的 ANSI 和 Unicode 字符类型。|

`CString`对象还具有以下特征：

- `CStringT`对象可以由于串联操作而增大。

- `CStringT`对象遵循"值语义"。 将`CStringT`对象视为实际字符串，而不是指向字符串的指针。

- 您可以自由地将`CStringT`对象替换为`PCXSTR`函数参数。

- 字符串缓冲区的自定义内存管理。 有关详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="cstringt-predefined-types"></a>CStringT 预定义类型

由于`CStringT`使用模板参数定义受支持的字符类型[（wchar_t](../../c-runtime-library/standard-types.md)或[char），](../../c-runtime-library/standard-types.md)因此方法参数类型有时可能很复杂。 为了简化此问题，在整个`CStringT`类中定义和使用一组预定义类型。 下表列出了各种类型：

|名称|说明|
|----------|-----------------|
|`XCHAR`|与`CStringT`对象具有相同字符类型的单个字符 **（wchar_t**或**字符**）。|
|`YCHAR`|具有相反字符类型的单个字符 **（wchar_t**或**字符**）作为`CStringT`对象。|
|`PXSTR`|指向与对象具有相同字符类型的字符串 **（wchar_t**或**字符**）的`CStringT`指针。|
|`PYSTR`|指向字符串 **（wchar_t**或**字符**）的指针，该指针的字符类型为`CStringT`对象。|
|`PCXSTR`|指向与对象具有相同字符类型的**const**字符串 **（wchar_t**或**字符**）的`CStringT`指针。|
|`PCYSTR`|指向**const**字符串 **（wchar_t**或**字符**）的指针，该指针具有相反的字符类型`CStringT`作为对象。|

> [!NOTE]
> 以前`CString`使用 （如`AssignCopy`） 的未记录方法的代码必须替换为使用以下文档记录的方法`CStringT`（如`GetBuffer`或`ReleaseBuffer`） 的代码。 这些方法是从 继承的`CSimpleStringT`。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>要求

|标头|用于|
|------------|-------------|
|cstringt.h|仅限 MFC 的字符串对象|
|atlstr.h|非 MFC 字符串对象|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a>CStringT：allocSysString

分配 BSTR 类型的自动化兼容字符串，并将`CStringT`对象的内容复制到该字符串中，包括终止空字符。

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>返回值

新分配的字符串。

### <a name="remarks"></a>备注

在 MFC 程序中，如果内存不足，将引发[CMemoryexception 类](../../mfc/reference/cmemoryexception-class.md)。 在 ATL 程序中，将抛出一个[CAtlException。](../../atl/reference/catlexception-class.md) 此函数通常用于返回自动化的字符串。

通常，如果此字符串作为 [in] 参数传递给 COM 函数，则这需要调用方释放该字符串。 这可以通过使用[SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)来实现，如 Windows SDK 中所述。 有关详细信息，请参阅为[BSTR 分配和释放内存](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)。

有关 Windows 中的 OLE 分配功能的详细信息，请参阅 Windows SDK 中的[SysAllocString。](/windows/win32/api/oleauto/nf-oleauto-sysallocstring)

### <a name="example"></a>示例

以下示例演示了 `CStringT::AllocSysString` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a>弦乐：：安西托姆

将此`CStringT`对象中的所有字符从 ANSI 字符集转换为 OEM 字符集。

```
void AnsiToOem();
```

### <a name="remarks"></a>备注

如果定义了_UNICODE，则该函数不可用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a>CStringT：：附加格式

将格式化的数据追加到现有`CStringT`对象。

```
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>参数

*psz格式*<br/>
格式控制字符串。

*nFormatID*<br/>
包含格式控制字符串的字符串资源标识符。

argument**<br/>
可选参数。

### <a name="remarks"></a>备注

此函数在 中设置和附加一系列字符和值`CStringT`。 每个可选参数（如果有）根据*pszFormat 中的*相应格式规范或*nFormatID*标识的字符串资源进行转换和追加。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a>CStringT：：整理

使用泛文本函数`_tcscoll`比较两个字符串。

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>参数

*psz*<br/>
用于比较的另一个字符串。

### <a name="return-value"></a>返回值

如果字符串相同，则为零，如果此对象`CStringT`小于*psz，* 则< 0;如果此`CStringT`对象大于*psz，* 则> 0。

### <a name="remarks"></a>备注

泛文本函数`_tcscoll`， 在 TCHAR 中定义.H， 映射到`strcoll`，`wcscoll`或`_mbscoll`， 取决于编译时定义的字符集。 每个函数根据当前使用的代码页对字符串执行区分大小写的比较。 有关详细信息，请参阅[斯特科尔、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l。](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a>CStringT：：克拉特诺凯斯

使用泛文本函数`_tcscoll`比较两个字符串。

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>参数

*psz*<br/>
用于比较的另一个字符串。

### <a name="return-value"></a>返回值

如果字符串相同（忽略大小写），则< 0（如果此`CStringT`对象小于*psz（* 忽略大小写），则>如果此`CStringT`对象大于*psz（* 忽略大小写）。

### <a name="remarks"></a>备注

泛文本函数`_tcscoll`， 在 TCHAR 中定义.H， 映射到`stricoll`，`wcsicoll`或`_mbsicoll`， 取决于编译时定义的字符集。 每个函数根据当前使用的代码页对字符串执行不区分大小写的比较。 有关详细信息，请参阅[斯特科尔、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l。](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a>CStringT：比较

比较两个字符串（区分大小写）。

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>参数

*psz*<br/>
用于比较的另一个字符串。

### <a name="return-value"></a>返回值

如果字符串相同，则为零，如果此对象`CStringT`小于*psz，* 则< 0;如果此`CStringT`对象大于*psz，* 则> 0。

### <a name="remarks"></a>备注

泛文本函数`_tcscmp`， 在 TCHAR 中定义.H， 映射到`strcmp`，`wcscmp`或`_mbscmp`， 取决于编译时定义的字符集。 每个函数执行字符串的区分大小写比较，不受区域设置的影响。 有关详细信息，请参阅[strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)。

如果字符串包含嵌入的 null，为了比较，字符串被视为在第一个嵌入的 null 字符处被截断。

### <a name="example"></a>示例

以下示例演示了 `CStringT::Compare` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a>CStringT：比较无案例

比较两个字符串（不区分大小写）。

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>参数

*psz*<br/>
用于比较的另一个字符串。

### <a name="return-value"></a>返回值

如果字符串相同（忽略大小写），则<0（如果此`CStringT`对象小于*psz（* 忽略大小写），则>如果此`CStringT`对象大于*psz（* 忽略大小写）。

### <a name="remarks"></a>备注

泛文本函数`_tcsicmp`， 在 TCHAR 中定义.H，映射到`_stricmp`或`_wcsicmp``_mbsicmp`，具体取决于编译时定义的字符集。 每个函数执行不区分大小写的字符串比较。 比较取决于区域设置LC_CTYPE方面，而不是LC_COLLATE。 有关详细信息，请参阅[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l_mbsicmp_l。](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a>弦乐：：CStringT

构造 `CStringT` 对象。

```
CStringT() throw() :
    CThisSimpleString(StringTraits::GetDefaultManager());

explicit CStringT(IAtlStringMgr* pStringMgr) throw() :
    CThisSimpleString( pStringMgr);

CStringT(const VARIANT& varSrc);

CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);

CStringT(const CStringT& strSrc) :
    CThisSimpleString( strSrc);

operator CSimpleStringT<
                    BaseType,
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()

template <bool bMFCDLL>
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :
    CThisSimpleString( strSrc);

template <class SystemString>
CStringT(SystemString^ pString) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength) :
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());

CStringT(const YCHAR* pch, int nLength) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :
    CThisSimpleString( pch, nLength, pStringMgr);

CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);
```

### <a name="parameters"></a>参数

*Pch*<br/>
指向长度*nLength*的字符数组的指针，而不是 null 终止。

*n 长度*<br/>
*pch*中字符数的计数。

*ch*<br/>
单个字符。

*皮茨斯尔克*<br/>
要复制到此`CStringT`对象的 null 终止字符串。

*普斯特林姆格*<br/>
指向对象的内存管理器的`CStringT`指针。 有关 的详细信息`IAtlStringMgr`和内存管理`CStringT`，请参阅使用[CStringT 的内存管理](../../atl-mfc-shared/memory-management-with-cstringt.md)。

*斯特斯尔克*<br/>
要复制到`CStringT`此`CStringT`对象的现有对象。 有关`CThisString`和`CThisSimpleString`的详细信息，请参阅备注部分。

*varSrc*<br/>
要复制到此`CStringT`对象的变体对象。

*BaseType*<br/>
字符串类的字符类型。 可以是以下值之一：

**字符**（用于 ANSI 字符串）。

**wchar_t（** 对于 Unicode 字符串）。

TCHAR（适用于 ANSI 和 Unicode 字符串）。

*bMFCDLL*<br/>
布尔，用于指定项目是否为 MFC DLL （TRUE） （FALSE）。

*系统字符串*<br/>
必须`System::String`为 ，并且项目必须使用 /clr 编译。

*pString*<br/>
`CStringT`对象的句柄。

### <a name="remarks"></a>备注

由于构造函数将输入数据复制到新的分配存储中，因此您应该注意可能会出现内存异常。 请注意，其中一些构造函数充当转换函数。 例如，这允许您替换需要`CStringT`对象的 LPTSTR。

- `CStringT`：`LPCSTR``lpsz`从 ANSI`CStringT`字符串构造 Unicode。 您还可以使用此构造函数加载字符串资源，如下例所示。

- `CStringT(`： 从 Unicode 字符串构造 a。 `CStringT` `LPCWSTR` `lpsz`

- `CStringT`（ `const unsigned char*` `psz` ）： 允许您构造`CStringT`从指针到**未签名的字符**。

> [!NOTE]
> 定义_CSTRING_DISABLE_NARROW_WIDE_CONVERSION宏以关闭 ANSI 和 Unicode 字符串之间的隐式字符串转换。 宏从支持转换的编译构造函数中排除。

请注意 *，strSrc*参数可以是 或`CStringT``CThisSimpleString`对象。 对于`CStringT`，使用其默认实例化之一`CString`（、`CStringA`或`CStringW`）。for `CThisSimpleString`，使用此**指针。** `CThisSimpleString`声明[CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)的实例 ，它是一个较小的字符串类，其内置功能比`CStringT`类少。

重载运算符`CSimpleStringT<>&()`从`CSimpleStringT`声明构造`CStringT`对象。

> [!NOTE]
> 尽管可以创建`CStringT`包含嵌入的空字符的实例，但我们建议不要这样做。 对`CStringT`包含嵌入的空字符的对象调用方法和运算符可以产生意外的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a>弦乐：：*CStringT

销毁`CStringT`对象。

```
~CStringT() throw();
```

### <a name="remarks"></a>备注

销毁`CStringT`对象。

## <a name="cstringtdelete"></a><a name="delete"></a>CStringT：:D埃莱特

从字符串中删除以给定索引中的字符开头的字符。

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
要删除`CStringT`的对象中第一个字符的零基索引。

*nCount*<br/>
要删除的字符数。

### <a name="return-value"></a>返回值

已更改字符串的长度。

### <a name="remarks"></a>备注

如果*nCount*长于字符串，则将删除字符串的其余部分。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a>CStringT：查找

搜索此字符串以搜索字符或子字符串的第一个匹配项。

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>参数

*pszSub*<br/>
要搜索的子字符串。

*i 开始*<br/>
字符串中要开始搜索的字符的索引，或从开头开始的 0。

*ch*<br/>
要搜索的单个字符。

### <a name="return-value"></a>返回值

此`CStringT`对象中第一个字符的零基索引，与请求的子字符串或字符匹配;-1 如果未找到子字符串或字符。

### <a name="remarks"></a>备注

函数重载以接受单个字符（类似于运行时函数`strchr`）和字符串（类似于`strstr`）。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a>弦乐：：查找

搜索此字符串的第一个字符，该字符与*pszCharSet*中包含的任何字符匹配。

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>参数

*pszCharSet*<br/>
包含用于匹配的字符的字符串。

### <a name="return-value"></a>返回值

此字符串中第一个字符的零基索引，该索引也位于*pszCharSet 中*;-1 如果没有匹配项。

### <a name="remarks"></a>备注

查找*pszCharSet*中任何字符的第一次出现。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a>CStringT：格式

以sprintf_s将数据格式转换为`CStringT`C 样式字符数组[sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)的方式将格式化数据写入 。

```
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>参数

*nFormatID*<br/>
包含格式控制字符串的字符串资源标识符。

*psz格式*<br/>
格式控制字符串。

argument**<br/>
可选参数。

### <a name="remarks"></a>备注

此函数在 中设置和存储一系列字符和值`CStringT`。 每个可选参数（如果有）根据*pszFormat 中的*相应格式规范或*nFormatID*标识的字符串资源进行转换和输出。

如果字符串对象本身作为 参数提供给`Format`，则调用将失败。 例如，以下代码将导致不可预知的结果：

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

有关详细信息，请参阅[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a>CStringT：：格式消息

设置消息字符串的格式。

```
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>参数

*nFormatID*<br/>
包含未格式化消息文本的字符串资源标识符。

*psz格式*<br/>
指向格式控制字符串。 它将被扫描为插入和相应的格式。 格式字符串类似于运行时函数*printf-style*格式字符串，只不过它允许以任意顺序插入参数。

argument**<br/>
可选参数。

### <a name="remarks"></a>备注

函数需要消息定义作为输入。 消息定义由*pszFormat*或*nFormatID*标识的字符串资源确定。 该函数将格式化的消息文本复制到对象，`CStringT`并处理任何嵌入的插入序列（如果请求）。

> [!NOTE]
> `FormatMessage`尝试为新格式化的字符串分配系统内存。 如果此尝试失败，将自动引发内存异常。

每个插入必须具有遵循*pszFormat*或*nFormatID*参数的相应参数。 在消息文本中，支持多个转义序列来动态格式化消息。 有关详细信息，请参阅 Windows SDK 中的 Windows[格式消息](/windows/win32/api/winbase/nf-winbase-formatmessage)功能。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a>CStringT：：格式消息V

使用变量参数列表设置消息字符串的格式。

```
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>参数

*psz格式*<br/>
指向格式控制字符串。 它将被扫描为插入和相应的格式。 格式字符串类似于运行时函数`printf`样式格式字符串，只不过它允许以任意顺序插入参数。

*pArglist*<br/>
指向参数列表的指针。

### <a name="remarks"></a>备注

该函数需要消息定义作为输入，由*pszFormat*确定。 函数将格式化的消息文本和参数的变量列表复制到`CStringT`对象，如果请求，处理任何嵌入的插入序列。

> [!NOTE]
> `FormatMessageV`调用[CStringT：：FormatMessage](#formatmessage)，它尝试为新格式化的字符串分配系统内存。 如果此尝试失败，将自动引发内存异常。

有关详细信息，请参阅 Windows SDK 中的 Windows[格式消息](/windows/win32/api/winbase/nf-winbase-formatmessage)功能。

## <a name="cstringtformatv"></a><a name="formatv"></a>CStringT：：格式V

使用变量参数列表设置消息字符串的格式。

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>参数

*psz格式*<br/>
指向格式控制字符串。 它将被扫描为插入和相应的格式。 格式字符串类似于运行时函数`printf`样式格式字符串，只不过它允许以任意顺序插入参数。

*阿格斯*<br/>
指向参数列表的指针。

### <a name="remarks"></a>备注

以将数据`vsprintf_s`格式化为 C 样式字符数组的方式将格式化字符串`CStringT`和参数的变量列表写入字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a>CStringT：获取环境变量

将字符串设置为指定环境变量的值。

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>参数

*pszVar*<br/>
指向指定环境变量的 null 端接字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

从调用进程的环境块检索指定变量的值。 该值以 null 终止字符串的形式出现。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a>CStringT：插入

在字符串中的给定索引上插入单个字符或子字符串。

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
将发生插入的字符的索引。

*psz*<br/>
指向要插入的子字符串的指针。

*ch*<br/>
要插入的字符。

### <a name="return-value"></a>返回值

已更改字符串的长度。

### <a name="remarks"></a>备注

*iIndex*参数标识将移动的第一个字符，以便为字符或子字符串腾出空间。 如果*nIndex*为零，则插入将在整个字符串之前进行。 如果*nIndex*高于字符串的长度，则函数将串联当前字符串和*ch*或*psz*提供的新材料。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a>CStringT：左

从该`CStringT`对象中提取最左侧的*nCount*字符，并返回提取的子字符串的副本。

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>参数

*nCount*<br/>
从此 `CStringT` 对象中提取的字符的数量。

### <a name="return-value"></a>返回值

包含指定范围内的字符的副本的 `CStringT` 对象。 返回的 `CStringT` 对象可以为空。

### <a name="remarks"></a>备注

如果*nCount*超过字符串长度，则提取整个字符串。 `Left` 类似于 Basic `Left` 函数。

对于多字节字符集 （MBCS），nCount 将每个 8 位序列视为字符，以便*nCount*将多字节字符数乘以 2。 *nCount*

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a>CStringT：：加载字符串

将*由 nID*标识的 Windows 字符串资源读取`CStringT`到现有对象中。

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
模块实例的句柄。

*nID*<br/>
Windows 字符串资源 ID。

*w语言ID*<br/>
字符串资源的语言。

### <a name="return-value"></a>返回值

如果资源负载成功，则非零;否则 0。

### <a name="remarks"></a>备注

使用指定的语言 *（w语言*） 从指定的模块 *（hA）* 加载字符串资源 （*nID*）。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a>CStringT：：制作下

将`CStringT`对象转换为小写字符串。

```
CStringT& MakeLower();
```

### <a name="return-value"></a>返回值

生成的小写字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a>CStringT：：使反向

反转`CStringT`对象中字符的顺序。

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>返回值

生成的反向字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a>CStringT：：制作上

将`CStringT`对象转换为大写字符串。

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>返回值

生成的大写字符串。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a>CStringT：中

从该`CStringT`对象中提取长度*nCount*字符的子字符串，从位置*iFirst*开始（基于零）。

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>参数

*i第一*<br/>
此`CStringT`对象中第一个字符的零点索引，该索引将包含在提取的子字符串中。

*nCount*<br/>
从此 `CStringT` 对象中提取的字符的数量。 如果未提供此参数，则提取字符串的其余部分。

### <a name="return-value"></a>返回值

包含指定范围内的字符的副本的 `CStringT` 对象。 请注意，返回`CStringT`的对象可能为空。

### <a name="remarks"></a>备注

函数返回提取的子字符串的副本。 `Mid`与基本中间函数类似（Basic 中的索引是一个基的除外）。

对于多字节字符集 *（MBCS），nCount*表示每个 8 位字符;也就是说，一个多字节字符中的引线和跟踪字节计为两个字符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a>弦乐：：OemToansi

将此`CStringT`对象中的所有字符从 OEM 字符集转换为 ANSI 字符集。

```
void OemToAnsi();
```

### <a name="remarks"></a>备注

如果定义了_UNICODE，则此功能不可用。

### <a name="example"></a>示例

请参阅[CStringT 示例：：AnsiToOem](#ansitooem)。

## <a name="cstringtoperator-"></a><a name="operator_eq"></a>CStringT：：运算符 |

为字符串分配一个新值。

```
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);

CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>参数

*斯特斯尔克*<br/>
要`CStringT`分配给此字符串的 。

*Str*<br/>
对 `CThisSimpleString` 对象的引用。

*bMFCDLL*<br/>
指定项目是否为 MFC DLL 的布尔。

*BaseType*<br/>
字符串基类型。

*var*<br/>
要分配给此字符串的变体对象。

*ch*<br/>
要分配给字符串的 ANSI 或 Unicode 字符。

*皮茨斯尔克*<br/>
指向要分配的原始字符串的指针。

### <a name="remarks"></a>备注

赋值运算符接受另`CStringT`一个对象、字符指针或单个字符。 您应该注意，每当使用此运算符时，都会发生内存异常，因为可以分配新的存储。

有关 的信息`CThisSimpleString`，请参阅[CStringT：：CStringT](#cstringt)的备注部分。

> [!NOTE]
> 尽管可以创建`CStringT`包含嵌入的空字符的实例，但我们建议不要这样做。 对`CStringT`包含嵌入的空字符的对象调用方法和运算符可以产生意外的结果。

## <a name="cstringtoperator-"></a><a name="operator_add"></a>CStringT：运算符 |

串联两个字符串或一个字符和一个字符串。

```
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>参数

*ch1*<br/>
要与字符串串联的 ANSI 或 Unicode 字符。

*ch2*<br/>
要与字符串串联的 ANSI 或 Unicode 字符。

*str1*<br/>
与`CStringT`字符串或字符串联的 。

*str2*<br/>
与`CStringT`字符串或字符串联的 。

*psz1*<br/>
指向 null 端接字符串的指针，用于与字符串或字符串联。

*psz2*<br/>
指向字符串的指针，用于与字符串或字符串联。

### <a name="remarks"></a>备注

`CStringT::operator+`函数有七种重载形式。 第一个版本串联两个现有`CStringT`对象。 接下来的两个连接了一个`CStringT`对象和一个 null 终止的字符串。 接下来的两个连接了一个`CStringT`对象和一个ANSI字符。 最后两个连接对象`CStringT`和 Unicode 字符。

> [!NOTE]
> 尽管可以创建`CStringT`包含嵌入的空字符的实例，但我们建议不要这样做。 对`CStringT`包含嵌入的空字符的对象调用方法和运算符可以产生意外的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a>CStringT：：运算符 |

将字符串联到字符串的末尾。

```
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```

### <a name="parameters"></a>参数

*Str*<br/>
对 `CThisSimpleString` 对象的引用。

*bMFCDLL*<br/>
指定项目是否为 MFC DLL 的布尔。

*BaseType*<br/>
字符串基类型。

*var*<br/>
要串联到此字符串的变体对象。

*ch*<br/>
要与字符串串联的 ANSI 或 Unicode 字符。

*皮茨斯尔克*<br/>
指向要串联的原始字符串的指针。

*斯特斯尔克*<br/>
要`CStringT`串联到此字符串。

### <a name="remarks"></a>备注

运算符接受另一`CStringT`个对象、字符指针或单个字符。 您应该注意，每当使用此串联运算符时，都可能发生内存异常，因为可以为添加到此`CStringT`对象的字符分配新的存储。

有关 的信息`CThisSimpleString`，请参阅[CStringT：：CStringT](#cstringt)的备注部分。

> [!NOTE]
> 尽管可以创建`CStringT`包含嵌入的空字符的实例，但我们建议不要这样做。 对`CStringT`包含嵌入的空字符的对象调用方法和运算符可以产生意外的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a>CStringT：：运算符 |

确定两个字符串在逻辑上是否相等。

```
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>参数

*ch1*<br/>
用于比较的 ANSI 或 Unicode 字符。

*ch2*<br/>
用于比较的 ANSI 或 Unicode 字符。

*str1*<br/>
A`CStringT`表示比较。

*str2*<br/>
A`CStringT`表示比较。

*psz1*<br/>
指向 null 终止字符串的指针，用于比较。

*psz2*<br/>
指向 null 终止字符串的指针，用于比较。

### <a name="remarks"></a>备注

测试左侧的字符串或字符是否等于右侧的字符串或字符，并相应地返回 TRUE 或 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a>CStringT：：操作员！]

确定两个字符串在逻辑上是否不相等。

```
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>参数

*ch1*<br/>
要与字符串串联的 ANSI 或 Unicode 字符。

*ch2*<br/>
要与字符串串联的 ANSI 或 Unicode 字符。

*str1*<br/>
A`CStringT`表示比较。

*str2*<br/>
A`CStringT`表示比较。

*psz1*<br/>
指向 null 终止字符串的指针，用于比较。

*psz2*<br/>
指向 null 终止字符串的指针，用于比较。

### <a name="remarks"></a>备注

测试左侧的字符串或字符是否不等于右侧的字符串或字符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a>CStringT：：运算符&lt;

确定运算符左侧的字符串是否小于右侧的字符串。

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>参数

*str1*<br/>
A`CStringT`表示比较。

*str2*<br/>
A`CStringT`表示比较。

*psz1*<br/>
指向 null 终止字符串的指针，用于比较。

*psz2*<br/>
指向 null 终止字符串的指针，用于比较。

### <a name="remarks"></a>备注

字符串之间的字典比较，按字符进行，直到：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 如果找到的所有字符完全相同且字符串的字符数也相同，则这两个字符串视为相等。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a>CStringT：：运算符&gt;

确定运算符左侧的字符串是否大于右侧的字符串。

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>参数

*str1*<br/>
A`CStringT`表示比较。

*str2*<br/>
A`CStringT`表示比较。

*psz1*<br/>
指向 null 终止字符串的指针，用于比较。

*psz2*<br/>
指向 null 终止字符串的指针，用于比较。

### <a name="remarks"></a>备注

字符串之间的字典比较，按字符进行，直到：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a>CStringT：：运算符&lt;=

确定运算符左侧的字符串是否小于或等于右侧的字符串。

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>参数

*str1*<br/>
A`CStringT`表示比较。

*str2*<br/>
A`CStringT`表示比较。

*psz1*<br/>
指向 null 终止字符串的指针，用于比较。

*psz2*<br/>
指向 null 终止字符串的指针，用于比较。

### <a name="remarks"></a>备注

字符串之间的字典比较，按字符进行，直到：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a>CStringT：：运算符&gt;=

确定运算符左侧的字符串是大于还是等于右侧的字符串。

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>参数

*str1*<br/>
A`CStringT`表示比较。

*str2*<br/>
A`CStringT`表示比较。

*psz1*<br/>
指向字符串的指针进行比较。

*psz2*<br/>
指向字符串的指针进行比较。

### <a name="remarks"></a>备注

字符串之间的字典比较，按字符进行，直到：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a>CStringT：：删除

从字符串中删除指定字符的所有实例。

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>参数

*ch 删除*<br/>
要从字符串中删除的字符。

### <a name="return-value"></a>返回值

从字符串中删除的字符计数。 如果字符串未更改，则为零。

### <a name="remarks"></a>备注

字符的比较区分大小写。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a>CStringT：替换

有 两个版本`Replace`。第一个版本使用另一个子字符串替换子字符串的一个或多个副本。 两个子字符串都是 null 终止的。 第二个版本使用另一个字符替换字符的一个或多个副本。 两个版本都对存储在 中的`CStringT`字符数据进行操作。

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>参数

*pszOld*<br/>
指向 null 终止字符串的指针，要替换为*pszNew*。

*pszNew*<br/>
指向 null 终止字符串的指针，该指针替换*pszOld*。

*chOld*<br/>
要替换为*chNew*的字符 。

*ch New*<br/>
字符替换*chOld*。

### <a name="return-value"></a>返回值

返回字符或子字符串的替换实例数，如果字符串未更改，则返回零。

### <a name="remarks"></a>备注

`Replace`可以更改字符串长度，因为*pszNew*和*pszOld*不必具有相同的长度，并且旧子字符串的几个副本可以更改为新的子字符串。 函数执行区分大小写的匹配。

实例的示例`CStringT`包括`CString`、`CStringA`和`CStringW`。

对于`CStringA` `Replace` ，使用 ANSI 或多字节 （MBCS） 字符。 对于`CStringW` `Replace` ，使用宽字符。

对于`CString`，根据是否定义了下表中的常量，在编译时选择了字符数据类型。

|定义的常量|字符数据类型|
|----------------------|-------------------------|
|_UNICODE|宽字符|
|_MBCS|多字节字符|
|Neither|单字节字符|
|推送、请求和匿名|Undefined|

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a>CStringT：：反向查找

搜索此`CStringT`对象以搜索字符的最后一个匹配项。

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>参数

*ch*<br/>
要搜索的字符。

### <a name="return-value"></a>返回值

此`CStringT`对象中最后一个字符与请求的字符匹配的零基索引，如果未找到该字符，则为 -1。

### <a name="remarks"></a>备注

该函数类似于运行时函数`strrchr`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a>CStringT：右

从该`CStringT`对象中提取最后一个（即最右 *）nCount*字符，并返回提取的子字符串的副本。

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>参数

*nCount*<br/>
从此 `CStringT` 对象中提取的字符的数量。

### <a name="return-value"></a>返回值

包含指定范围内的字符的副本的 `CStringT` 对象。 请注意，返回`CStringT`的对象可以为空。

### <a name="remarks"></a>备注

如果*nCount*超过字符串长度，则提取整个字符串。 `Right`与基本`Right`函数类似（Basic 中的索引为零除外）。

对于多字节字符集 *（MBCS），nCount*表示每个 8 位字符;也就是说，一个多字节字符中的引线和跟踪字节计为两个字符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a>CStringT：：SetSysString

重新分配*pbstr*指向的 BSTR，并将`CStringT`对象的内容复制到其中，包括 NULL 字符。

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>参数

*pbstr*<br/>
指向字符串的指针。

### <a name="return-value"></a>返回值

新字符串。

### <a name="remarks"></a>备注

根据`CStringT`对象的内容 *，pbstr*引用的 BSTR 值可能会更改。 如果内存不足，`CMemoryException`则函数将引发 。

此函数通常用于更改通过引用传递的用于自动化的字符串的值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a>CStringT：：范围排除

从字符串中提取字符，从第一个字符开始，这些字符不在*pszCharSet*标识的字符集中。

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>参数

*pszCharSet*<br/>
被解释为一组字符的字符串。

### <a name="return-value"></a>返回值

包含字符串中不在*pszCharSet*中的字符的子字符串，从字符串中的第一个字符开始，到在字符串中找到的第一个字符结束，该字符也位于*pszCharSet*中（即，从字符串中的第一个字符开始，最多到但不包括找到*pszCharSet*的字符串中的第一个字符）。 如果在字符串中找不到*pszCharSet*中的字符，则返回整个字符串。

### <a name="remarks"></a>备注

`SpanExcluding`从*pszCharSet*提取并返回字符第一次出现之前的所有字符（换句话说，不会返回*pszCharSet*中的字符及其后的所有字符）。 如果在字符串中找不到*pszCharSet*中的字符，则`SpanExcluding`返回整个字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a>CStringT：：跨栏包括

从字符串中提取字符，从第一个字符开始，这些字符位于*pszCharSet*标识的字符集中。

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>参数

*pszCharSet*<br/>
被解释为一组字符的字符串。

### <a name="return-value"></a>返回值

包含*pszCharSet*中字符串中的字符的子字符串，从字符串中的第一个字符开始，到在字符串中找不到不在*pszCharSet*中的字符时结束。 `SpanIncluding`如果字符串中的第一个字符不在指定的集中，则返回一个空子字符串。

### <a name="remarks"></a>备注

如果字符串的第一个字符不在字符集中，则`SpanIncluding`返回一个空字符串。 否则，它将返回集中的连续字符序列。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a>CStringT：：令牌化

在目标字符串中查找下一个令牌

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>参数

*pszTokens*<br/>
包含令牌分隔符的字符串。 这些分隔符的顺序并不重要。

*i 开始*<br/>
开始搜索的零基索引。

### <a name="return-value"></a>返回值

包含`CStringT`当前令牌值的对象。

### <a name="remarks"></a>备注

函数`Tokenize`在目标字符串中查找下一个令牌。 *pszTokens*中的字符集指定要找到的令牌的可能分隔符。 对函数的每个调用`Tokenize`从*iStart*开始，跳过前导分隔符，并返回包含`CStringT`当前令牌的对象，该标记是下一个分隔符字符的字符串。 *iStart*的值将更新为结束分隔符字符之后的位置，如果达到字符串的末尾，则为 -1。 通过一系列调用`Tokenize`，可以使用*iStart*跟踪要读取下一个令牌在字符串中的位置，从而从目标字符串的其余部分中分解更多令牌。 当没有更多的令牌时，函数将返回一个空字符串 *，iStart*将设置为 -1。

与 CRT 标记strtok_s等函数不同[，_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)等函数`Tokenize`不会修改目标字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>备注

此示例的输出如下所示：

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a>CStringT：修剪

修剪字符串中前导字符和尾随字符。

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>参数

*chTarget*<br/>
要修剪的目标字符。

*pszTargets*<br/>
指向包含要修剪的目标字符的字符串的指针。 *pszTarget*中字符的所有前导和尾随事件都将从对象中`CStringT`修剪。

### <a name="return-value"></a>返回值

返回修剪的字符串。

### <a name="remarks"></a>备注

删除以下一项的所有前导和尾随事件：

- *chTarget*指定的字符。

- 在*pszTargets*指定的字符串中找到的所有字符。

- 空白。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>备注

此示例的输出如下所示：

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a>CStringT：：修剪左

从字符串修剪前导字符。

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>参数

*chTarget*<br/>
要修剪的目标字符。

*pszTargets*<br/>
指向包含要修剪的目标字符的字符串的指针。 *pszTarget*中字符的所有前导匹配项都将从对象中`CStringT`修剪。

### <a name="return-value"></a>返回值

生成的修剪字符串。

### <a name="remarks"></a>备注

删除以下一项的所有前导和尾随事件：

- *chTarget*指定的字符。

- 在*pszTargets*指定的字符串中找到的所有字符。

- 空白。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a>CStringT：：修剪权

从字符串中修剪尾随字符。

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>参数

*chTarget*<br/>
要修剪的目标字符。

*pszTargets*<br/>
指向包含要修剪的目标字符的字符串的指针。 *pszTarget*中字符的所有尾随发生都将从`CStringT`对象中修剪。

### <a name="return-value"></a>返回值

返回包含`CStringT`修剪的字符串的对象。

### <a name="remarks"></a>备注

删除以下一个的尾随事件：

- *chTarget*指定的字符。

- 在*pszTargets*指定的字符串中找到的所有字符。

- 空白。

版本`CStringT& TrimRight(XCHAR chTarget)`接受一个字符参数，并从`CStringT`字符串数据末尾删除该字符的所有副本。 它从字符串的末尾开始，朝向前面工作。 当它找到不同的字符或字符数据用完时`CSTringT`，它将停止。

版本`CStringT& TrimRight(PCXSTR pszTargets)`接受一个 null 终止的字符串，其中包含要搜索的所有不同字符。 它删除`CStringT`对象中这些字符的所有副本。 它从字符串的末尾开始，朝向前面工作。 当它找到不在目标字符串中的字符或字符数据用完时`CStringT`，它将停止。 它不尝试将整个目标字符串匹配到 的末尾的`CStringT`子字符串。

该`CStringT& TrimRight()`版本不需要参数。 它会从`CStringT`字符串的末尾修剪任何尾随的空白字符。 空白字符可以是换行符、空格或制表符。

-

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)
