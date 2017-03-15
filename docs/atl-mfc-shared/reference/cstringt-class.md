---
title: "CStringT 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CString
- CStringT
- ATL::CStringT
- ATL.CStringT
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
caps.latest.revision: 33
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: 961dc75623ec04993d118e46e1d4ba73a9aadcec
ms.lasthandoff: 02/28/2017

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
  
- `char`（针对 ANSI 字符串）。  
  
- `wchar_t`（对于 Unicode 字符串）。  
  
- **TCHAR** （针对 ANSI 和 Unicode 字符串）。  
  
 `StringTraits`  
 确定此字符串类是否需要 C 运行时 (CRT) 库支持和字符串资源的位置。 可以是以下各项之一：  
  
- **StrTraitATL<> </> ** |`char` |**TCHAR、 ChTraitsCRT<> </> ** |`char` |**TCHAR > >**  
  
     此类需要 CRT 支持，并由指定的模块中的资源字符串搜索`m_hInstResource`（应用程序的模块类的成员）。  
  
- **StrTraitATL<> </> ** |`char` |**TCHAR、 ChTraitsOS<> </> ** |`char` |**TCHAR > >**  
  
     类无需 CRT 支持，并由指定的模块中的资源字符串搜索`m_hInstResource`（应用程序的模块类的成员）。  
  
- **StrTraitMFC<> </> ** |`char` |**TCHAR、 ChTraitsCRT<> </> ** |`char` |**TCHAR > >**  
  
     此类需要 CRT 支持，并使用标准 MFC 搜索算法的资源字符串的搜索。  
  
