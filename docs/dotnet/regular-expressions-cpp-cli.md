---
title: 正则表达式 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
- .NET Framework [C++], regular expressions
- regular expressions [C++], about regular expressions
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
- substrings, simple matches
- searching, exact substring matches
- strings [C++], exact substring matching
- regular expressions [C++], simple matching
- IsMatch method
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
- regular expressions [C++], rearranging data
- data [C++], rearranging
- search and replace
- Replace method
- regular expressions [C++], search and replace
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 838bab49-0dbc-4089-a604-ef146269ef5a
ms.openlocfilehash: 24a278e4d5b208c5d8e3b95b9f5a0bd0306dbab3
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741905"
---
# <a name="regular-expressions-ccli"></a>正则表达式 (C++/CLI)

演示如何使用.NET Framework 中的正则表达式类的各种字符串操作。

以下主题演示如何使用.NET framework<xref:System.Text.RegularExpressions>命名空间 (在一个用例<xref:System.String.Split%2A?displayProperty=fullName>方法) 若要搜索，分析数据并修改字符串。

## <a name="parse_regex"></a> 使用正则表达式分析字符串

下面的代码示例演示如何使用简单的字符串分析<xref:System.Text.RegularExpressions.Regex>类中<xref:System.Text.RegularExpressions?displayProperty=fullName>命名空间。 构造一个包含多个类型的字描绘的字符串。 然后使用分析的字符串<xref:System.Text.RegularExpressions.Regex>类结合<xref:System.Text.RegularExpressions.Match>类。 然后，分别显示在句子中的每个单词。

### <a name="example"></a>示例

```cpp
// regex_parse.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main( )
{
   int words = 0;
   String^ pattern = "[a-zA-Z]*";
   Console::WriteLine( "pattern : '{0}'", pattern );
   Regex^ regex = gcnew Regex( pattern );

   String^ line = "one\ttwo three:four,five six  seven";
   Console::WriteLine( "text : '{0}'", line );
   for( Match^ match = regex->Match( line );
        match->Success; match = match->NextMatch( ) )
   {
      if( match->Value->Length > 0 )
      {
         words++;
         Console::WriteLine( "{0}", match->Value );
      }
   }
   Console::WriteLine( "Number of Words : {0}", words );

   return 0;
}
```

## <a name="parse_split"></a> 使用 Split 方法分析字符串

下面的代码示例演示了如何使用<xref:System.String.Split%2A?displayProperty=fullName>方法以从字符串中提取每个单词。 包含多个类型的字描绘的字符串是构造，然后通过调用分析<xref:System.String.Split%2A>描绘的列表。 然后，分别显示在句子中的每个单词。

### <a name="example"></a>示例

```cpp
// regex_split.cpp
// compile with: /clr
using namespace System;

int main()
{
   String^ delimStr = " ,.:\t";
   Console::WriteLine( "delimiter : '{0}'", delimStr );
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ words;
   String^ line = "one\ttwo three:four,five six seven";

   Console::WriteLine( "text : '{0}'", line );
   words = line->Split( delimiter );
   Console::WriteLine( "Number of Words : {0}", words->Length );
   for (int word=0; word<words->Length; word++)
      Console::WriteLine( "{0}", words[word] );

   return 0;
}
```

## <a name="regex_simple"></a> 使用正则表达式用于简单匹配

下面的代码示例使用正则表达式来查找确切的子字符串匹配项。 由静态执行搜索<xref:System.Text.RegularExpressions.Regex.IsMatch%2A>方法，它使用两个字符串作为输入。 第一个是要搜索的字符串和第二个是要在其中搜索的模式。

### <a name="example"></a>示例

```cpp
// regex_simple.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
   array<String^>^ sentence =
   {
      "cow over the moon",
      "Betsy the Cow",
      "cowering in the corner",
      "no match here"
   };

   String^ matchStr = "cow";
   for (int i=0; i<sentence->Length; i++)
   {
      Console::Write( "{0,24}", sentence[i] );
      if ( Regex::IsMatch( sentence[i], matchStr,
                     RegexOptions::IgnoreCase ) )
         Console::WriteLine("  (match for '{0}' found)", matchStr);
      else
         Console::WriteLine("");
   }
   return 0;
}
```

## <a name="regex_extract"></a> 使用正则表达式提取数据字段

下面的代码示例演示如何将正则表达式来从带格式字符串中提取数据。 下面的代码示例使用<xref:System.Text.RegularExpressions.Regex>类指定为电子邮件地址相对应的模式。 此模式包括可用于检索用户和主机名部分的每个电子邮件地址的字段标识符。 <xref:System.Text.RegularExpressions.Match>类用于执行实际的模式匹配。 如果给定的电子邮件地址是否有效，被提取和显示的用户名和主机名。

### <a name="example"></a>示例

