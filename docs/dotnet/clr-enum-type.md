---
title: "CLR 枚举类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enum class 关键字 [C++]"
  - "enum struct 关键字 [C++]"
  - "范围, CLR 枚举的"
ms.assetid: 4541d952-97bb-4e35-a7f8-d14f5f6a6606
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CLR 枚举类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，枚举的声明和行为发生了更改。  
  
 托管扩展的枚举声明以 `__value` 关键字开头。  其目的是将本机枚举与从 `System::ValueType` 派生的 CLR 枚举区分开来，同时建议一个类似功能。  例如：  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};  
```  
  
 新语法解决区分本机枚举和 CLR 枚举问题的方法是：强调后者的类性质而非其值类型根。  同样，丢弃了 `__value` 关键字，而由空格分隔的关键字对 `enum class` 替换。  这对引用、值和接口类的声明提供了对称的成对关键字：  
  
```  
enum class ec;  
value class vc;  
ref class rc;  
interface class ic;  
```  
  
 枚举对 `e1` 和 `e2` 的转换在新语法中如下所示：  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 除此语法的稍微更改外，CLR 枚举的行为在许多方面发生了更改：  
  
-   不再支持 CLR 枚举的前向声明。  没有映射。  而简单地将其标记为编译时错误。  
  
```  
__value enum status; // Managed Extensions: ok  
enum class status;   // new syntax: error  
```  
  
-   内置算术类型和 `Object` 类层次结构之间的重载决策在这两种语言版本中相反！  它的副作用是 CLR 枚举不再隐式转换为算术类型。  
  
-   在新的语法中，CLR 枚举保持其自身范围，而在托管扩展中则不是这样。  以前，枚举数在枚举的包含范围内可见。  现在，枚举数封装在枚举的范围内。  
  
## CLR 枚举是一种对象  
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
  
 对本机 C\+\+ 程序员来说，调用哪个重载的 `f()` 的实例的问题的通常回答是：调用 `f(int)` 的实例。  枚举是符号整数常数，并且它参与此情况下优先级高的标准整数提升。实际上，在托管扩展中，它是调用解析到的实例。  这导致了许多疑问 — 不是当我们在本机 C\+\+ 框架中使用枚举时，而是在我们需要它们与现有 BCL（基类库）交互时，其中 `Enum` 是从 `Object` 间接派生的类。  在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 语言设计中，调用的 `f()` 的实例是 `f(Object^)` 的实例。  
  
 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 选择强制执行此操作的方式是不支持 CLR 枚举类型和算术类型之间的隐式转换。  这意味着 CLR 枚举类型的对象向算术类型的任何分配都需要显式强制转换。  例如，假设  
  
```  
void f( int );  
```  
  
 作为一个非重载方法，在托管扩展中，调用  
  
```  
f( rslt ); // ok: Managed Extensions; error: new syntax  
```  
  
 是可以的，并且 `rslt` 内包含的值隐式转换为一个整数值。  在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中，此调用无法编译。  若要正确地转换它，必须插入一个转换运算符：  
  
```  
f( safe_cast<int>( rslt )); // ok: new syntax  
```  
  
## CLR 枚举类型的范围  
 C 和 C\+\+ 语言的差别之一是 C\+\+ 中增加了结构功能内的范围。  在 C 中，结构仅是一个不支持接口或关联范围的数据聚合。  这在当时是一个相当基本的更改，对原先使用 C 语言的新 C\+\+ 用户来说是一个有争议的问题。  本机枚举和 CLR 枚举之间的关系是类似的。  
  
 在托管扩展中，为了模拟不存在本机枚举内的范围，曾尝试为 CLR 枚举的枚举数定义弱插入名称。  这并没有证明是成功的。  问题是它导致枚举数溢出到全局命名空间中，从而难于管理名称冲突。  在新语法中，我们在支持 CLR 枚举内的范围方面与其他 CLR 语言保持一致。  
  
 这意味着新语法无法识别 CLR 枚举的枚举数的任何非限定使用。  让我们看一个具体的示例。  
  
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
  
      // here are the problems …  
      optionList->Add(S"?", __box(OPTION_USAGE)); // (1)  
      optionList->Add(S"help", __box(OPTION_USAGE)); // (2)  
  
      itagList = new ListDictionary;  
      itagList->Add(S"returns",   
         __box(XDC0004_WRN_XML_LOAD_FAILURE)); // (3)  
   }  
};  
```  
  
 为了编译源代码，需要将枚举数名称的三个非限定使用（`(1)`、`(2)` 和 `(3)`）分别限定在新语法的转换中。  以下是原始源代码的一个正确转换：  
  
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
  
 这会更改本机枚举和 CLR 枚举之间的设计策略。  由于在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中 CLR 枚举保持关联范围，对类中枚举的声明进行封装既没必要又效率低下。  这个用法随着贝尔实验室的 cfront 2.0 不断发展，也用来解决全局命名污染的问题。  
  
 在由贝尔实验室的 Jerry Schwarz 发布的新 iostream 库的原始 beta 版中，Jerry 没有封装为该库定义的所有关联枚举以及公共枚举数（如 `read`、`write`、`append` 等），使用户几乎不可能编译自已的现有代码。  一种解决方案是重整名称，如 `io_read`、`io_write`等。第二种解决方案是通过将范围添加到枚举来修改语言，但这在当时是不切实际的。  （折中的解决方案是：封装类或类层次结构中的枚举，其中标记名和枚举的枚举数将填充封闭类范围。）也就是说，至少最初将枚举放置在类中的动机是不理性的，但是却对全局命名空间污染问题作了实际的响应。  
  
 有了 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 枚举，封装类中的枚举不再有任何明显的好处。  事实上，如果查看 `System` 命名空间，您将看到枚举、类和接口都存在于相同的声明空间中。  
  
## 请参阅  
 [值类型及其行为 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [enum class](../windows/enum-class-cpp-component-extensions.md)