- **StrTraitMFC<> </> ** |`char` |**TCHAR、 ChTraitsOS<> </> ** |`char` |**TCHAR > >**  
  
     此类不需要 CRT 支持，并使用标准 MFC 搜索算法的资源字符串的搜索。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CStringT::CStringT](#cstringt)|构造`CStringT`对象以各种方式。|  
|[CStringT:: ~ CStringT](#_dtorcstringt)|销毁 `CStringT` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CStringT::AllocSysString](#allocsysstring)|分配`BSTR`从`CStringT`数据。|  
|[CStringT::AnsiToOem](#ansitooem)|可以从 OEM 字符集中的 ANSI 字符集的就地转换。|  
|[CStringT::AppendFormat](#appendformat)|将带格式的数据追加到现有`CStringT`对象。|  
|[CStringT::Collate](#collate)|比较两个字符串 （区分大小写，使用特定于区域设置信息）。|  
|[CStringT::CollateNoCase](#collatenocase)|比较两个字符串 （不区分大小写，使用特定于区域设置信息）。|  
|[CStringT::Compare](#compare)|比较两个字符串 （区分大小写）。|  
|[CStringT::CompareNoCase](#comparenocase)|比较两个字符串 （不区分大小写）。|  
|[CStringT::Delete](#delete)|从字符串中删除一个字符。|  
|[CStringT::Find](#find)|查找字符或较大字符串内的子字符串。|  
|[CStringT::FindOneOf](#findoneof)|查找从一组的第一个匹配字符。|  
|[CStringT::Format](#format)|格式字符串作为`sprintf`未。|  
|[CStringT::FormatMessage](#formatmessage)|设置消息字符串的格式。|  
|[CStringT::FormatMessageV](#formatmessagev)|设置使用变量参数列表的消息字符串的格式。|  
|[CStringT::FormatV](#formatv)|设置使用变量参数列表的字符串的格式。|  
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|将字符串设置为指定的环境变量的值。|  
|[CStringT::Insert](#insert)|在字符串中的给定索引处插入一个字符或子字符串。|  
|[CStringT::Left](#left)|提取字符串的左侧的部分。|  
|[CStringT::LoadString](#loadstring)|加载现有`CStringT`从 Windows 资源的对象。|  
|[CStringT::MakeLower](#makelower)|将转换为小写字符此字符串中的所有字符。|  
|[CStringT::MakeReverse](#makereverse)|反转字符串。|  
|[CStringT::MakeUpper](#makeupper)|将转换为大写字符此字符串中的所有字符。|  
|[CStringT::Mid](#mid)|提取字符串的中间部分。|  
|[CStringT::OemToAnsi](#oemtoansi)|可以进行适当地转换为 ANSI 字符集的 OEM 字符集中。|  
|[CStringT::Remove](#remove)|删除表示字符串中的字符。|  
|[CStringT::Replace](#replace)|替换指明字符替换为其他字符。|  
|[CStringT::ReverseFind](#reversefind)|查找较大的字符串; 中的字符从末尾开始。|  
|[CStringT::Right](#right)|提取字符串的右侧部分。|  
|[CStringT::SetSysString](#setsysstring)|设置现有`BSTR`对象从所有数据`CStringT`对象。|  
|[CStringT::SpanExcluding](#spanexcluding)|提取的字符开头的第一个字符，不是由标识的字符集的字符串`pszCharSet`。|  
|[CStringT::SpanIncluding](#spanincluding)|提取子字符串，其中包含仅在一组字符。|  
|[CStringT::Tokenize](#tokenize)|提取的目标字符串中指定的令牌。|  
|[CStringT::Trim](#trim)|修剪前导空格和尾随空白字符的字符串。|  
|[CStringT::TrimLeft](#trimleft)|修剪前导空白字符的字符串。|  
|[CStringT::TrimRight](#trimright)|修剪尾随空白字符的字符串。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](#operator_eq)|将一个新值赋给`CStringT`对象。|  
|[CStringT::operator +](#operator_add)|串联两个字符串或字符和字符串。|  
|[CStringT::operator + =](#operator_add_eq)|连接到现有字符串的末尾的新字符串。|  
|[CStringT::operator = =](#operator_eq_eq)|确定两个字符串是否在逻辑上相等。|  
|[CStringT::operator ！ =](#operator_neq)|确定两个字符串是否在逻辑上不相等。|  
|[CStringT::operator&lt;](#operator_lt)|确定该运算符左侧的字符串是否小于右侧的字符串。|  
|[CStringT::operator&gt;](#operator_gt)|确定该运算符左侧的字符串是否大于右侧的字符串。|  
|[CStringT::operator&lt;=](#operator_lt_eq)|确定该运算符左侧的字符串是否小于或等于右侧的字符串。|  
|[CStringT::operator&gt;=](#operator_gt_eq)|确定该运算符左侧的字符串是否大于或等于右侧的字符串。|  
  
## <a name="remarks"></a>备注  
 `CStringT`继承自[CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)。 高级的功能，如字符操作，排序和搜索，由实现`CStringT`。  
  
> [!NOTE]
> `CStringT`对象是能够引发异常。 发生这种情况时`CStringT`对象出于任何原因耗尽内存。  
  
 一个`CStringT`对象包含的字符长度可变的序列。 `CStringT`提供了函数和运算符使用的语法类似于 Basic。 串联运算符和比较运算符，以及简化的内存管理、 使`CStringT`更加轻松地使用比普通字符数组的对象。  
  
> [!NOTE]
>  尽管可能创建`CStringT`实例包含嵌入的 null 字符，我们建议您不要它。 在调用方法和运算符`CStringT`包含嵌入的空字符的对象可能会产生意外的结果。  
  
 通过使用不同的组合`BaseType`和`StringTraits`参数，`CStringT`对象可以是以下类型中的有已预定义的 ATL 库。  
  
 如果使用 ATL 应用程序中︰  
  
 `CString``CStringA`，和`CStringW`导出从 MFC DLL (MFC90。DLL)，永远不会从用户 Dll。 这样做是为了防止`CStringT`从被多次定义。  
  
> [!NOTE]
>  如果在导出时遇到的链接器错误`CString`-派生自 MFC 扩展 DLL 中 Visual c + +.NET 2002年的类，并且应用了解决方法知识库文章"链接错误时您导入 CString-Derived 类"(Q309801) 中所述应删除此解决方法代码，因为此问题已修复在 Visual c + +.NET 2003年。 您可以找到知识库文章位于 MSDN Library CD-ROM 或[http://support.microsoft.com/support](http://support.microsoft.com/support)。  
  
 下面的字符串类型都是基于 MFC 的应用程序中可用︰  
  
|CStringT 类型|声明|  
|-------------------|-----------------|  
|`CStringA`|一个 ANSI 字符键入与 CRT 支持的字符串。|  
|`CStringW`|一个 Unicode 字符键入与 CRT 支持的字符串。|  
|`CString`|具有 CRT 支持的 ANSI 和 Unicode 字符类型。|  
  
 下面的字符串中提供了类型项目的位置**ATL_CSTRING_NO_CRT**定义︰  
  
|CStringT 类型|声明|  
|-------------------|-----------------|  
|**CAtlStringA**|一个 ANSI 字符键入不带 CRT 支持的字符串。|  
|**CAtlStringW**|一个 Unicode 字符键入不带 CRT 支持的字符串。|  
|**CAtlString**|如果没有 CRT 支持 ANSI 和 Unicode 字符类型。|  
  
 下面的字符串中提供了类型项目的位置**ATL_CSTRING_NO_CRT**未定义︰  
  
|CStringT 类型|声明|  
|-------------------|-----------------|  
|**CAtlStringA**|一个 ANSI 字符键入与 CRT 支持的字符串。|  
|**CAtlStringW**|一个 Unicode 字符键入与 CRT 支持的字符串。|  
|**CAtlString**|具有 CRT 支持的 ANSI 和 Unicode 字符类型。|  
  
 `CString`对象还具有以下特征︰  
  
- `CStringT`串联操作后，对象可能会增长。  
  
- `CStringT`对象遵循"值语义"。 思考的`CStringT`对象作为实际的字符串，而不是指向字符串的指针。  
  
-   您可以自由地替换`CStringT`对象`PCXSTR`函数参数。  
  
-   字符串缓冲区的自定义内存管理。 有关详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="cstringt-predefined-types"></a>CStringT 预定义的类型  
 因为`CStringT`使用模板参数来定义字符类型 (任一[wchar_t](../../c-runtime-library/standard-types.md)或[char](../../c-runtime-library/standard-types.md)) 支持，方法参数类型可以是复杂的时段。 若要简化此问题，一组预定义的类型定义和使用在整个`CStringT`类。 下表列出了各种类型︰  
  
|名称|描述|  
|----------|-----------------|  
|`XCHAR`|单个字符 (要么`wchar_t`或`char`) 具有相同的字符类型，作为`CStringT`对象。|  
|**YCHAR**|单个字符 (要么`wchar_t`或`char`) 相反的字符类型，作为`CStringT`对象。|  
|`PXSTR`|指向字符字符串的指针 (要么`wchar_t`或`char`) 具有相同的字符类型，作为`CStringT`对象。|  
|**PYSTR**|指向字符字符串的指针 (要么`wchar_t`或`char`) 相反的字符类型，作为`CStringT`对象。|  
|`PCXSTR`|一个指向**const**字符字符串 (既`wchar_t`或`char`) 具有相同的字符类型，作为`CStringT`对象。|  
|**PCYSTR**|一个指向**const**字符字符串 (既`wchar_t`或`char`) 相反的字符类型，作为`CStringT`对象。|  
  
> [!NOTE]
>  以前使用过的文档中未提到的方法的代码`CString`(如**AssignCopy**) 必须与使用的以下有案可稽的方法的代码替换`CStringT`(如`GetBuffer`或`ReleaseBuffer`)。 这些方法从继承`CSimpleStringT`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)  
  
 `CStringT`  
  
## <a name="requirements"></a>要求  
  
|Header|用于|  
|------------|-------------|  
|cstringt.h|仅 MFC 字符串对象|  
|atlstr.h|非 MFC 字符串对象|  
  
##  <a name="a-nameallocsysstringa--cstringtallocsysstring"></a><a name="allocsysstring"></a>CStringT::AllocSysString  
 分配的类型的自动化兼容字符串`BSTR`，并将复制的内容`CStringT`对象插入它，包括终止 null 字符。  
  
```  
BSTR AllocSysString() const;  
```  
  
### <a name="return-value"></a>返回值  
 新分配的字符串。  
  
### <a name="remarks"></a>备注  
 在 MFC 程序中， [CMemoryException 类](../../mfc/reference/cmemoryexception-class.md)如果存在内存不足，则会引发。 在 ATL 程序[CAtlException](../../atl/reference/catlexception-class.md)引发。 此函数通常用于为自动化返回的字符串。  
  
 通常，如果将此字符串传递给 COM 函数作为 [in] 参数，则此要求调用方释放字符串。 这可以通过使用[SysFreeString](http://msdn.microsoft.com/en-us/8f230ee3-5f6e-4cb9-a910-9c90b754dcd3)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 有关详细信息，请参阅[Allocating 和释放内存可供 BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)。  
  
 有关 Windows 中的 OLE 分配函数的详细信息，请参阅[SysAllocString](http://msdn.microsoft.com/en-us/9e0437a2-9b4a-4576-88b0-5cb9d08ca29b)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CStringT::AllocSysString` 的用法。  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&105;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]  
  
##  <a name="a-nameansitooema--cstringtansitooem"></a><a name="ansitooem"></a>CStringT::AnsiToOem  
 将在此的所有字符都转换`CStringT`OEM 字符集中的 ANSI 字符集中的对象。  
  
```  
void AnsiToOem();
```  
  
### <a name="remarks"></a>备注  
 该函数不可用如果`_UNICODE`定义。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&106;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]  
  
##  <a name="a-nameappendformata--cstringtappendformat"></a><a name="appendformat"></a>CStringT::AppendFormat  
 将带格式的数据追加到现有`CStringT`对象。  
  
```  
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```  
  
### <a name="parameters"></a>参数  
 `pszFormat`  
 格式控件字符串。  
  
 `nFormatID`  
 字符串资源标识符，包含窗体控件字符串。  
  
 `argument`  
 可选参数。  
  
### <a name="remarks"></a>备注  
 此函数设置的格式并将追加一系列字符和中的值`CStringT`。 每个可选参数 （如果有） 转换，并根据相应的格式规范中追加`pszFormat`或者从标识的字符串资源`nFormatID`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&107; 页](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]  
  
##  <a name="a-namecollatea--cstringtcollate"></a><a name="collate"></a>CStringT::Collate  
 比较两个字符串使用一般文本函数`_tcscoll`。  
  
```  
int Collate(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 用于比较的其他字符串。  
  
### <a name="return-value"></a>返回值  
 如果字符串是相同的则为零< 0="" if="" this="">`CStringT`对象是小于`psz`，或如果此为 1> 0`CStringT`对象是否大于`psz`。  
  
### <a name="remarks"></a>备注  
 一般文本函数`_tcscoll`，TCHAR 中定义。H、 映射到任何一个`strcoll`， `wcscoll`，或`_mbscoll`，取决于在编译时定义的字符集。 每个函数执行区分大小写的字符串比较根据代码页当前正在使用。 有关详细信息，请参阅[strcoll、 wcscoll、 _mbscoll、 _strcoll_l、 _wcscoll_l、 _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。  
  
##  <a name="a-namecollatenocasea--cstringtcollatenocase"></a><a name="collatenocase"></a>CStringT::CollateNoCase  
 比较两个字符串使用一般文本函数`_tcscoll`。  
  
```  
int CollateNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 用于比较的其他字符串。  
  
### <a name="return-value"></a>返回值  
 零字符串是否完全相同 （忽略大小写） < 0="" if="" this=""> `CStringT`对象是小于`psz`（忽略大小写），或如果此为 1> 0`CStringT`对象是否大于`psz`（忽略大小写）。  
  
### <a name="remarks"></a>备注  
 一般文本函数`_tcscoll`，TCHAR 中定义。H、 映射到任何一个`stricoll`， `wcsicoll`，或`_mbsicoll`，取决于在编译时定义的字符集。 每个函数执行不区分大小写的字符串比较，根据当前正在使用的代码页。 有关详细信息，请参阅[strcoll、 wcscoll、 _mbscoll、 _strcoll_l、 _wcscoll_l、 _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&109;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]  
  
##  <a name="a-namecomparea--cstringtcompare"></a><a name="compare"></a>CStringT::Compare  
 比较两个字符串 （区分大小写）。  
  
```  
int Compare(PCXSTR psz) const; 
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 用于比较的其他字符串。  
  
### <a name="return-value"></a>返回值  
 如果字符串是相同的则为零< 0="" if="" this="">`CStringT`对象是小于`psz`，或如果此为 1> 0`CStringT`对象是否大于`psz`。  
  
### <a name="remarks"></a>备注  
 一般文本函数`_tcscmp`，TCHAR 中定义。H、 映射到任何一个`strcmp`， `wcscmp`，或`_mbscmp`，取决于在编译时定义的字符集。 每个函数执行区分大小写的字符串比较，并不受区域设置。 有关详细信息，请参阅[strcmp、 wcscmp、 _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)。  
  
 如果该字符串包含嵌入的 null，出于比较的字符串被认为在第一个嵌入的 null 字符处截断。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CStringT::Compare` 的用法。  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&110;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]  
  
##  <a name="a-namecomparenocasea--cstringtcomparenocase"></a><a name="comparenocase"></a>CStringT::CompareNoCase  
 比较两个字符串 （不区分大小写）。  
  
```  
int CompareNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 用于比较的其他字符串。  
  
### <a name="return-value"></a>返回值  
 零字符串是否完全相同 （忽略大小写） <0 if="" this=""></0> `CStringT`对象是小于`psz`（忽略大小写） 或&1;>&0;，如果此`CStringT`对象是否大于`psz`（忽略大小写）。  
  
### <a name="remarks"></a>备注  
 一般文本函数`_tcsicmp`，TCHAR 中定义。H、 映射到任何一个`_stricmp`，`_wcsicmp`或`_mbsicmp`，取决于在编译时定义的字符集。 每个函数执行不区分大小写的字符串比较。 取决于比较`LC_CTYPE`方面的区域设置而非`LC_COLLATE`。 有关详细信息，请参阅[_stricmp、 _wcsicmp、 _mbsicmp、 _stricmp_l、 _wcsicmp_l、 _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&111;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]  
  
##  <a name="a-namecstringta--cstringtcstringt"></a><a name="cstringt"></a>CStringT::CStringT  
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
 指向字符数组的长度的指针`nLength`、 不以 null 结尾。  
  
 `nLength`  
 中的字符数的计数`pch`。  
  
 `ch`  
 单个字符。  
  
 `pszSrc`  
 以 null 结尾的字符串复制到此`CStringT`对象。  
  
 `pStringMgr`  
 指向内存管理器为`CStringT`对象。 有关详细信息`IAtlStringMgr`和内存管理`CStringT`，请参阅[使用 CStringT 进行内存管理](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
 `strSrc`  
 现有`CStringT`要复制到此对象`CStringT`对象。 有关详细信息`CThisString`和`CThisSimpleString`，请参阅备注部分。  
  
 `varSrc`  
 变量的对象要复制到此`CStringT`对象。  
  
 `BaseType`  
 此字符串类字符类型。 可以是以下各项之一：  
  
 `char`（针对 ANSI 字符串）。  
  
 `wchar_t`（对于 Unicode 字符串）。  
  
 `TCHAR`（针对 ANSI 和 Unicode 字符串）。  
  
 `bMFCDLL`  
 一个布尔值，指定该项目是 MFC DLL (TRUE) 还是不 (FALSE)。  
  
 `SystemString`  
 必须是`System::String`，并且必须使用 /clr 编译项目。  
  
 `pString`  
 句柄`CStringT`对象。  
  
### <a name="remarks"></a>备注  
 因为构造函数将输入的数据复制到新的已分配存储，您应该知道可能会导致异常的内存。 请注意，某些这些构造函数成为转换函数。 这样可替代，例如，`LPTSTR`其中`CStringT`预期对象。  
  
- `CStringT`( `LPCSTR` `lpsz` ): 构造 Unicode`CStringT`从 ANSI 字符串。 您还可以使用此构造函数中加载字符串资源，如下面的示例中所示。  
  
- `CStringT(``LPCWSTR` `lpsz` ): 构造`CStringT`从 Unicode 字符串。  
  
- `CStringT`( `const unsigned char*` `psz` ): 可用于构建`CStringT`从指针到`unsigned char`。  
  
> [!NOTE]
>  定义**_CSTRING_DISABLE_NARROW_WIDE_CONVERSION**要关闭之间的隐式字符串转换宏[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]和[!INCLUDE[TLA#tla_unicode](../../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]字符串。 从编译构造函数来支持转换中排除该宏。  
  
 请注意，`strSrc`参数可以是`CStringT`或`CThisSimpleString`对象。 有关`CStringT`，使用其默认的实例化之一 ( `CString`， `CStringA`，或`CStringW`); 对于`CThisSimpleString`，使用`this`指针。 `CThisSimpleString`声明的实例[CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)，它是一个较小的字符串类与少于内置功能比`CStringT`类。  
  
 重载运算符`CSimpleStringT<>&()`构造`CStringT`对象从`CSimpleStringT`声明。  
  
> [!NOTE]
>  尽管可能创建`CStringT`实例包含嵌入的 null 字符，我们建议您不要它。 在调用方法和运算符`CStringT`包含嵌入的空字符的对象可能会产生意外的结果。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&112;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]  
  
##  <a name="a-namedtorcstringta--cstringtcstringt"></a><a name="_dtorcstringt"></a>CStringT:: ~ CStringT  
 销毁`CStringT`对象。  
  
```  
~CStringT() throw();
```  
  
### <a name="remarks"></a>备注  
 销毁`CStringT`对象。  
  
##  <a name="a-namedeletea--cstringtdelete"></a><a name="delete"></a>CStringT::Delete  
 从给定索引处的字符开头的字符串中删除一个字符。  
  
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
 如果`nCount`超过了字符串，字符串的其余部分将被删除。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&113;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]  
  
```Output  
Before: Soccer is best,
    but hockey is quicker!  
After: Soccer best,
    but hockey is quicker!  
```  
  
##  <a name="a-namefinda--cstringtfind"></a><a name="find"></a>CStringT::Find  
 此字符串中搜索的字符或子字符串的第一个匹配。  
  
```  
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pszSub`  
 要搜索的子字符串。  
  
 `iStart`  
 在字符串中开始进行搜索或为 0 以从头开始字符的索引。  
  
 `ch`  
 要搜索的单个字符。  
  
### <a name="return-value"></a>返回值  
 在此的第一个字符的从零开始索引`CStringT`与请求的子字符串或字符匹配的对象; 如果未找到子字符串或字符则为-1。  
  
### <a name="remarks"></a>备注  
 该函数将被重载以接受两个单字符 (类似于运行时函数`strchr`) 和字符串 (类似于`strstr`)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&114;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]  
  
##  <a name="a-namefindoneofa--cstringtfindoneof"></a><a name="findoneof"></a>CStringT::FindOneOf  
 此字符串中包含任何字符匹配的第一个字符中搜索`pszCharSet`。  
  
```  
int FindOneOf(PCXSTR pszCharSet) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pszCharSet`  
 包含用于匹配的字符字符串。  
  
### <a name="return-value"></a>返回值  
 也是在此字符串中的第一个字符的从零开始索引`pszCharSet`; 如果没有匹配项的 –&1;。  
  
### <a name="remarks"></a>备注  
 查找任一种情况中的字符的第一个匹配项`pszCharSet`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&115;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]  
  
##  <a name="a-nameformata--cstringtformat"></a><a name="format"></a>CStringT::Format  
 写入格式化的数据写入`CStringT`在同一个方式[sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)设置数据的格式为 C 样式的字符数组。  
  
```  
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```  
  
### <a name="parameters"></a>参数  
 `nFormatID`  
 字符串资源标识符，包含窗体控件字符串。  
  
 `pszFormat`  
 格式控件字符串。  
  
 `argument`  
 可选参数。  
  
### <a name="remarks"></a>备注  
 此函数设置的格式，并将存储一系列字符和中的值`CStringT`。 每个可选参数 （如果有的话） 进行转换和输出中的相应格式规范根据`pszFormat`或者从标识的字符串资源`nFormatID`。  
  
 如果以参数形式向提供的字符串对象本身，则呼叫将失败`Format`。 例如，下面的代码将导致不可预知的结果︰  
  
 [!code-cpp[NVC_ATLMFC_Utilities 排行榜的 #&116;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]  
  
 有关详细信息，请参阅[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&117;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]  
  
##  <a name="a-nameformatmessagea--cstringtformatmessage"></a><a name="formatmessage"></a>CStringT::FormatMessage  
 设置消息字符串的格式。  
  
```  
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```  
  
### <a name="parameters"></a>参数  
 `nFormatID`  
 包含未格式化的消息文本的字符串资源标识符。  
  
 `pszFormat`  
 指向以窗体控件字符串。 它将扫描以查找插入并相应地进行格式化。 格式字符串是类似于运行时函数`printf`-样式格式字符串，但它允许按任意顺序插入的参数。  
  
 `argument`  
 可选参数。  
  
### <a name="remarks"></a>备注  
 此函数需要作为输入的消息定义。 消息定义由`pszFormat`或者从标识的字符串资源`nFormatID`。 该函数将复制到的格式的消息文本`CStringT`处理任何嵌入的对象，如果请求插入序列。  
  
> [!NOTE]
> `FormatMessage`尝试为新格式的字符串分配系统内存。 如果此尝试失败，是自动引发内存异常。  
  
 每次插入必须具有相应的参数以下`pszFormat`或`nFormatID`参数。 消息文本中的动态设置消息的格式支持多个转义序列。 有关详细信息，请参阅 Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) ，此功能在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&118;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]  
  
##  <a name="a-nameformatmessageva--cstringtformatmessagev"></a><a name="formatmessagev"></a>CStringT::FormatMessageV  
 设置使用变量参数列表的消息字符串的格式。  
  
```  
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```  
  
### <a name="parameters"></a>参数  
 `pszFormat`  
 指向以窗体控件字符串。 它将扫描以查找插入并相应地进行格式化。 格式字符串是类似于运行时函数`printf`-样式格式字符串，但它允许按任意顺序插入的参数。  
  
 `pArgList`  
 指向参数列表的指针。  
  
### <a name="remarks"></a>备注  
 此函数需要作为输入，消息定义由`pszFormat`。 该函数将格式的消息文本和变量的参数列表复制`CStringT`处理任何嵌入的对象，如果请求插入序列。  
  
> [!NOTE]
> `FormatMessageV`调用[CStringT::FormatMessage](#formatmessage)，尝试为新格式的字符串分配系统内存。 如果此尝试失败，是自动引发内存异常。  
  
 有关详细信息，请参阅 Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) ，此功能在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameformatva--cstringtformatv"></a><a name="formatv"></a>CStringT::FormatV  
 设置使用变量参数列表的消息字符串的格式。  
  
```  
void FormatV(PCXSTR pszFormat, va_list args);
```  
  
### <a name="parameters"></a>参数  
 `pszFormat`  
 指向以窗体控件字符串。 它将扫描以查找插入并相应地进行格式化。 格式字符串是类似于运行时函数`printf`-样式格式字符串，但它允许按任意顺序插入的参数。  
  
 `args`  
 指向参数列表的指针。  
  
### <a name="remarks"></a>备注  
 将格式化的字符串和可变的参数列表写入`CStringT`中相同的字符串方式`vsprintf_s`设置数据的格式为 C 样式的字符数组。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&119;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&120;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]  
  
##  <a name="a-namegetenvironmentvariablea--cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a>CStringT::GetEnvironmentVariable  
 将字符串设置为指定的环境变量的值。  
  
```  
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```  
  
### <a name="parameters"></a>参数  
 `pszVar`  
 以 null 结尾的字符串，指定环境变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 调用进程的环境块中检索指定的变量的值。 值是字符串的以 null 结尾的字符的形式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&121;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]  
  
##  <a name="a-nameinserta--cstringtinsert"></a><a name="insert"></a>CStringT::Insert  
 在字符串中的给定索引处插入一个字符或子字符串。  
  
```  
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```  
  
### <a name="parameters"></a>参数  
 `iIndex`  
 要在其前面插入会发生的字符的索引。  
  
 `psz`  
 指向要插入的子字符串的指针。  
  
 `ch`  
 要插入的字符。  
  
### <a name="return-value"></a>返回值  
 已更改的字符串的长度。  
  
### <a name="remarks"></a>备注  
 `iIndex`参数标识将被移动，以便腾出空间供字符或子字符串的第一个字符。 如果`nIndex`为零，则插入将发生在整个字符串之前。 如果`nIndex`高于字符串，该函数的长度将串联存在字符串和新材料提供通过以下任一方法`ch`或`psz`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&122;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]  
  
##  <a name="a-namelefta--cstringtleft"></a><a name="left"></a>CStringT::Left  
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
 [!code-cpp[NVC_ATLMFC_Utilities #&123;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]  
  
##  <a name="a-nameloadstringa--cstringtloadstring"></a><a name="loadstring"></a>CStringT::LoadString  
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
 Windows 字符串的资源 id。  
  
 `wLanguageID`  
 包含字符串资源的语言。  
  
### <a name="return-value"></a>返回值  
 如果资源加载成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 加载字符串资源 ( `nID`) 从指定的模块 ( `hInstance`) 使用特定的语言 ( `wLanguage`)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&124;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]  
  
##  <a name="a-namemakelowera--cstringtmakelower"></a><a name="makelower"></a>CStringT::MakeLower  
 将转换`CStringT`对象和小写的字符串。  
  
```  
CStringT& MakeLower();
```  
  
### <a name="return-value"></a>返回值  
 生成的小写字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&125;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]  
  
##  <a name="a-namemakereversea--cstringtmakereverse"></a><a name="makereverse"></a>CStringT::MakeReverse  
 中的字符顺序反转`CStringT`对象。  
  
```  
CStringT& MakeReverse();
```  
  
### <a name="return-value"></a>返回值  
 生成反转字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&126;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]  
  
##  <a name="a-namemakeuppera--cstringtmakeupper"></a><a name="makeupper"></a>CStringT::MakeUpper  
 将转换`CStringT`对象传递给大写的字符串。  
  
```  
CStringT& MakeUpper();
```  
  
### <a name="return-value"></a>返回值  
 生成的大写字符串。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&127;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]  
  
##  <a name="a-namemida--cstringtmid"></a><a name="mid"></a>CStringT::Mid  
 提取子字符串的长度`nCount`字符从此`CStringT`对象，从位置开始`iFirst`（从零开始）。  
  
```  
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const; 
```  
  
### <a name="parameters"></a>参数  
 `iFirst`  
 在此的第一个字符的从零开始索引`CStringT`提取子字符串中包括的对象。  
  
 `nCount`  
 从此 `CStringT` 对象中提取的字符的数量。 如果未提供此参数，然后提取字符串的其余部分。  
  
### <a name="return-value"></a>返回值  
 包含指定范围内的字符的副本的 `CStringT` 对象。 请注意，返回`CStringT`对象可以为空。  
  
### <a name="remarks"></a>备注  
 该函数返回提取的子字符串的副本。 `Mid`类似于基本 Mid 函数 （只是在 Basic 中的索引是基于&1; 的）。  
  
 对于多字节字符集 (MBCS)，`nCount`指的是一个多字节字符被视为两个字符中每个 8 位字符; 也就是说，主管和记录字节。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&128;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]  
  
##  <a name="a-nameoemtoansia--cstringtoemtoansi"></a><a name="oemtoansi"></a>CStringT::OemToAnsi  
 将在此的所有字符都转换`CStringT`ANSI 字符集中的 OEM 字符集中的对象。  
  
```  
void OemToAnsi();
```  
  
### <a name="remarks"></a>备注  
 此功能不可用如果`_UNICODE`定义。  
  
### <a name="example"></a>示例  
 请参阅示例[CStringT::AnsiToOem](#ansitooem)。  
  
##  <a name="a-nameoperatoradda--cstringtoperator-"></a><a name="operator_add"></a>CStringT::operator +  
 串联两个字符串或字符和字符串。  
  
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
 要与字符串串联 ANSI 或 Unicode 字符。  
  
 `ch2`  
 要与字符串串联 ANSI 或 Unicode 字符。  
  
 `str1`  
 一个`CStringT`要串联的字符串或字符。  
  
 `str2`  
 一个`CStringT`要串联的字符串或字符。  
  
 `psz1`  
 指向以 null 结尾的字符串来连接字符串或字符开头的指针。  
  
 `psz2`  
 指向要串联的字符串或字符字符串的指针。  
  
### <a name="remarks"></a>备注  
 有七种重载形式的`CStringT::operator+`函数。 第一个版本串联两个现有`CStringT`对象。 后面的两个连接`CStringT`对象，并以 null 结尾的字符串。 后面的两个连接`CStringT`对象和一个 ANSI 字符。 最后两个连接`CStringT`对象和一个 Unicode 字符。  
  
> [!NOTE]
>  尽管可能创建`CStringT`实例包含嵌入的 null 字符，我们建议您不要它。 在调用方法和运算符`CStringT`包含嵌入的空字符的对象可能会产生意外的结果。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&140;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]  
  
##  <a name="a-nameoperatoraddeqa--cstringtoperator-"></a><a name="operator_add_eq"></a>CStringT::operator + =  
 连接字符串的末尾的字符。  
  
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
 一个布尔值，该值指示项目是否为非 MFC DLL 是否。  
  
 `BaseType`  
 向基于字符串的类型。  
  
 `var`  
 要连接到此字符串的变体对象。  
  
 `ch`  
 要与字符串串联 ANSI 或 Unicode 字符。  
  
 `pszSrc`  
 指向要串联的原始字符串的指针。  
  
 `strSrc`  
 一个`CStringT`要连接到此字符串。  
  
### <a name="remarks"></a>备注  
 运算符可接受另一个`CStringT`对象、 一个字符指针或单个字符。 您应该知道每当您使用此连接运算符，因为新的存储可分配的字符添加到此时，可能会发生异常，内存`CStringT`对象。  
  
 如需有关`CThisSimpleString`，请参阅备注部分的[CStringT::CStringT](#cstringt)。  
  
> [!NOTE]
>  尽管可能创建`CStringT`实例包含嵌入的 null 字符，我们建议您不要它。 在调用方法和运算符`CStringT`包含嵌入的空字符的对象可能会产生意外的结果。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&141;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]  
  
##  <a name="a-nameoperatoreqeqa--cstringtoperator-"></a><a name="operator_eq_eq"></a>CStringT::operator = =  
 确定两个字符串是否在逻辑上相等。  
  
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
 比较 ANSI 或 Unicode 字符。  
  
 `ch2`  
 比较 ANSI 或 Unicode 字符。  
  
 `str1`  
 一个`CStringT`进行比较。  
  
 `str2`  
 一个`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 测试是否字符串或左侧的字符等同于一个字符串或字符在右侧窗格中，并返回 TRUE 或 FALSE 相应地。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&142;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]  
  
##  <a name="a-nameoperatorneqa--cstringtoperator-"></a><a name="operator_neq"></a>CStringT::operator ！ =  
 确定两个字符串是否在逻辑上不相等。  
  
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
 要与字符串串联 ANSI 或 Unicode 字符。  
  
 `ch2`  
 要与字符串串联 ANSI 或 Unicode 字符。  
  
 `str1`  
 一个`CStringT`进行比较。  
  
 `str2`  
 一个`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 测试是否有一个字符串或字符的左侧不等于字符串或右侧的字符。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&143;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]  
  
##  <a name="a-nameoperatorlta--cstringtoperator-lt"></a><a name="operator_lt"></a>CStringT::operator&lt;  
 确定该运算符左侧的字符串是否小于右侧的字符串。  
  
```  
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 一个`CStringT`进行比较。  
  
 `str2`  
 一个`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 直到逐字符的字符串之间按字典序比较︰  
  
-   如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。  
  
-   如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。  
  
-   如果找到的所有字符完全相同且字符串的字符数也相同，则这两个字符串视为相等。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&144;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]  
  
##  <a name="a-nameoperatorgta--cstringtoperator-gt"></a><a name="operator_gt"></a>CStringT::operator&gt;  
 确定该运算符左侧的字符串是否大于右侧的字符串。  
  
```  
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 一个`CStringT`进行比较。  
  
 `str2`  
 一个`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 直到逐字符的字符串之间按字典序比较︰  
  
-   如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。  
  
-   如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。  
  
-   它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&145;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]  
  
##  <a name="a-nameoperatorlteqa--cstringtoperator-lt"></a><a name="operator_lt_eq"></a>CStringT::operator&lt;=  
 确定该运算符左侧的字符串是否小于或等于右侧的字符串。  
  
```  
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 一个`CStringT`进行比较。  
  
 `str2`  
 一个`CStringT`进行比较。  
  
 `psz1`  
 指向以 null 结尾的字符串进行比较的指针。  
  
 `psz2`  
 指向以 null 结尾的字符串进行比较的指针。  
  
### <a name="remarks"></a>备注  
 直到逐字符的字符串之间按字典序比较︰  
  
-   如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。  
  
-   如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。  
  
-   它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&146;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]  
  
##  <a name="a-nameoperatorgteqa--cstringtoperator-gt"></a><a name="operator_gt_eq"></a>CStringT::operator&gt;=  
 确定该运算符左侧的字符串是否大于或等于右侧的字符串。  
  
```  
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 一个`CStringT`进行比较。  
  
 `str2`  
 一个`CStringT`进行比较。  
  
 `psz1`  
 为用于比较的字符串指针。  
  
 `psz2`  
 为用于比较的字符串指针。  
  
### <a name="remarks"></a>备注  
 直到逐字符的字符串之间按字典序比较︰  
  
-   如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。  
  
-   如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。  
  
-   它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&147;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]  
  
##  <a name="a-nameremovea--cstringtremove"></a><a name="remove"></a>CStringT::Remove  
 从字符串中移除指定的字符的所有实例。  
  
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
 [!code-cpp[NVC_ATLMFC_Utilities #&129;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]  
  
##  <a name="a-namereplacea--cstringtreplace"></a><a name="replace"></a>CStringT::Replace  
 有两个版本的`Replace`。第一个版本通过使用另一个子字符串替换子字符串的一个或多个的副本。 两个子字符串是以 null 终止。 第二个版本来使用其他字符替换字符的一个或多个副本。 这两个版本对中存储的字符数据执行操作`CStringT`。  
  
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
 要被替换的字符`chNew`。  
  
 `chNew`  
 字符替换`chOld`。  
  
### <a name="return-value"></a>返回值  
 如果字符串未发生更改时，请返回被替换字符或子字符串，则为零的实例数。  
  
### <a name="remarks"></a>备注  
 `Replace`可以更改的字符串长度，因为`pszNew`和`pszOld`旧子字符串的多个副本可以变为新并不一定要相同长度。 此函数将执行区分大小写的匹配项。  
  
 示例`CStringT`实例`CString`， `CStringA`，和`CStringW`。  
  
 有关`CStringA`， `Replace` ANSI 或多字节 (MBCS) 字符配合工作。 有关`CStringW`，`Replace`配合宽字符。  
  
 有关`CString`，字符数据类型在编译时，根据选择是否定义下表中的常量。  
  
|定义的常量|字符数据类型|  
|----------------------|-------------------------|  
|`_UNICODE`|宽字符|  
|`_MBCS`|多字节字符|  
|均不|单字节字符|  
|消息和传送|未定义|  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&200;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]  
  
##  <a name="a-namereversefinda--cstringtreversefind"></a><a name="reversefind"></a>CStringT::ReverseFind  
 搜索此`CStringT`字符的最后一个匹配的对象。  
  
```  
int ReverseFind(XCHAR ch) const throw();
```  
  
### <a name="parameters"></a>参数  
 `ch`  
 要搜索的字符。  
  
### <a name="return-value"></a>返回值  
 在此的最后一个字符的从零开始索引`CStringT`匹配所请求的字符集，则返回 –&1;，如果未找到该字符的对象。  
  
### <a name="remarks"></a>备注  
 该函数是类似于运行时函数`strrchr`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&130;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]  
  
##  <a name="a-namerighta--cstringtright"></a><a name="right"></a>CStringT::Right  
 提取上一次 (即最右边)`nCount`字符从此`CStringT`对象并返回提取的子字符串的副本。  
  
```  
CStringT Right(int nCount) const; 
```  
  
### <a name="parameters"></a>参数  
 `nCount`  
 从此 `CStringT` 对象中提取的字符的数量。  
  
### <a name="return-value"></a>返回值  
 包含指定范围内的字符的副本的 `CStringT` 对象。 请注意，返回`CStringT`对象可以为空。  
  
### <a name="remarks"></a>备注  
 如果 `nCount` 超过了字符串长度，则提取整个字符串。 `Right`是类似于 Basic`Right`函数 （只不过在 Basic 中的索引是从零开始）。  
  
 对于多字节字符集 (MBCS)，`nCount`指的是一个多字节字符被视为两个字符中每个 8 位字符; 也就是说，主管和记录字节。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&131;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]  
  
##  <a name="a-namesetsysstringa--cstringtsetsysstring"></a><a name="setsysstring"></a>CStringT::SetSysString  
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
 具体取决于内容`CStringT`对象、 的值`BSTR`所引用的`pbstr`可以更改。 该函数将引发`CMemoryException`如果内存不足，无法存在。  
  
 此函数通常用于更改用于自动化通过引用传递的字符串值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&132;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]  
  
##  <a name="a-namespanexcludinga--cstringtspanexcluding"></a><a name="spanexcluding"></a>CStringT::SpanExcluding  
 提取的字符开头的第一个字符，不是由标识的字符集的字符串`pszCharSet`。  
  
```  
CStringT SpanExcluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>参数  
 `pszCharSet`  
 字符串解释为一组字符。  
  
### <a name="return-value"></a>返回值  
 包含不在字符串中的字符的子字符串`pszCharSet`，以在字符串中的第一个字符开头，也是在字符串中找到的第一个字符结束`pszCharSet`(即，从第一个字符在字符串中和截至但不包括所找到的字符串中的第一个字符开始`pszCharSet`)。 它将返回整个字符串，如果在没有字符`pszCharSet`字符串中找到。  
  
### <a name="remarks"></a>备注  
 `SpanExcluding`提取并返回前面的字符集中的第一个匹配项的所有字符`pszCharSet`(换句话说，从字符`pszCharSet`并不会返回在字符串内，之后的所有字符)。 如果从没有字符`pszCharSet`在字符串中，然后找到`SpanExcluding`返回整个字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&133;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]  
  
##  <a name="a-namespanincludinga--cstringtspanincluding"></a><a name="spanincluding"></a>CStringT::SpanIncluding  
 提取的字符开头的第一个字符，位于由标识的字符集的字符串`pszCharSet`。  
  
```  
CStringT SpanIncluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>参数  
 `pszCharSet`  
 字符串解释为一组字符。  
  
### <a name="return-value"></a>返回值  
 包含在字符串中的字符的子字符串`pszCharSet`，从字符串中的第一个字符开始和结束时将不在字符串中找到的字符`pszCharSet`。 `SpanIncluding`如果在字符串中的第一个字符不在指定的集，则返回空的子字符串。  
  
### <a name="remarks"></a>备注  
 如果该字符串的第一个字符不在的字符集，然后`SpanIncluding`返回一个空字符串。 否则，它将返回集中的连续字符的序列。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&134;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]  
  
##  <a name="a-nametokenizea--cstringttokenize"></a><a name="tokenize"></a>CStringT::Tokenize  
 在目标字符串中查找下一个令牌  
  
```  
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const; 
```  
  
### <a name="parameters"></a>参数  
 `pszTokens`  
 包含标记分隔符的字符串。 这些分隔符的顺序并不重要。  
  
 `iStart`  
 要开始搜索的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 一个`CStringT`对象，它包含当前的令牌值。  
  
### <a name="remarks"></a>备注  
 `Tokenize`函数在目标字符串中查找下一个令牌。 中的字符的一套`pszTokens`指定可能要找的标记分隔符。 每次调用`Tokenize`函数开始处`iStart`、 跳过前导分隔符，并返回`CStringT`对象，它包含当前令牌，该字符串的下一步的分隔符字符之前的字符字符串。 值`iStart`更新以便之后结束的分隔符字符，则为-1，如果已到达字符串末尾的位置。 多个标记超出目标字符串的其余部分都可以通过调用一系列分解`Tokenize`，并使用`iStart`来跟踪在字符串的下一个标记为要读取的位置。 当没有更多标记该函数将返回一个空字符串和`iStart`将设置为-1。  
  
 与不同的 CRT 标记功能，如[strtok_s、 _strtok_s_l、 wcstok_s、 _wcstok_s_l、 _mbstok_s、 _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)，`Tokenize`不会修改目标字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&135;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]  
  
### <a name="remarks"></a>备注  
 此示例的输出是，如下所示︰  
  
 `Resulting Token: First`  
  
 `Resulting Token: Second`  
  
 `Resulting Token: Third`  
  
##  <a name="a-nametrima--cstringttrim"></a><a name="trim"></a>CStringT::Trim  
 修剪前导空格和尾随字符的字符串。  
  
```  
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```  
  
### <a name="parameters"></a>参数  
 `chTarget`  
 要修整目标字符。  
  
 `pszTargets`  
 指向包含目标字符要修整的字符串的指针。 所有前导空格和尾随匹配项中的字符`pszTarget`将从削减`CStringT`对象。  
  
### <a name="return-value"></a>返回值  
 返回裁剪后的字符串。  
  
### <a name="remarks"></a>备注  
 移除所有前导和尾随空白以下项之一︰  
  
-   由指定的字符`chTarget.`  
  
-   通过指定的字符串中找到的所有字符`pszTargets.`  
  
-   空格。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&136;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]  
  
### <a name="remarks"></a>备注  
 此示例的输出是，如下所示︰  
  
 `Before: "******Soccer is best, but liquor is quicker!!!!!"`  
  
 `After : "Soccer is best, but liquor is quicker"`  
  
##  <a name="a-nametrimlefta--cstringttrimleft"></a><a name="trimleft"></a>CStringT::TrimLeft  
 修剪前导字符的字符串。  
  
```  
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```  
  
### <a name="parameters"></a>参数  
 `chTarget`  
 要修整目标字符。  
  
 `pszTargets`  
 指向包含目标字符要修整的字符串的指针。 中的字符的所有前导匹配项`pszTarget`将从削减`CStringT`对象。  
  
### <a name="return-value"></a>返回值  
 生成裁剪后的字符串。  
  
### <a name="remarks"></a>备注  
 移除所有前导和尾随空白以下项之一︰  
  
-   由指定的字符`chTarget.`  
  
-   通过指定的字符串中找到的所有字符`pszTargets.`  
  
-   空格。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&137;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]  
  
##  <a name="a-nametrimrighta--cstringttrimright"></a><a name="trimright"></a>CStringT::TrimRight  
 剪裁尾随字符的字符串。  
  
```  
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```  
  
### <a name="parameters"></a>参数  
 `chTarget`  
 要修整目标字符。  
  
 `pszTargets`  
 指向包含目标字符要修整的字符串的指针。 所有尾部匹配项中的字符`pszTarget`将从削减`CStringT`对象。  
  
### <a name="return-value"></a>返回值  
 返回`CStringT`对象，其中包含裁剪后的字符串。  
  
### <a name="remarks"></a>备注  
 删除尾随匹配项的以下项之一︰  
  
-   由指定的字符`chTarget.`  
  
-   通过指定的字符串中找到的所有字符`pszTargets.`  
  
-   空格。  
  
 `CStringT& TrimRight(XCHAR chTarget)`版本接受一个字符参数，并删除该字符的所有副本的末尾`CStringT`字符串数据。 它从字符串末尾开始，到队的工作。 当它找到一个不同的角色或停止`CSTringT`不足字符数据。  
  
 `CStringT& TrimRight(PCXSTR pszTargets)`版本接受包含所有不同的字符要搜索的以 null 结尾的字符串。 它会删除这些字符中的所有副本`CStringT`对象。 它从字符串末尾开始并向您提供前面。 它将停止它查找不是目标字符串中字符或时`CStringT`不足字符数据。 它不会尝试匹配整个目标字符串末尾的子字符串到`CStringT`。  
  
 `CStringT& TrimRight()`版本不需要任何参数。 剪裁任何尾随空格字符结尾处`CStringT`字符串。 空白字符可以是换行符、 空格或制表符。  
  
-  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&138;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)   
 [CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)



