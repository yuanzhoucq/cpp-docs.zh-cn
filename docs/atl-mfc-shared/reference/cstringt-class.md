---
title: "CStringT 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d3b718249603c34d5a9a13eec966b586151f2e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cstringt-class"></a>CStringT 类
此类表示`CStringT`对象。  
  
## <a name="syntax"></a>语法  
  
```  
 
template<typename BaseType, class StringTraits>  
class CStringT :   
public CSimpleStringT<BaseType,
                      _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                      ::c_bIsMFCDLLTraits>  
 
```  
  
#### <a name="parameters"></a>参数  
 `BaseType`  
 此字符串类字符类型。 可以是以下各项之一：  
  
- `char`（对于 ANSI 字符字符串）。  
  
- `wchar_t`（对于 Unicode 字符串）。  
  
- **TCHAR** （针对 ANSI 和 Unicode 字符串）。  
  
 `StringTraits`  
 确定此字符串类是否需要 C 运行时 (CRT) 库支持和字符串资源的位置。 可以是以下各项之一：  
  
- **StrTraitATL < wchar_t** &#124;`char` &#124;**TCHAR、 ChTraitsCRT < wchar_t** &#124;`char` &#124;**TCHAR >>**  
  
     类要求 CRT 支持并搜索由指定的模块中的资源字符串`m_hInstResource`（应用程序的模块类的成员）。  
  
- **StrTraitATL < wchar_t** &#124;`char` &#124;**TCHAR、 ChTraitsOS < wchar_t** &#124;`char` &#124;**TCHAR >>**  
  
     类不需要 CRT 支持和搜索由指定的模块中的资源字符串`m_hInstResource`（应用程序的模块类的成员）。  
  
- **StrTraitMFC < wchar_t** &#124;`char` &#124;**TCHAR、 ChTraitsCRT < wchar_t** &#124;`char` &#124;**TCHAR >>**  
  
     类要求 CRT 支持并使用标准 MFC 搜索算法的资源字符串的搜索。  
  
