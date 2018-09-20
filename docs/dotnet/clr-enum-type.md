---
title: CLR 枚举类型 |Microsoft Docs
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
ms.openlocfilehash: a39c451bcff7b5b3b1d7dd9f0d3925616b9d6aab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436218"
---
# <a name="clr-enum-type"></a>CLR 枚举类型

声明和行为的枚举已从托管扩展 c + + 的 Visual c + +。

托管扩展枚举声明的前面有`__value`关键字。 这里的思路是将本机枚举与派生自的 CLR 枚举区分开来`System::ValueType`，同时建议一个类似功能。 例如：

```
__value enum e1 { fail, pass };
public __value enum e2 : unsigned short  {
   not_ok = 1024,
   maybe, ok = 2048
};
```

新语法通过强调后一种而不是源于值类型的类特性可解决的问题区分本机和 CLR 枚举。 在这种情况下，`__value`关键字将被放弃，替换为空格分隔的关键字对`enum class`。 这提供了对称的引用、 值和接口的类声明的成对的关键字：

```
enum class ec;
value class vc;
ref class rc;
interface class ic;
```

枚举对翻译`e1`和`e2`中新的语法如下所示：

```
enum class e1 { fail, pass };
public enum class e2 : unsigned short {
   not_ok = 1024,
   maybe, ok = 2048
};
```

除了此细微的语法更改，CLR 枚举类型的行为已更改中通过多种方式：

- 不再支持 CLR 枚举的前向声明。 没有映射。 它只被标记为编译时错误。

```
__value enum status; // Managed Extensions: ok
enum class status;   // new syntax: error
```

- 内置算术类型之间的重载决策和`Object`类层次结构中具有相反的两个语言版本 ！ 其副作用是，CLR 枚举将不再隐式转换为算术类型。

- 在新语法中，CLR 枚举可以保持自己的作用域，不是托管扩展中的用例。 以前，枚举器可在枚举的包含作用域内可见。 现在，枚举器枚举的作用域内封装。

## <a name="clr-enums-are-a-kind-of-object"></a>CLR 枚举都是一个类型的对象

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

对本机 c + + 程序员来说，自然回答这个问题的实例的重载`f()`调用是`f(int)`。 枚举是一个符号的整型常量，和它参与了标准的整型提升其在这种情况下更高优先级。  实际上在托管扩展这就是调用解析的实例。 这导致大量意外情况的不是当我们使用本机 c + + 在框架中的但我们需要它们以便与现有的 BCL （基类库） 框架，其中`Enum`类间接派生自`Object`。 在 Visual c + + 语言设计中的实例`f()`的调用是`f(Object^)`。

已选择 Visual c + + 强制实施此方法是不支持 CLR 枚举类型和算术类型之间的隐式转换。 这意味着任何分配为算术类型的 CLR 枚举类型的对象，将需要显式强制转换。 因此，例如，给定

```
void f( int );
```

作为非重载方法，在托管扩展中，调用

```
f( rslt ); // ok: Managed Extensions; error: new syntax
```

为确定，而值包含在`rslt`隐式转换为一个整数值。 在 Visual c + +，无法编译此调用。 若要正确地转换它，我们必须插入转换运算符：

```
f( safe_cast<int>( rslt )); // ok: new syntax
```

## <a name="the-scope-of-the-clr-enum-type"></a>CLR 枚举类型的作用域

C 和 c + + 语言之间的变化之一是 c + + 中添加的结构设施内的作用域。 在 C 中，结构是只是数据聚合不支持的接口或关联的范围。 这是相当了根本改变时，来自于 C 语言的许多新 c + + 用户的争用问题。 本机和 CLR 枚举之间的关系非常类似。

在托管扩展中，已尝试定义 CLR 枚举的枚举器的弱插入的名称，以便模拟本机枚举中的作用域不存在。 这并没有证明是成功。 问题在于，这会导致溢出至全局命名空间，从而导致难以管理名称冲突的枚举器。 在新语法中，我们必须遵守到支持在 CLR 枚举的作用域中其他 CLR 语言版本。

这意味着任何使用非限定的 CLR 枚举的枚举器将不会通过新的语法进行识别。 让我们看一个真实示例。

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

每个非限定的三个使用的枚举器名称 (`(1)`， `(2)`，和`(3)`) 将需要限定在对源代码进行编译的顺序中的新语法的转换。 下面是原始源代码的正确翻译：

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

这会更改之间本机和 CLR 枚举的设计策略。 维护 Visual c + + 中的关联作用域中 CLR 枚举，它既不必要也不是有效地封装在类中枚举的声明。 此习惯用法发展 cfront 2.0 贝尔时间附近也来解决全局名称污染的问题。

在原始 beta 版本中的新 iostream 库通过在贝尔 Jerry Schwarz，Jerry 未封装有关库，例如常见的枚举器定义的所有关联的枚举`read`， `write`， `append`，等等使用户能够编译其现有的代码几乎不可能。 一种解决方案是重整名称，如`io_read`， `io_write`，等等。第二种解决方案是通过将范围添加到枚举，修改语言，但这不是可行的情况下时。 中间的解决方案是封装在类中，枚举或类层次结构，其中的标记名称和枚举的枚举器填充封闭类范围。）即，至少最初放置在类中，枚举的动机不是理论，但对全局命名空间污染问题的实际响应。

使用 Visual c + + 枚举是不再封装在类中的枚举任何明显的好处。 事实上，如果您看一下`System`命名空间，您将看到该枚举、 类和接口都存在同一声明空间。

## <a name="see-also"></a>请参阅

[值类型及其行为 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[枚举类](../windows/enum-class-cpp-component-extensions.md)