---
title: CLR 枚举类型 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scope, of CLR enum
- enum struct keyword [C++]
- enum class keyword [C++]
ms.assetid: 4541d952-97bb-4e35-a7f8-d14f5f6a6606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2416a306373db08c5e925b4987fc8a9273973c39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111492"
---
# <a name="clr-enum-type"></a>CLR 枚举类型
声明和行为的枚举已从更改托管扩展的 c + + 为 Visual c + +。  
  
 托管扩展枚举声明前都附有`__value`关键字。 本指南旨在从该类派生自的 CLR 枚举区分本机枚举`System::ValueType`，同时建议类似的功能。 例如：  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};  
```  
  
 新语法中解决的问题区分本机和 CLR 枚举了通过强调后者而不是其值类型根的类特性。 在这种情况下，`__value`关键字将被丢弃，替换为空格分隔的关键字对`enum class`。 这提供了配对的关键字对称的引用、 值和接口类的声明：  
  
```  
enum class ec;  
value class vc;  
ref class rc;  
interface class ic;  
```  
  
 枚举对翻译`e1`和`e2`的新语法中将如下所示：  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 除了此小语法更改后，CLR 枚举类型的行为已更改多种方式：  
  
-   不再支持的 CLR 枚举的前向声明。 没有映射。 它只被标记编译时错误。  
  
```  
__value enum status; // Managed Extensions: ok  
enum class status;   // new syntax: error  
```  
  
-   内置算术类型之间的重载解决方案和`Object`类层次结构中的两个语言版本相反 ！ 作为其副作用是，CLR 枚举将不再隐式转换为算术类型。  
  
-   在新语法中，CLR 枚举维护自己的作用域，不是这种情况在托管扩展。 以前，枚举器可在枚举包含作用域内可见。 现在，枚举的作用域内封装了枚举数。  
  
## <a name="clr-enums-are-a-kind-of-object"></a>CLR 枚举是一个类型的对象  
 考虑以下代码片断：  
  
```  
__value enum status { fail, pass };  
  
void f( Object* ){ Console::WriteLine("f(Object)\n"); }  
void f( int ){ Console::WriteLine("f(int)\n"); }  
  