- **StrTraitMFC < wchar_t** &#124;`char` &#124;**TCHAR、 ChTraitsOS < wchar_t** &#124;`char` &#124;**TCHAR >>**  
  
     类不需要 CRT 支持并使用标准 MFC 搜索算法的资源字符串的搜索。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CStringT::CStringT](#cstringt)|构造`CStringT`以各种方式的对象。|  
|[CStringT:: ~ CStringT](#_dtorcstringt)|销毁 `CStringT` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CStringT::AllocSysString](#allocsysstring)|分配`BSTR`从`CStringT`数据。|  
|[CStringT::AnsiToOem](#ansitooem)|可以从 OEM 字符集中的 ANSI 字符集的就地转换。|  
|[CStringT::AppendFormat](#appendformat)|将格式化的数据追加到现有`CStringT`对象。|  
|[CStringT::Collate](#collate)|比较两个字符串 （使用特定于区域设置信息中的区分大小写）。|  
|[CStringT::CollateNoCase](#collatenocase)|比较两个字符串 （使用特定于区域设置信息中的区分大小写）。|  
|[CStringT::Compare](#compare)|比较两个字符串 （区分大小写）。|  
|[CStringT::CompareNoCase](#comparenocase)|比较两个字符串 （不区分大小写）。|  
|[CStringT::Delete](#delete)|从字符串中删除一个字符。|  
|[CStringT::Find](#find)|查找的字符或在较大字符串内的子字符串。|  
|[CStringT::FindOneOf](#findoneof)|查找一组从第一个匹配的字符。|  
|[CStringT::Format](#format)|设置为字符串的格式`sprintf`未。|  
|[CStringT::FormatMessage](#formatmessage)|格式化消息字符串。|  
|[CStringT::FormatMessageV](#formatmessagev)|格式化消息字符串使用变量自变量列表。|  
|[CStringT::FormatV](#formatv)|设置使用变量参数列表的字符串的格式。|  
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|将字符串设置为指定的环境变量的值。|  
|[CStringT::Insert](#insert)|字符串内的给定索引处插入单个字符或子字符串。|  
|[CStringT::Left](#left)|提取字符串的左侧的部分。|  
|[CStringT::LoadString](#loadstring)|加载现有`CStringT`从 Windows 资源的对象。|  
|[CStringT::MakeLower](#makelower)|将转换为小写字符此字符串中的所有字符。|  
|[CStringT::MakeReverse](#makereverse)|反转字符串。|  
|[CStringT::MakeUpper](#makeupper)|将转换为大写字符此字符串中的所有字符。|  
|[CStringT::Mid](#mid)|提取字符串的中间部分。|  
|[CStringT::OemToAnsi](#oemtoansi)|可以从 ANSI 字符集中的 OEM 字符集就地转换。|  
|[CStringT::Remove](#remove)|删除指示字符串中的字符。|  
|[CStringT::Replace](#replace)|替换指示字符替换为其他字符。|  
|[CStringT::ReverseFind](#reversefind)|查找在较大的字符串; 内的字符启动从端。|  
|[CStringT::Right](#right)|提取字符串的右侧部分。|  
|[CStringT::SetSysString](#setsysstring)|设置现有`BSTR`对象从所有数据`CStringT`对象。|  
|[CStringT::SpanExcluding](#spanexcluding)|从开头的第一个字符，不在组由标识的字符的字符串中提取字符`pszCharSet`。|  
|[CStringT::SpanIncluding](#spanincluding)|提取子字符串，其中包含仅在一组字符。|  
|[CStringT::Tokenize](#tokenize)|提取目标字符串中指定令牌。|  
|[CStringT::Trim](#trim)|修剪所有前导和尾随空白字符，从字符串。|  
|[CStringT::TrimLeft](#trimleft)|修剪前导空白字符的字符串。|  
|[CStringT::TrimRight](#trimright)|修剪尾随空白字符的字符串中。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](#operator_eq)|将新值赋给`CStringT`对象。|  
|[CStringT::operator +](#operator_add)|连接两个字符串或字符和字符串。|  
|[CStringT::operator + =](#operator_add_eq)|连接到现有字符串的末尾的新字符串。|  
|[CStringT::operator = =](#operator_eq_eq)|确定两个字符串是否逻辑上相等。|  
|[CStringT::operator ！ =](#operator_neq)|确定两个字符串是否以逻辑方式不相等。|  
|[CStringT::operator&lt;](#operator_lt)|确定运算符左侧的字符串是否小于右侧的字符串。|  
|[CStringT::operator&gt;](#operator_gt)|确定运算符左侧的字符串是否大于右侧的字符串。|  
|[CStringT::operator&lt;=](#operator_lt_eq)|确定运算符左侧的字符串是否小于或等于右侧的字符串。|  
|[CStringT::operator&gt;=](#operator_gt_eq)|确定运算符左侧的字符串是否大于或等于右侧的字符串。|  
  
## <a name="remarks"></a>备注  
 `CStringT`继承自[CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)。 高级的功能，如字符操作、 排序和搜索，实现通过`CStringT`。  
  
> [!NOTE]
> `CStringT`对象是能够引发异常。 发生这种情况时`CStringT`对象出于任何原因耗尽内存。  
  
 A`CStringT`对象包含的字符长度可变的序列。 `CStringT`提供了函数和运算符使用语法类似于 Basic。 串联运算符和比较运算符，以及简化的内存管理，使`CStringT`更轻松地使用比普通字符数组的对象。  
  
> [!NOTE]
>  但也可以创建`CStringT`包含的实例嵌入的空字符，我们建议对其。 在调用方法和运算符`CStringT`包含嵌入的空字符的对象可能会产生意外的结果。  
  
 通过使用不同的组合`BaseType`和`StringTraits`参数，`CStringT`对象可以在以下类型，它们是返回已预定义的 ATL 库。  
  
 如果使用 ATL 应用程序中：  
  
 `CString``CStringA`，和`CStringW`导出从 MFC DLL (MFC90。DLL)，永远不会从用户 Dll。 这样做是为了防止`CStringT`从被多次定义。  
  
> [!NOTE]
>  如果你的代码包含中所述的链接器错误的解决方法[Linking Errors When You Import CString-Derived 类"(Q309801)](https://support.microsoft.com/help/309801/you-may-receive-an-lnk2019-error-message-when-you-build-a-visual-c-200)，应删除该代码。 不再需要此方法。  
  
 以下字符串类型是基于 MFC 的应用程序中可用：  
  
|CStringT 类型|声明|  
|-------------------|-----------------|  
|`CStringA`|ANSI 字符键入 CRT 支持的字符串。|  
|`CStringW`|Unicode 字符键入 CRT 支持的字符串。|  
|`CString`|具有 CRT 支持 ANSI 和 Unicode 字符类型。|  
  
 以下字符串中可用的类型项目的位置**ATL_CSTRING_NO_CRT**定义：  
  
|CStringT 类型|声明|  
|-------------------|-----------------|  
|**CAtlStringA**|ANSI 字符键入没有 CRT 支持的字符串。|  
|**CAtlStringW**|Unicode 字符键入没有 CRT 支持的字符串。|  
|**CAtlString**|没有 CRT 支持 ANSI 和 Unicode 字符类型。|  
  
 以下字符串中可用的类型项目的位置**ATL_CSTRING_NO_CRT**未定义：  
  
|CStringT 类型|声明|  
|-------------------|-----------------|  
|**CAtlStringA**|ANSI 字符键入 CRT 支持的字符串。|  
|**CAtlStringW**|Unicode 字符键入 CRT 支持的字符串。|  
|**CAtlString**|具有 CRT 支持 ANSI 和 Unicode 字符类型。|  
  
 `CString`对象还具有以下特征：  
  
- `CStringT`串联操作后，对象可能会增长。  
  
- `CStringT`对象遵循"值语义"。 想一想`CStringT`对象为实际字符串，而不是指向字符串的指针。  
  
-   你可以自由地替换`CStringT`对象`PCXSTR`函数自变量。  
  
-   字符串缓冲区的自定义的内存管理。 有关详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="cstringt-predefined-types"></a>CStringT 预定义的类型  
 因为`CStringT`使用模板自变量来定义字符类型 (任一[wchar_t](../../c-runtime-library/standard-types.md)或[char](../../c-runtime-library/standard-types.md)) 支持，方法参数类型可以是复杂的时段。 若要简化此问题，一组预定义的类型定义和使用整个`CStringT`类。 下表列出了各种类型：  
  
|name|描述|  
|----------|-----------------|  
|`XCHAR`|单个字符 (请`wchar_t`或`char`) 具有相同的字符类型，作为`CStringT`对象。|  
|**YCHAR**|单个字符 (请`wchar_t`或`char`) 通过相反的字符类型，作为`CStringT`对象。|  
|`PXSTR`|指向字符字符串的指针 (或者`wchar_t`或`char`) 具有相同的字符类型，作为`CStringT`对象。|  
|**PYSTR**|指向字符字符串的指针 (或者`wchar_t`或`char`) 通过相反的字符类型，作为`CStringT`对象。|  
|`PCXSTR`|指向的指针**const**字符字符串 (请`wchar_t`或`char`) 具有相同的字符类型，作为`CStringT`对象。|  
|**PCYSTR**|指向的指针**const**字符字符串 (请`wchar_t`或`char`) 通过相反的字符类型，作为`CStringT`对象。|  
  
> [!NOTE]
>  以前使用未记录的方法的代码`CString`(如**AssignCopy**) 必须使用以下有案可稽的方法的代码的替换`CStringT`(如`GetBuffer`或`ReleaseBuffer`)。 这些方法均继承于`CSimpleStringT`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)  
  
 `CStringT`  
  
## <a name="requirements"></a>惠?  
  
|Header|用于|  
|------------|-------------|  
|cstringt.h|仅 MFC 字符串对象|  
|atlstr.h|非 MFC 字符串对象|  
  
##  <a name="allocsysstring"></a>CStringT::AllocSysString  
 分配类型的自动化兼容字符串`BSTR`，并将复制的内容`CStringT`到其中，包括终止 null 字符的对象。  
  
```  
BSTR AllocSysString() const;  
```  
  
### <a name="return-value"></a>返回值  
 新分配的字符串。  
  
### <a name="remarks"></a>备注  
 在 MFC 程序中， [CMemoryException 类](../../mfc/reference/cmemoryexception-class.md)如果存在内存不足，则会引发。 ATL 程序中[CAtlException](../../atl/reference/catlexception-class.md)引发。 此函数通常用于自动化返回的字符串。  
  

 通常情况下，如果此字符串传递给 COM 函数为 [in] 参数，则这要求调用方释放字符串。 这可以通过使用[SysFreeString](https://msdn.microsoft.com/library/windows/desktop/ms221481.aspx)，如 Windows SDK 中所述。 有关详细信息，请参阅[Allocating 和释放内存可供 BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)。  
  
 有关 Windows 中的 OLE 分配函数的详细信息，请参阅[SysAllocString](https://msdn.microsoft.com/library/windows/desktop/ms221458.aspx) Windows SDK 中。  

  
### <a name="example"></a>示例  
 以下示例演示了 `CStringT::AllocSysString` 的用法。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]  
  
##  <a name="ansitooem"></a>CStringT::AnsiToOem  
 将在此的所有字符都转换`CStringT`ANSI 字符集为 OEM 字符集中的对象。  
  
```  
void AnsiToOem();
```  
  
### <a name="remarks"></a>备注  
 该函数不可用如果`_UNICODE`定义。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]  
  
##  <a name="appendformat"></a>CStringT::AppendFormat  
 将格式化的数据追加到现有`CStringT`对象。  
  
```  
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```  
  
### <a name="parameters"></a>参数  
 `pszFormat`  
 格式控件字符串。  
  
 `nFormatID`  
 包含格式控件字符串的字符串资源标识符。  
  
 `argument`  
 可选参数。  
  
### <a name="remarks"></a>备注  
 此函数格式，并将一系列中的字符和值追加`CStringT`。 每个可选参数 （如果有） 转换，并根据相应的格式规范中追加`pszFormat`或从所标识的字符串资源`nFormatID`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]  
  
##  <a name="collate"></a>CStringT::Collate  
 比较两个字符串使用一般文本函数`_tcscoll`。  
  
```  
int Collate(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 用于比较的其他字符串。  
  
### <a name="return-value"></a>返回值  
 零; 如果字符串相同，如果此为 < 0`CStringT`对象是小于`psz`，或 > 0，如果此`CStringT`对象是否大于`psz`。  
  
### <a name="remarks"></a>备注  
 一般文本函数`_tcscoll`，TCHAR 中定义。H，映射为`strcoll`， `wcscoll`，或`_mbscoll`，取决于在编译时定义的字符集。 每个函数执行区分大小写的字符串比较根据代码页当前正在使用。 有关详细信息，请参阅[strcoll、 wcscoll、 _mbscoll、 _strcoll_l、 _wcscoll_l、 _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。  
  
##  <a name="collatenocase"></a>CStringT::CollateNoCase  
 比较两个字符串使用一般文本函数`_tcscoll`。  
  
```  
int CollateNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 用于比较的其他字符串。  
  
### <a name="return-value"></a>返回值  
 零字符串是否相同 （忽略大小写），如果此为 < 0`CStringT`对象是小于`psz`（忽略大小写），或 > 0，如果此`CStringT`对象是否大于`psz`（忽略大小写）。  
  
### <a name="remarks"></a>备注  
 一般文本函数`_tcscoll`，TCHAR 中定义。H，映射为`stricoll`， `wcsicoll`，或`_mbsicoll`，取决于在编译时定义的字符集。 每个函数根据当前正在使用的代码页执行的字符串，不区分大小写的比较。 有关详细信息，请参阅[strcoll、 wcscoll、 _mbscoll、 _strcoll_l、 _wcscoll_l、 _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]  
  
##  <a name="compare"></a>CStringT::Compare  
 比较两个字符串 （区分大小写）。  
  
```  
int Compare(PCXSTR psz) const; 
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 用于比较的其他字符串。  
  
### <a name="return-value"></a>返回值  
 零; 如果字符串相同，如果此为 < 0`CStringT`对象是小于`psz`，或 > 0，如果此`CStringT`对象是否大于`psz`。  
  
### <a name="remarks"></a>备注  
 一般文本函数`_tcscmp`，TCHAR 中定义。H，映射为`strcmp`， `wcscmp`，或`_mbscmp`，取决于在编译时定义的字符集。 每个函数执行区分大小写的字符串比较，并不受区域设置。 有关详细信息，请参阅[strcmp、 wcscmp、 _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)。  
  
 如果字符串包含嵌入的 null，出于比较的字符串被视为在第一个嵌入的 null 字符处截断。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CStringT::Compare` 的用法。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]  
  
##  <a name="comparenocase"></a>CStringT::CompareNoCase  
 比较两个字符串 （不区分大小写）。  
  
```  
int CompareNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 用于比较的其他字符串。  
  
### <a name="return-value"></a>返回值  
 零字符串是否相同 （忽略大小写），< 0，如果此`CStringT`对象是小于`psz`（忽略大小写），或 > 0，如果此`CStringT`对象是否大于`psz`（忽略大小写）。  
  
### <a name="remarks"></a>备注  
 一般文本函数`_tcsicmp`，TCHAR 中定义。H，映射为`_stricmp`，`_wcsicmp`或`_mbsicmp`，取决于在编译时定义的字符集。 每个函数执行不区分大小写的字符串比较。 取决于比较`LC_CTYPE`方面的区域设置而不是`LC_COLLATE`。 有关详细信息，请参阅[_stricmp、 _wcsicmp、 _mbsicmp、 _stricmp_l、 _wcsicmp_l、 _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]  
  
##  <a name="cstringt"></a>CStringT::CStringT  
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
 `pch`  
 指向字符长度的数组的指针`nLength`、 不以 null 结尾。  
  
 `nLength`  
 中的字符数的计数`pch`。  
  
 `ch`  
 单个字符。  
  
 `pszSrc`  
 以 null 结尾的字符串复制到此`CStringT`对象。  
  
 `pStringMgr`  
 指向的内存管理器的`CStringT`对象。 有关详细信息`IAtlStringMgr`和内存管理`CStringT`，请参阅[CStringT 使用内存管理](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
 `strSrc`  
 现有`CStringT`要复制到此对象`CStringT`对象。 有关详细信息`CThisString`和`CThisSimpleString`，请参阅备注部分。  
  
 `varSrc`  
 要复制到此变体对象`CStringT`对象。  
  
 `BaseType`  
 此字符串类字符类型。 可以是以下各项之一：  
  
 `char`（对于 ANSI 字符字符串）。  
  
 `wchar_t`（对于 Unicode 字符串）。  
  
 `TCHAR`（针对 ANSI 和 Unicode 字符串）。  
  
 `bMFCDLL`  
 布尔值，该值指定该项目是 MFC DLL (TRUE) 还是不 (FALSE)。  
  
 `SystemString`  
 必须是`System::String`，并且必须使用 /clr 编译项目。  
  
 `pString`  
 句柄`CStringT`对象。  
  
### <a name="remarks"></a>备注  
 因为构造函数将输入的数据复制到新的已分配存储，你应注意异常可能会导致该内存。 请注意，某些这些构造函数成为转换函数。 此选项，可以替代，例如，`LPTSTR`其中`CStringT`预期对象。  
  
- `CStringT`( `LPCSTR` `lpsz` ): 构造 Unicode`CStringT`从 ANSI 字符串。 你还可以使用此构造函数中加载字符串资源，如下面的示例中所示。  
  
- `CStringT(``LPCWSTR` `lpsz` ): 构造`CStringT`从 Unicode 字符串。  
  
- `CStringT`( `const unsigned char*` `psz` ): 使你可以构造`CStringT`从指针到`unsigned char`。  
  
> [!NOTE]
>  定义**_CSTRING_DISABLE_NARROW_WIDE_CONVERSION**宏来关闭之间的隐式字符串转换[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]和[!INCLUDE[TLA#tla_unicode](../../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]字符串。 从编译构造函数来支持转换中排除宏。  
  
 请注意，`strSrc`参数可以是`CStringT`或`CThisSimpleString`对象。 有关`CStringT`，使用其默认实例化之一 ( `CString`， `CStringA`，或`CStringW`); 对于`CThisSimpleString`，使用`this`指针。 `CThisSimpleString`实例声明[CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)，即具有比少于内置功能的较小字符串类`CStringT`类。  
  
 重载运算符`CSimpleStringT<>&()`构造`CStringT`对象`CSimpleStringT`声明。  
  
> [!NOTE]
>  但也可以创建`CStringT`包含的实例嵌入的空字符，我们建议对其。 在调用方法和运算符`CStringT`包含嵌入的空字符的对象可能会产生意外的结果。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]  
  
##  <a name="_dtorcstringt"></a>CStringT:: ~ CStringT  
 销毁`CStringT`对象。  
  
```  
~CStringT() throw();
```  
  
### <a name="remarks"></a>备注  
 销毁`CStringT`对象。  
  
##  <a name="delete"></a>CStringT::Delete  
 从给定索引处的字符从字符串中删除一个字符。  
  
```  
int Delete(int iIndex, int nCount = 1);
```  
  
### <a name="parameters"></a>参数  
 `iIndex`  
 中的第一个字符的从零开始索引`CStringT`要删除对象。  
  
 `nCount`  
 要删除的字符数。  
  
### <a name="return-value"></a>返回值  
 已更改的字符串的长度。  
  
### <a name="remarks"></a>备注  
 如果`nCount`超过会删除字符串，字符串的其余部分。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]  
  
```Output  
Before: Soccer is best,
    but hockey is quicker!  
After: Soccer best,
    but hockey is quicker!  
```  
  
##  <a name="find"></a>CStringT::Find  
 此字符串中搜索的字符或子字符串的第一个匹配项。  
  
```  
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pszSub`  
 要搜索的子字符串。  
  
 `iStart`  
 要开始使用，搜索的字符串或为 0 从头开始中的字符的索引。  
  
 `ch`  
 要搜索的单个字符。  
  
### <a name="return-value"></a>返回值  
 在此的第一个字符的从零开始索引`CStringT`匹配的请求的子字符串或字符的对象; 如果未找到子字符串或字符，则为-1。  
  
### <a name="remarks"></a>备注  
 函数重载以接受两个单字符 (类似于运行时函数`strchr`) 和字符串 (类似于`strstr`)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]  
  
##  <a name="findoneof"></a>CStringT::FindOneOf  
 此字符串中包含任何字符匹配的第一个字符中搜索`pszCharSet`。  
  
```  
int FindOneOf(PCXSTR pszCharSet) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pszCharSet`  
 包含用于匹配的字符的字符串。  
  
### <a name="return-value"></a>返回值  
 也是在此字符串中的第一个字符的从零开始索引`pszCharSet`; 如果没有匹配项-1。  
  
### <a name="remarks"></a>备注  
 查找任一种情况中的字符的第一个匹配项`pszCharSet`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]  
  
##  <a name="format"></a>CStringT::Format  
 写入格式化的数据写入`CStringT`中相同的方式[sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)数据到 C 样式字符数组的格式。  
  
```  
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```  
  
### <a name="parameters"></a>参数  
 `nFormatID`  
 包含格式控件字符串的字符串资源标识符。  
  
 `pszFormat`  
 格式控件字符串。  
  
 `argument`  
 可选参数。  
  
### <a name="remarks"></a>备注  
 此函数格式并将存储中的字符和值的一系列`CStringT`。 每个可选参数 （如果有） 进行转换和输出中的相应格式规范根据`pszFormat`或从所标识的字符串资源`nFormatID`。  
  
 如果作为参数传递给提供的字符串对象本身，则调用将失败`Format`。 例如，下面的代码将导致不可预知的结果：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]  
  
 有关详细信息，请参阅[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]  
  
##  <a name="formatmessage"></a>CStringT::FormatMessage  
 格式化消息字符串。  
  
```  
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```  
  
### <a name="parameters"></a>参数  
 `nFormatID`  
 包含未格式化的消息文本的字符串资源标识符。  
  
 `pszFormat`  
 指向以的格式控件字符串。 它将为插入扫描并相应地设置格式。 格式字符串是类似于运行时函数`printf`-样式格式字符串，但它允许按任意顺序插入的参数。  
  
 `argument`  
 可选参数。  
  
### <a name="remarks"></a>备注  
 函数需要作为输入的消息定义。 消息定义由`pszFormat`或从所标识的字符串资源`nFormatID`。 函数将复制到的格式的消息文本`CStringT`处理任何嵌入的对象，如果请求插入序列。  
  
> [!NOTE]
> `FormatMessage`尝试为新格式的字符串分配系统内存。 如果此尝试失败，会自动引发一个内存异常。  
  
 每次插入必须具有相应的参数以下`pszFormat`或`nFormatID`参数。 消息文本中用于动态格式化消息支持多个转义序列。 有关详细信息，请参阅 Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) Windows SDK 中的函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]  
  
##  <a name="formatmessagev"></a>CStringT::FormatMessageV  
 格式化消息字符串使用变量自变量列表。  
  
```  
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```  
  
### <a name="parameters"></a>参数  
 `pszFormat`  
 指向以的格式控件字符串。 它将为插入扫描并相应地设置格式。 格式字符串是类似于运行时函数`printf`-样式格式字符串，但它允许按任意顺序插入的参数。  
  
 `pArgList`  
 指向参数列表的指针。  
  
### <a name="remarks"></a>备注  
 函数需要作为输入，消息定义由`pszFormat`。 函数将复制的格式的消息文本和变量的自变量列表`CStringT`处理任何嵌入的对象，如果请求插入序列。  
  
> [!NOTE]
> `FormatMessageV`调用[CStringT::FormatMessage](#formatmessage)，尝试为新格式的字符串分配系统内存。 如果此尝试失败，会自动引发一个内存异常。  
  
 有关详细信息，请参阅 Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) Windows SDK 中的函数。  
  
##  <a name="formatv"></a>CStringT::FormatV  
 格式化消息字符串使用变量自变量列表。  
  
```  
void FormatV(PCXSTR pszFormat, va_list args);
```  
  
### <a name="parameters"></a>参数  
 `pszFormat`  
 指向以的格式控件字符串。 它将为插入扫描并相应地设置格式。 格式字符串是类似于运行时函数`printf`-样式格式字符串，但它允许按任意顺序插入的参数。  
  
 `args`  
 指向参数列表的指针。  
  
### <a name="remarks"></a>备注  
 将格式化的字符串和变量的自变量列表`CStringT`中相同的字符串的方式`vsprintf_s`数据到 C 样式字符数组的格式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]  
  
##  <a name="getenvironmentvariable"></a>CStringT::GetEnvironmentVariable  
 将字符串设置为指定的环境变量的值。  
  
```  
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```  
  
### <a name="parameters"></a>参数  
 `pszVar`  
 为指定的环境变量的以 null 结尾的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 调用进程的环境块中检索指定的变量的值。 值为以 null 结尾的字符串的字符的形式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]  
  
##  <a name="insert"></a>CStringT::Insert  
 字符串内的给定索引处插入单个字符或子字符串。  
  
```  
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```  
  
### <a name="parameters"></a>参数  
 `iIndex`  
 在其前插入将发生的字符的索引。  
  
 `psz`  
 指向要插入的子字符串的指针。  
  
 `ch`  
 要插入的字符。  
  
### <a name="return-value"></a>返回值  
 已更改的字符串的长度。  
  
### <a name="remarks"></a>备注  
 `iIndex`参数标识将被移动以便腾出空间供字符或子字符串的第一个字符。 如果`nIndex`为零，在整个字符串之前将发生插入。 如果`nIndex`高于字符串，该函数的长度将连接存在字符串和新材料提供通过以下任一方法`ch`或`psz`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]  
  
##  <a name="left"></a>CStringT::Left  
 从此 `nCount` 对象中提取最左侧 `CStringT` 字符并返回已提取的子字符串的副本。  
  
```  
CStringT Left(int nCount) const; 
```  
  
### <a name="parameters"></a>参数  
 `nCount`  
 从此 `CStringT` 对象中提取的字符的数量。  
  
### <a name="return-value"></a>返回值  
 包含指定范围内的字符的副本的 `CStringT` 对象。 返回的 `CStringT` 对象可以为空。  
  
### <a name="remarks"></a>备注  
 如果 `nCount` 超过了字符串长度，则提取整个字符串。 `Left` 类似于 Basic `Left` 函数。  
  
 对于多字节字符集 (MBCS)，`nCount` 将每 8 位序列视为一个字符，以便让 `nCount` 返回多字节字符的数目乘以 2。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]  
  
##  <a name="loadstring"></a>CStringT::LoadString  
 读取 Windows 字符串资源，由标识`nID`，到现有`CStringT`对象。  
  
```  
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `hInstance`  
 该模块的实例句柄。  
  
 `nID`  
 Windows 字符串资源 id。  
  
 `wLanguageID`  
 字符串资源的语言。  
  
### <a name="return-value"></a>返回值  
 如果资源负载成功; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 加载的字符串资源 ( `nID`) 从指定的模块 ( `hInstance`) 使用指定的语言 ( `wLanguage`)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]  
  
##  <a name="makelower"></a>CStringT::MakeLower  
 将转换`CStringT`对象和小写的字符串。  
  
```  
CStringT& MakeLower();
```  
  
### <a name="return-value"></a>返回值  
 生成的小写字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]  
  
##  <a name="makereverse"></a>CStringT::MakeReverse  
 中的字符顺序反转`CStringT`对象。  
  
```  
CStringT& MakeReverse();
```  
  
### <a name="return-value"></a>返回值  
 生成反转字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]  
  
##  <a name="makeupper"></a>CStringT::MakeUpper  
 将转换`CStringT`为大写的字符串对象。  
  
```  
CStringT& MakeUpper();
```  
  
### <a name="return-value"></a>返回值  
 生成的大写字符串。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]  
  
##  <a name="mid"></a>CStringT::Mid  
 提取子字符串的长度`nCount`从此字符`CStringT`对象，从位置开始`iFirst`（从零开始）。  
  
```  
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const; 
```  
  
### <a name="parameters"></a>参数  
 `iFirst`  
 在此的第一个字符的从零开始索引`CStringT`提取子字符串中要包括的对象。  
  
 `nCount`  
 从此 `CStringT` 对象中提取的字符的数量。 如果未提供此参数，然后提取字符串的其余部分。  
  
### <a name="return-value"></a>返回值  
 包含指定范围内的字符的副本的 `CStringT` 对象。 请注意，返回`CStringT`对象可能为空。  
  
### <a name="remarks"></a>备注  
 该函数返回提取子字符串的副本。 `Mid`类似于基本 Mid 函数 （只是在 Basic 中的索引都是一个基于）。  
  
 为多字节字符集 (MBCS)`nCount`指的是一个多字节字符被视为两个字符中每个 8 位字符; 即，主管和结尾字节。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]  
  
##  <a name="oemtoansi"></a>CStringT::OemToAnsi  
 将在此的所有字符都转换`CStringT`从 ANSI 字符集中的 OEM 字符集的对象。  
  
```  
void OemToAnsi();
```  
  
### <a name="remarks"></a>备注  
 此函数不可用如果`_UNICODE`定义。  
  
### <a name="example"></a>示例  
 请参阅示例[CStringT::AnsiToOem](#ansitooem)。  
  
##  <a name="operator_add"></a>CStringT::operator +  
 连接两个字符串或字符和字符串。  
  
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
 `ch1`  
 要使用字符串串联 ANSI 或 Unicode 字符。  
  
 `ch2`  
 要使用字符串串联 ANSI 或 Unicode 字符。  
  
 `str1`  
 A`CStringT`要串联的字符串或字符。  
  
 `str2`  
 A`CStringT`要串联的字符串或字符。  
  
 `psz1`  
 指向以 null 结尾的字符串要串联的字符串或字符的指针。  
  
 `psz2`  
 指向要串联的字符串或字符字符串的指针。  
  
### <a name="remarks"></a>备注  
 有七个重载形式的`CStringT::operator+`函数。 第一个版本串联两个现有`CStringT`对象。 下一步的两个连接`CStringT`对象并以 null 结尾的字符串。 下一步的两个连接`CStringT`对象和一个 ANSI 字符。 最后两个连接`CStringT`对象和一个 Unicode 字符。  
  
> [!NOTE]
>  但也可以创建`CStringT`包含的实例嵌入的空字符，我们建议对其。 在调用方法和运算符`CStringT`包含嵌入的空字符的对象可能会产生意外的结果。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]  
  
##  <a name="operator_add_eq"></a>CStringT::operator + =  
 连接到字符串的末尾字符数。  
  
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
 str  
 对 `CThisSimpleString` 对象的引用。  
  
 `bMFCDLL`  
 指定的项目是否 MFC DLL 是否一个布尔值。  
  
 `BaseType`  
 字符串基类型。  
  
 `var`  
 要串联到此字符串的变量对象。  
  
 `ch`  
 要使用字符串串联 ANSI 或 Unicode 字符。  
  
 `pszSrc`  
 指向要串联的原始字符串的指针。  
  
 `strSrc`  
 A`CStringT`要串联到此字符串。  
  
### <a name="remarks"></a>备注  
 运算符可接受另一个`CStringT`对象、 字符指针或单个字符。 你应注意每当你使用此串联运算符，因为可以为添加到此字符分配新存储，可能会发生异常的内存`CStringT`对象。  
  
 有关信息`CThisSimpleString`，请参阅备注部分的[CStringT::CStringT](#cstringt)。  
  
> [!NOTE]
>  但也可以创建`CStringT`包含的实例嵌入的空字符，我们建议对其。 在调用方法和运算符`CStringT`包含嵌入的空字符的对象可能会产生意外的结果。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]  
  
##  <a name="operator_eq_eq"></a>CStringT::operator = =  
 确定两个字符串是否逻辑上相等。  
  
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
 `ch1`  
 比较中的 ANSI 或 Unicode 字符。  
  
 `ch2`  
 比较中的 ANSI 或 Unicode 字符。  
  
 `str1`  
 A`CStringT`进行比较。  
  
 `str2`  
 A`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 测试是否字符串或左侧的字符等于字符串或字符，在右侧，并返回 TRUE 或 FALSE 相应地。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]  
  
##  <a name="operator_neq"></a>CStringT::operator ！ =  
 确定两个字符串是否以逻辑方式不相等。  
  
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
 `ch1`  
 要使用字符串串联 ANSI 或 Unicode 字符。  
  
 `ch2`  
 要使用字符串串联 ANSI 或 Unicode 字符。  
  
 `str1`  
 A`CStringT`进行比较。  
  
 `str2`  
 A`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 如果字符串或左侧的字符不是与字符串或字符右侧相等，测试。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]  
  
##  <a name="operator_lt"></a>CStringT::operator&lt;  
 确定运算符左侧的字符串是否小于右侧的字符串。  
  
```  
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 A`CStringT`进行比较。  
  
 `str2`  
 A`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 字符串，直到逐字符之间的字典顺序比较：  
  
-   如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。  
  
-   如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。  
  
-   如果找到的所有字符完全相同且字符串的字符数也相同，则这两个字符串视为相等。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]  
  
##  <a name="operator_gt"></a>CStringT::operator&gt;  
 确定运算符左侧的字符串是否大于右侧的字符串。  
  
```  
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 A`CStringT`进行比较。  
  
 `str2`  
 A`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 字符串，直到逐字符之间的字典顺序比较：  
  
-   如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。  
  
-   如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。  
  
-   它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]  
  
##  <a name="operator_lt_eq"></a>CStringT::operator&lt;=  
 确定运算符左侧的字符串是否小于或等于右侧的字符串。  
  
```  
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 A`CStringT`进行比较。  
  
 `str2`  
 A`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 字符串，直到逐字符之间的字典顺序比较：  
  
-   如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。  
  
-   如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。  
  
-   它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]  
  
##  <a name="operator_gt_eq"></a>CStringT::operator&gt;=  
 确定运算符左侧的字符串是否大于或等于右侧的字符串。  
  
```  
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 A`CStringT`进行比较。  
  
 `str2`  
 A`CStringT`进行比较。  
  
 `psz1`  
 为用于比较的字符串指针。  
  
 `psz2`  
 为用于比较的字符串指针。  
  
### <a name="remarks"></a>备注  
 字符串，直到逐字符之间的字典顺序比较：  
  
-   如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。  
  
-   如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。  
  
-   它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]  
  
##  <a name="remove"></a>CStringT::Remove  
 从字符串中删除指定的字符的所有实例。  
  
```  
int Remove(XCHAR chRemove);
```  
  
### <a name="parameters"></a>参数  
 `chRemove`  
 要从字符串中删除的字符。  
  
### <a name="return-value"></a>返回值  
 从字符串中删除的字符数。 如果未更改字符串，则为零。  
  
### <a name="remarks"></a>备注  
 字符比较是区分大小写。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]  
  
##  <a name="replace"></a>CStringT::Replace  
 有两个版本的`Replace`。第一个版本通过使用另一个子字符串替换子字符串的一个或多个的副本。 这两个子字符串是以 null 结尾。 第二个版本使用另一个字符替换字符的一个或多个副本。 这两个版本操作中存储的字符数据`CStringT`。  
  
```  
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```  
  
### <a name="parameters"></a>参数  
 `pszOld`  
 指向以 null 结尾的字符串替换为`pszNew`。  
  
 `pszNew`  
 指向以 null 结尾的字符串，用于替换`pszOld`。  
  
 `chOld`  
 要由替换的字符`chNew`。  
  
 `chNew`  
 字符替换`chOld`。  
  
### <a name="return-value"></a>返回值  
 如果未更改字符串，则返回字符或子字符串，则为零的被替换实例的数。  
  
### <a name="remarks"></a>备注  
 `Replace`可以更改的字符串长度，因为`pszNew`和`pszOld`的旧子字符串的多个副本可以变为新并不一定要长度相同。 函数执行区分大小写的匹配项。  
  
 示例`CStringT`实例`CString`， `CStringA`，和`CStringW`。  
  
 有关`CStringA`，`Replace`配合 ANSI 或多字节 (MBCS) 字符。 有关`CStringW`，`Replace`配合宽字符。  
  
 有关`CString`，字符数据类型选择在编译时，基于是否定义下表中的常量。  
  
|定义的常量|字符数据类型|  
|----------------------|-------------------------|  
|`_UNICODE`|宽字符|  
|`_MBCS`|多字节字符|  
|既不|单字节字符|  
|消息和传送|未定义|  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]  
  
##  <a name="reversefind"></a>CStringT::ReverseFind  
 搜索此`CStringT`字符的最后一个匹配项的对象。  
  
```  
int ReverseFind(XCHAR ch) const throw();
```  
  
### <a name="parameters"></a>参数  
 `ch`  
 要搜索的字符。  
  
### <a name="return-value"></a>返回值  
 在此的最后一个字符的从零开始索引`CStringT`匹配的请求的字符，则为-1，如果未找到该字符的对象。  
  
### <a name="remarks"></a>备注  
 函数是类似于运行时函数`strrchr`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]  
  
##  <a name="right"></a>CStringT::Right  
 提取上次 (即最右边)`nCount`从此字符`CStringT`对象并返回提取的子字符串的副本。  
  
```  
CStringT Right(int nCount) const; 
```  
  
### <a name="parameters"></a>参数  
 `nCount`  
 从此 `CStringT` 对象中提取的字符的数量。  
  
### <a name="return-value"></a>返回值  
 包含指定范围内的字符的副本的 `CStringT` 对象。 请注意，返回`CStringT`对象可以为空。  
  
### <a name="remarks"></a>备注  
 如果 `nCount` 超过了字符串长度，则提取整个字符串。 `Right`类似于 Basic`Right`函数 （只不过 Basic 中的索引是从零开始）。  
  
 为多字节字符集 (MBCS)`nCount`指的是一个多字节字符被视为两个字符中每个 8 位字符; 即，主管和结尾字节。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]  
  
##  <a name="setsysstring"></a>CStringT::SetSysString  
 重新分配`BSTR`指向`pbstr`，并将复制的内容`CStringT`对象执行它，请包括`NULL`字符。  
  
```  
BSTR SetSysString(BSTR* pbstr) const; 
```  
  
### <a name="parameters"></a>参数  
 `pbstr`  
 指向字符字符串的指针。  
  
### <a name="return-value"></a>返回值  
 新字符串。  
  
### <a name="remarks"></a>备注  
 具体取决于内容`CStringT`对象、 的值`BSTR`所引用的`pbstr`可以更改。 该函数将引发`CMemoryException`如果存在内存不足。  
  
 此函数通常用于更改为自动化通过引用传递的字符串的值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]  
  
##  <a name="spanexcluding"></a>CStringT::SpanExcluding  
 从开头的第一个字符，不在组由标识的字符的字符串中提取字符`pszCharSet`。  
  
```  
CStringT SpanExcluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>参数  
 `pszCharSet`  
 字符串解释为一组字符。  
  
### <a name="return-value"></a>返回值  
 包含不在字符串中的字符的子字符串`pszCharSet`、 从字符串中的第一个字符开始和结尾，也是在字符串中找到的第一个字符`pszCharSet`(即，开头的第一个字符字符串和最多到但不是字符串中的第一个字符包括找到`pszCharSet`)。 它将返回整个字符串，如果在没有符`pszCharSet`字符串中找到。  
  
### <a name="remarks"></a>备注  
 `SpanExcluding`提取并返回前面从一个字符的第一个匹配项的所有字符`pszCharSet`(换而言之中的字符`pszCharSet`并不会返回以下字符串中的所有字符)。 如果从没有符`pszCharSet`在字符串中，然后找到`SpanExcluding`返回整个字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]  
  
##  <a name="spanincluding"></a>CStringT::SpanIncluding  
 从开头的第一个字符，位于由标识的字符集的字符串中提取字符`pszCharSet`。  
  
```  
CStringT SpanIncluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>参数  
 `pszCharSet`  
 字符串解释为一组字符。  
  
### <a name="return-value"></a>返回值  
 包含在字符串中的字符的子字符串`pszCharSet`，从字符串中的第一个字符开始和结束时将不在字符串中找到的字符`pszCharSet`。 `SpanIncluding`如果字符串中的第一个字符不在指定的集，则返回空的子字符串。  
  
### <a name="remarks"></a>备注  
 如果字符串的第一个字符不在的字符集，然后`SpanIncluding`返回空字符串。 否则，它将返回集中的连续字符序列。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]  
  
##  <a name="tokenize"></a>CStringT::Tokenize  
 在目标字符串中查找下一个标记  
  
```  
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const; 
```  
  
### <a name="parameters"></a>参数  
 `pszTokens`  
 包含标记分隔符的字符串。 这些分隔符的顺序并不重要。  
  
 `iStart`  
 要开始搜索的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 A`CStringT`对象，其中包含当前的令牌值。  
  
### <a name="remarks"></a>备注  
 `Tokenize`函数查找目标字符串中的下一个标记。 中的字符组`pszTokens`指定可能要找的标记的分隔符。 每次调用`Tokenize`函数开始`iStart`、 跳过前导分隔符，并返回`CStringT`对象，其中包含当前令牌，直到下一步的分隔符字符的字符串。 值`iStart`更新要之后结束的分隔符字符，则为-1，如果已到达字符串末尾的位置。 多个令牌的更改会损坏超出目标字符串的其余部分一系列调用到`Tokenize`，使用`iStart`来跟踪在字符串的下一个标记为要读取的位置。 没有更多的令牌时该函数将返回空字符串和`iStart`将设置为-1。  
  
 与不同的 CRT 标记功能，例如[strtok_s、 _strtok_s_l、 wcstok_s、 _wcstok_s_l，_mbstok_s，_mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)，`Tokenize`不会修改目标字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]  
  
### <a name="remarks"></a>备注  
 此示例的输出如下所示：  
  
 `Resulting Token: First`  
  
 `Resulting Token: Second`  
  
 `Resulting Token: Third`  
  
##  <a name="trim"></a>CStringT::Trim  
 修剪前导空格和尾随从字符串的字符。  
  
```  
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```  
  
### <a name="parameters"></a>参数  
 `chTarget`  
 要修整目标字符。  
  
 `pszTargets`  
 指向包含目标字符要修整的字符串的指针。 所有前导空格和尾随匹配项中的字符`pszTarget`将从无法删除`CStringT`对象。  
  
### <a name="return-value"></a>返回值  
 返回裁剪后的字符串。  
  
### <a name="remarks"></a>备注  
 移除下列其中一项的所有前导和尾随匹配的项：  
  
-   由指定的字符`chTarget.`  
  
-   在指定的字符串中找到的所有字符`pszTargets.`  
  
-   空格。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]  
  
### <a name="remarks"></a>备注  
 此示例的输出如下所示：  
  
 `Before: "******Soccer is best, but liquor is quicker!!!!!"`  
  
 `After : "Soccer is best, but liquor is quicker"`  
  
##  <a name="trimleft"></a>CStringT::TrimLeft  
 修剪前导从字符串的字符。  
  
```  
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```  
  
### <a name="parameters"></a>参数  
 `chTarget`  
 要修整目标字符。  
  
 `pszTargets`  
 指向包含目标字符要修整的字符串的指针。 中的字符的所有前导匹配项`pszTarget`将从无法删除`CStringT`对象。  
  
### <a name="return-value"></a>返回值  
 生成裁剪后的字符串。  
  
### <a name="remarks"></a>备注  
 移除下列其中一项的所有前导和尾随匹配的项：  
  
-   由指定的字符`chTarget.`  
  
-   在指定的字符串中找到的所有字符`pszTargets.`  
  
-   空格。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]  
  
##  <a name="trimright"></a>CStringT::TrimRight  
 修剪尾随从字符串的字符。  
  
```  
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```  
  
### <a name="parameters"></a>参数  
 `chTarget`  
 要修整目标字符。  
  
 `pszTargets`  
 指向包含目标字符要修整的字符串的指针。 所有尾随匹配项中的字符`pszTarget`将从无法删除`CStringT`对象。  
  
### <a name="return-value"></a>返回值  
 返回`CStringT`对象，其中包含裁剪后的字符串。  
  
### <a name="remarks"></a>备注  
 删除尾随匹配项的以下项之一：  
  
-   由指定的字符`chTarget.`  
  
-   在指定的字符串中找到的所有字符`pszTargets.`  
  
-   空格。  
  
 `CStringT& TrimRight(XCHAR chTarget)`版本接受一个字符参数和从末尾删除该字符的所有副本`CStringT`字符串数据。 它从字符串末尾开始，到队工作原理。 它停止找到不同的字符时或当`CSTringT`用完了字符数据。  
  
 `CStringT& TrimRight(PCXSTR pszTargets)`版本接受包含所有不同的字符要搜索的以 null 结尾的字符串。 它会删除这些字符中的所有副本`CStringT`对象。 它从字符串末尾开始并且到队工作。 它停止找到不在目标字符串的字符时或当`CStringT`用完了字符数据。 它不会尝试将整个目标字符串与末尾的子字符串匹配`CStringT`。  
  
 `CStringT& TrimRight()`版本不需要任何参数。 剪裁任何尾随空格字符结尾处`CStringT`字符串。 分行符、 空格或选项卡，可以是空白字符。  
  
-  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)   
 [CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)


