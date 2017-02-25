---
title: "CStringT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CString"
  - "CStringT"
  - "ATL::CStringT"
  - "ATL.CStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringT class"
  - "shared classes, CStringT"
  - "字符串 [C++], 在 ATL 中"
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 34
---
# CStringT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示 `CStringT` 对象。  
  
## 语法  
  
```  
  
      template< typename   
      BaseType  
      , class   
      StringTraits  
       >  
class CStringT :   
public CSimpleStringT<   BaseType,   _CSTRING_IMPL_::_MFCDLLTraitsCheck<      BaseType,      StringTraits   >   ::c_bIsMFCDLLTraits>  
```  
  
#### 参数  
 `BaseType`  
 字符串选件类的字符类型。  可以是如下内容之一：  
  
-   `char` \(对于ANSI字符字符串）。  
  
-   `wchar_t` \(对于Unicode字符串）。  
  
-   **TCHAR** \(对于ANSI和Unicode字符串）。  
  
 `StringTraits`  
 确定字符串选件类是否需要C运行时\(CRT\)库支持，并且位于的位置字符串资源。  可以是如下内容之一：  
  
-   **strtraitatl\< wchar\_t** &#124; `char` &#124; **TCHAR，chtraitscrt\< wchar\_t** &#124; `char` &#124; **TCHAR \> \>**  
  
     选件类需要CRT支持和 `m_hInstResource` 模块中的资源字符串指定搜索\(应用程序模块选件类的成员）。  
  
-   **strtraitatl\< wchar\_t** &#124; `char` &#124; **TCHAR，chtraitsos\< wchar\_t** &#124; `char` &#124; **TCHAR \> \>**  
  
     选件类不需要CRT支持和 `m_hInstResource` 模块中的资源字符串指定搜索\(应用程序模块选件类的成员）。  
  
-   **strtraitmfc\< wchar\_t** &#124; `char` &#124; **TCHAR，chtraitscrt\< wchar\_t** &#124; `char` &#124; **TCHAR \> \>**  
  
     使用标准MFC搜索算法，选件类需要CRT支持和搜索资源字符串。  
  
-   **strtraitmfc\< wchar\_t** &#124; `char` &#124; **TCHAR，chtraitsos\< wchar\_t** &#124; `char` &#124; **TCHAR \> \>**  
  
     使用标准MFC搜索算法，选件类不需要CRT支持和搜索资源字符串。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CStringT::CStringT](../Topic/CStringT::CStringT.md)|构造一个 `CStringT` 对象以多种方式。|  
|[CStringT::~CStringT](../Topic/CStringT::~CStringT.md)|销毁 `CStringT` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CStringT::AllocSysString](../Topic/CStringT::AllocSysString.md)|从 `CStringT` 数据分配 `BSTR`。|  
|[CStringT::AnsiToOem](../Topic/CStringT::AnsiToOem.md)|由ANSI字符集进行就地转换为OEM字符集。|  
|[CStringT::AppendFormat](../Topic/CStringT::AppendFormat.md)|向现有 `CStringT` 对象的Appends设置数据格式。|  
|[CStringT::Collate](../Topic/CStringT::Collate.md)|比较两个字符串\(区分大小写，使用区域设置特定信息）。|  
|[CStringT::CollateNoCase](../Topic/CStringT::CollateNoCase.md)|比较两个字符串\(不区分大小写，使用区域设置特定信息）。|  
|[CStringT::Compare](../Topic/CStringT::Compare.md)|比较两个字符串\(区分大小写）。|  
|[CStringT::CompareNoCase](../Topic/CStringT::CompareNoCase.md)|比较两个字符串\(不区分大小写）。|  
|[CStringT::Delete](../Topic/CStringT::Delete.md)|从字符串中删除字符或字符。|  
|[CStringT::Find](../Topic/CStringT::Find.md)|查找某个字符或子字符串在一个更大的字符串中。|  
|[CStringT::FindOneOf](../Topic/CStringT::FindOneOf.md)|查找从的第一个匹配的字符集。|  
|[CStringT::Format](../Topic/CStringT::Format.md)|来设置字符串格式，`sprintf`。|  
|[CStringT::FormatMessage](../Topic/CStringT::FormatMessage.md)|格式化消息字符串。|  
|[CStringT::FormatMessageV](../Topic/CStringT::FormatMessageV.md)|格式化消息字符串使用变量参数列表。|  
|[CStringT::FormatV](../Topic/CStringT::FormatV.md)|来设置字符串格式使用变量参数列表。|  
|[CStringT::GetEnvironmentVariable](../Topic/CStringT::GetEnvironmentVariable.md)|将字符串到指定的环境变量的值。|  
|[CStringT::Insert](../Topic/CStringT::Insert.md)|插入单个字符或一个子字符串在给定索引字符串中。|  
|[CStringT::Left](../Topic/CStringT::Left.md)|提取字符串的左侧部分。|  
|[CStringT::LoadString](../Topic/CStringT::LoadString.md)|从Windows资源加载现有 `CStringT` 对象。|  
|[CStringT::MakeLower](../Topic/CStringT::MakeLower.md)|转换在此字符串中的所有字符转换为小写字母。|  
|[CStringT::MakeReverse](../Topic/CStringT::MakeReverse.md)|反转该字符串。|  
|[CStringT::MakeUpper](../Topic/CStringT::MakeUpper.md)|转换在此字符串中的所有字符转换为大写字符。|  
|[CStringT::Mid](../Topic/CStringT::Mid.md)|提取字符串的中心部分。|  
|[CStringT::OemToAnsi](../Topic/CStringT::OemToAnsi.md)|由OEM字符集进行就地转换为ANSI字符集。|  
|[CStringT::Remove](../Topic/CStringT::Remove.md)|移除指示从字符串中的字符。|  
|[CStringT::Replace](../Topic/CStringT::Replace.md)|replaces指示字符与其他字符。|  
|[CStringT::ReverseFind](../Topic/CStringT::ReverseFind.md)|查找在较大字符串中的字符;从末尾开始。|  
|[CStringT::Right](../Topic/CStringT::Right.md)|提取字符串的正确部分。|  
|[CStringT::SetSysString](../Topic/CStringT::SetSysString.md)|设置与数据的现有 `BSTR` 对象从 `CStringT` 对象。|  
|[CStringT::SpanExcluding](../Topic/CStringT::SpanExcluding.md)|从字符串中提取字符，从第一个字符开头，没有在 `pszCharSet`确定的字符集。|  
|[CStringT::SpanIncluding](../Topic/CStringT::SpanIncluding.md)|将设置为仅包含字符的子字符串。|  
|[CStringT::Tokenize](../Topic/CStringT::Tokenize.md)|提取在目标字符串中指定标记。|  
|[CStringT::Trim](../Topic/CStringT::Trim.md)|调整从字符串中所有前导和尾随空格字符。|  
|[CStringT::TrimLeft](../Topic/CStringT::TrimLeft.md)|生成空白字符的去除字符串。|  
|[CStringT::TrimRight](../Topic/CStringT::TrimRight.md)|调整从字符串中拖尾空白字符。|  
  
### 运算符  
  
|||  
|-|-|  
|[CStringT::operator \=](../Topic/CStringT::operator%20=.md)|赋新值。`CStringT` 对象。|  
|[CStringT::operator \+](../Topic/CStringT::operator%20+.md)|串联两个字符串或字符和字符串。|  
|[CStringT::operator \+\=](../Topic/CStringT::operator%20+=.md)|连接一个新字符串为现有字符串的末尾。|  
|[CStringT::operator \=\=](../Topic/CStringT::operator%20==.md)|确定两个字符串是否在逻辑上是相等。|  
|[CStringT::operator \!\=](../Topic/CStringT::operator%20!=.md)|确定两个字符串是否不逻辑上是相等。|  
|[CStringT::operator \<](../Topic/CStringT::operator%20%3C.md)|确定在运算符左侧的字符串是否小于对于右侧的字符串。|  
|[CStringT::operator \>](../Topic/CStringT::operator%20%3E.md)|确定在运算符左侧的字符串是否大于对于右侧的字符串。|  
|[CStringT::operator \<\=](../Topic/CStringT::operator%20%3C=.md)|确定在运算符左侧的字符串是否小于或等于右侧的字符串。|  
|[CStringT::operator \>\=](../Topic/CStringT::operator%20%3E=.md)|确定在运算符左侧的字符串是否大于或等于右侧的字符串。|  
  
## 备注  
 `CStringT` 从 [CSimpleStringT选件类](../../atl-mfc-shared/reference/csimplestringt-class.md)继承。  高级功能，如个性纵容，排序和搜索，由 `CStringT`实现。  
  
> [!NOTE]
>  `CStringT` 对象能够引发异常。  当 `CStringT` 对象由于某种原因，内存不足发生此错误。  
  
 `CStringT` 对象包括字符的可变序列。  `CStringT` 提供使用语法的函数和运算符类似于基本。  串联和比较运算符，与简化的内存管理时，比普通字符数组使 `CStringT` 对象易于使用。  
  
> [!NOTE]
>  尽管创建包含嵌入式null字符的 `CStringT` 实例是可能的，但建议这样做。  调用方法和运算符包含嵌入式null字符的 `CStringT` 对象的可能导致意外的结果。  
  
 使用 `BaseType` 和 `StringTraits` 参数的不同组合，`CStringT` 对象可以从以下类型，是由ATL库预定义的。  
  
 如果对ATL应用程序:  
  
 `CString`、 `CStringA`和 `CStringW` 从MFC DLL \(MFC90.DLL\)导出，决不从用户DLL。  这样做是为了防止 `CStringT` 被多次定义。  
  
> [!NOTE]
>  如果遇到链接器错误，则导出 `CString`\-从MFC扩展DLL的派生类在Visual C\+\+ .NET 2002中时和应用工作区如知识库文章所述，“链接错误，当您导入CString派生的选件类”时\(Q309801\)，应移除工作区，代码，因为这在Visual C\+\+ .NET已修复2003。  知识库文章位于 MSDN Library CD\-ROM 中或 [http:\/\/support.microsoft.com\/default.aspx?ln\=zh\-cn](http://support.microsoft.com/default.aspx?ln=zh-cn) 上。  
  
 下面的字符串类型在基于MFC的应用程序中可用:  
  
|CStringT类型|声明|  
|----------------|--------|  
|`CStringA`|使用CRT中的ANSI字符类型字符串支持。|  
|`CStringW`|使用CRT的一个Unicode字符类型字符串支持。|  
|`CString`|ANSI和Unicode字符类型与CRT支持。|  
  
 下面的字符串类型可在 **ATL\_CSTRING\_NO\_CRT** 定义的项:  
  
|CStringT类型|声明|  
|----------------|--------|  
|**CAtlStringA**|无CRT中的ANSI字符类型字符串支持。|  
|**CAtlStringW**|无CRT的一个Unicode字符类型字符串支持。|  
|**CAtlString**|ANSI和Unicode字符类型无CRT支持。|  
  
 下面的字符串类型可在 **ATL\_CSTRING\_NO\_CRT** 未定义的项:  
  
|CStringT类型|声明|  
|----------------|--------|  
|**CAtlStringA**|使用CRT中的ANSI字符类型字符串支持。|  
|**CAtlStringW**|使用CRT的一个Unicode字符类型字符串支持。|  
|**CAtlString**|ANSI和Unicode字符类型与CRT支持。|  
  
 `CString` 对象还具有下列特性:  
  
-   由于串联运算，`CStringT` 对象可以增大。  
  
-   `CStringT` 对象在“值语义”。其视为 `CStringT` 对象作为实际字符串，不是指向字符串。  
  
-   可以使用 `PCXSTR` 函数参数自由地替换 `CStringT` 对象。  
  
-   字符串缓冲区的自定义内存管理。  有关更多信息，请参见 [内存管理和CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## CStringT预定义类型  
 由于 `CStringT` 使用模板参数定义\( [wchar\_t](../../c-runtime-library/standard-types.md) 或 [字符](../../c-runtime-library/standard-types.md)\)支持的字符类型，方法参数类型可以经常问题。  为了简化此问题，一组预定义的类型定义和使用在 `CStringT` 选件类中。  下表列出了各种类型:  
  
|名称|说明|  
|--------|--------|  
|`XCHAR`|单个字符\( `wchar_t` 或 `char`\)与字符类型和 `CStringT` 对象相同。|  
|**YCHAR**|单个字符\( `wchar_t` 或 `char`\)与相反的字符类型作为 `CStringT` 对象。|  
|`PXSTR`|对字符字符串的指针\( `wchar_t` 或 `char`\)与字符类型和 `CStringT` 对象相同。|  
|**PYSTR**|对字符字符串的指针\( `wchar_t` 或 `char`\)与相反的字符类型作为 `CStringT` 对象。|  
|`PCXSTR`|为 **const** 字符字符串的指针\( `wchar_t` 或 `char`\)与字符类型和 `CStringT` 对象相同。|  
|**PCYSTR**|为 **const** 字符字符串的指针\( `wchar_t` 或 `char`\)与相反的字符类型作为 `CStringT` 对象。|  
  
> [!NOTE]
>  代码必须使用 `CStringT` 以下文档的方法中的代码替换 `CString` 以前使用过的未记录的方法\(例如 **AssignCopy**\) \(例如 `GetBuffer` 或 `ReleaseBuffer`）。  这些方法从 `CSimpleStringT`继承。  
  
## 继承层次结构  
 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)  
  
 `CStringT`  
  
## 要求  
  
|Header|用途|  
|------------|--------|  
|cstringt.h|MFC字符串对象|  
|atlstr.h|非MFC字符串对象|  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)   
 [CSimpleStringT Class](../../atl-mfc-shared/reference/csimplestringt-class.md)