int main()  
{  
   status rslt = fail;  
  
   f( rslt ); // which f is invoked?  
}  
```  
  
 为本机 c + + 程序员，自然问题答案的重载的哪个实例`f()`调用是`f(int)`。 枚举是符号的整型常量，并且它参与标准的整型提升，这种情况下优先。  但实际上在托管扩展中此调用将解析的实例。 不是当我们使用本机 c + + 在框架中的但在我们需要它们与现有的 BCL （基类库） 框架进行交互时，这会导致意外的发生的许多其中`Enum`派生的类间接从`Object`。 在 Visual c + + 语言设计中，实例`f()`调用是`f(Object^)`。  
  
 Visual c + + 已选来强制执行此方法是不支持 CLR 枚举类型和算术类型之间的隐式转换。 这意味着任何分配到算术类型的 CLR 枚举类型的对象，将需要显式强制转换。 因此，例如，给定  
  
```  
void f( int );  
```  
  
 作为非重载方法，在托管扩展中，调用  
  
```  
f( rslt ); // ok: Managed Extensions; error: new syntax  
```  
  
 确定，且内包含的值`rslt`隐式转换为一个整数值。 在 Visual c + + 中，此调用将无法编译。 若要正确地转换它，我们必须插入转换运算符：  
  
```  
f( safe_cast<int>( rslt )); // ok: new syntax  
```  
  
## <a name="the-scope-of-the-clr-enum-type"></a>CLR 枚举类型的作用域  
 C 和 c + + 语言之间的更改之一是结构设施内的作用域的 c + + 中添加。 在 C 中，结构是只是不支持的接口或关联的作用域的聚合数据。 这是相当多的彻底更改时，对于来自 C 语言的许多新 c + + 用户有争议的问题。 本机和 CLR 枚举之间的关系是类似的。  
  
 在托管扩展中，尝试定义 CLR 枚举的枚举器的弱插入的名称，以便模拟不存在的范围内本机枚举。 这并没有证明是成功。 问题是，这会导致枚举器溢出到全局命名空间，从而导致难以管理名称冲突。 在新语法中，我们具有匹配到支持在 CLR 枚举的作用域中的其他 CLR 语言。  
  
 这意味着 CLR 枚举的枚举器的任何非限定的使用将不识别新的语法。 我们来看一个实际示例。  
  
```  
// Managed Extensions supporting weak injection  
__gc class XDCMake {  
public:  
   __value enum _recognizerEnum {   
      UNDEFINED,  
      OPTION_USAGE,   
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,  
      XDC0002_ERR_CANNOT_WRITE_TO = 2,  
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,  
      XDC0004_WRN_XML_LOAD_FAILURE = 4,  
      XDC0006_WRN_NONEXISTENT_FILES = 6,  
   };  
  
   ListDictionary* optionList;  
   ListDictionary* itagList;  
  
   XDCMake() {  
      optionList = new ListDictionary;  
  
      // here are the problems...  
      optionList->Add(S"?", __box(OPTION_USAGE)); // (1)  
      optionList->Add(S"help", __box(OPTION_USAGE)); // (2)  
  
      itagList = new ListDictionary;  
      itagList->Add(S"returns",   
         __box(XDC0004_WRN_XML_LOAD_FAILURE)); // (3)  
   }  
};  
```  
  
 每三个非限定使用的枚举器名称 (`(1)`， `(2)`，和`(3)`) 将需要限定在编译的源代码的顺序中的新语法的转换。 下面是原始源代码中的一个正确转换：  
  
```  
ref class XDCMake {  
public:  
   enum class _recognizerEnum {  
      UNDEFINED, OPTION_USAGE,   
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,  
      XDC0002_ERR_CANNOT_WRITE_TO = 2,  
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,  
      XDC0004_WRN_XML_LOAD_FAILURE = 4,  
      XDC0006_WRN_NONEXISTENT_FILES = 6  
   };  
  
   ListDictionary^ optionList;  
   ListDictionary^ itagList;  
  
   XDCMake() {  
      optionList = gcnew ListDictionary;  
      optionList->Add("?",_recognizerEnum::OPTION_USAGE); // (1)  
      optionList->Add("help",_recognizerEnum::OPTION_USAGE); //(2)  
      itagList = gcnew ListDictionary;  
      itagList->Add( "returns",   
         _recognizerEnum::XDC0004_WRN_XML_LOAD_FAILURE); //(3)  
   }  
};  
```  
  
 这会更改本机和 CLR 枚举之间的设计策略。 与维护关联的作用域中 Visual c + + CLR 枚举，它是没有必要，也不有效地封装在类中枚举的声明。 此习惯用法改进 cfront 2.0 钟形 Laboratories 时间附近还以解决全局名称污染问题。  
  
 在原始 beta 版本中的新 iostream 库通过在钟形 Laboratories 杰儿 Schwarz，杰儿未封装有关库，例如常见的枚举器定义的所有关联的枚举`read`， `write`， `append`，依次类推进行几乎不可能进行编译现有代码的用户。 一种解决方案将一直都是重整名称，如`io_read`， `io_write`，等等。第二个解决方案将一直都是通过将范围添加到枚举，修改的语言，但这不是可行下时。 折中的解决方案是封装在类中，枚举或类层次结构，其中的标记名称和枚举的枚举器填充封闭类范围。）也就是说，动机是针对将在类中，枚举放置至少最初不是理论，但对全局命名空间污染问题的实际响应。  
  
 与 Visual c + + 枚举中，已不再封装类内部枚举任何明显的好处。 实际上，如果你看一下`System`命名空间，你将看到该枚举、 类和接口都存在同一声明空间。  
  
## <a name="see-also"></a>请参阅  
 [值类型和它们的行为 (C + + /cli CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [枚举类](../windows/enum-class-cpp-component-extensions.md)