```cpp
// Regex_extract.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
    array<String^>^ address=
    {
        "jay@southridgevideo.com",
        "barry@adatum.com",
        "treyresearch.net",
        "karen@proseware.com"
    };

    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");

    for (int i=0; i<address->Length; i++)
    {
        Match^ m = emailregex->Match( address[i] );
        Console::Write("\n{0,25}", address[i]);

        if ( m->Success )
        {
            Console::Write("   User='{0}'",
            m->Groups["user"]->Value);
            Console::Write("   Host='{0}'",
            m->Groups["host"]->Value);
        }
        else
            Console::Write("   (invalid email address)");
        }

    Console::WriteLine("");
    return 0;
}
```

## <a name="regex_rearrange"></a> 使用正则表达式重新排列数据

下面的代码示例演示如何使用.NET Framework 正则表达式支持可以重新排列，或重新设置数据格式。 下面的代码示例使用<xref:System.Text.RegularExpressions.Regex>和<xref:System.Text.RegularExpressions.Match>类，以从字符串中提取第一个和最后一个名称，然后按相反的顺序显示这些名称元素。

<xref:System.Text.RegularExpressions.Regex>类用于构造描述了当前的数据格式的正则表达式。 这两个名称被假定由逗号分隔，且可使用任何数量的逗号周围的空白区域。 <xref:System.Text.RegularExpressions.Match>方法然后用来分析每个字符串。 如果成功，将从检索第一个和最后一个名称<xref:System.Text.RegularExpressions.Match>对象，并显示。

### <a name="example"></a>示例

```cpp
// regex_reorder.cpp
// compile with: /clr
#using <System.dll>
using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ name =
   {
      "Abolrous, Sam",
      "Berg,Matt",
      "Berry , Jo",
      "www.contoso.com"
   };

   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");

   for ( int i=0; i < name->Length; i++ )
   {
      Console::Write( "{0,-20}", name[i] );
      Match^ m = reg->Match( name[i] );
      if ( m->Success )
      {
         String^ first = m->Groups["first"]->Value;
         String^ last = m->Groups["last"]->Value;
         Console::WriteLine("{0} {1}", first, last);
      }
      else
         Console::WriteLine("(invalid)");
   }
   return 0;
}
```

## <a name="regex_search"></a> 使用正则表达式进行搜索和替换

下面的代码示例演示如何在正则表达式类<xref:System.Text.RegularExpressions.Regex>可用于执行搜索和替换。 这通过<xref:System.Text.RegularExpressions.Regex.Replace%2A>方法。 所使用的版本将作为输入的两个字符串： 要进行修改的字符串和字符串 （如果有） 来代替，部分要插入到给定模式相匹配<xref:System.Text.RegularExpressions.Regex>对象。

此代码在字符串中的所有数字都替换为下划线 (_)，然后将都替换具有空字符串，有效地删除它们。 可以在单个步骤中，完成相同的效果，但出于演示目的此处使用两个步骤。

### <a name="example"></a>示例

```cpp
// regex_replace.cpp
// compile with: /clr
#using <System.dll>
using namespace System::Text::RegularExpressions;
using namespace System;

int main()
{
   String^ before = "The q43uick bro254wn f0ox ju4mped";
   Console::WriteLine("original  : {0}", before);

   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");
   String^ after = digitRegex->Replace(before, "_");
   Console::WriteLine("1st regex : {0}", after);

   Regex^ underbarRegex = gcnew Regex("_");
   String^ after2 = underbarRegex->Replace(after, "");
   Console::WriteLine("2nd regex : {0}", after2);

   return 0;
}
```

## <a name="regex_validate"></a> 使用正则表达式验证数据格式

下面的代码示例演示如何将正则表达式来验证一个字符串的格式设置。 在下面的代码示例，该字符串应包含有效的电话号码。 下面的代码示例使用字符串"\d{3}-\d{3}-\d{4}"指示每个字段表示有效的电话号码。 在字符串中的"d"指示一个数字，并后每个"d"参数指示必须存在的数字个数。 在这种情况下，数字时需要用短划线分隔。

### <a name="example"></a>示例

```cpp
// regex_validate.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ number =
   {
      "123-456-7890",
      "444-234-22450",
      "690-203-6578",
      "146-893-232",
      "146-839-2322",
      "4007-295-1111",
      "407-295-1111",
      "407-2-5555",
   };

   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";

   for ( int i = 0; i < number->Length; i++ )
   {
      Console::Write( "{0,14}", number[i] );

      if ( Regex::IsMatch( number[i], regStr ) )
         Console::WriteLine(" - valid");
      else
         Console::WriteLine(" - invalid");
   }
   return 0;
}
```

## <a name="related-sections"></a>相关章节

[.NET Framework 正则表达式](/dotnet/standard/base-types/regular-expressions)

## <a name="see-also"></a>请参阅

[使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
