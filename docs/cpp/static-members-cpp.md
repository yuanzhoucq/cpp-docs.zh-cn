---
title: 静态成员 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fba58883db0f5936a8f3dedc1e0c4a19fb0aafa9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086195"
---
# <a name="static-members-c"></a>静态成员 (C++)

类可以包含静态成员数据和成员函数。 当数据成员声明为**静态**，只有一个数据副本保留的类的所有对象。

静态数据成员不是给定的类类型的对象的一部分。 因此，静态数据成员的声明不被视为一个定义。 在类范围中声明数据成员，但在文件范围内执行定义。 这些静态类成员具有外部链接。 下面的示例阐释了这一点：

```cpp
// static_data_members.cpp
class BufferedOutput
{
public:
   // Return number of bytes written by any object of this class.
   short BytesWritten()
   {
      return bytecount;
   }

   // Reset the counter.
   static void ResetCount()
   {
      bytecount = 0;
   }

   // Static member declaration.
   static long bytecount;
};

// Define bytecount in file scope.
long BufferedOutput::bytecount;

int main()
{
}
```

在前面的代码中，该成员 `bytecount` 在类 `BufferedOutput` 中声明，但它必须在类声明的外部定义。

在不引用类类型的对象的情况下，可以引用静态数据成员。 可以获取使用 `BufferedOutput` 对象编写的字节数，如下所示：

```cpp
long nBytes = BufferedOutput::bytecount;
```

对于存在的静态成员，类类型的所有对象的存在则没有必要。 此外可以使用成员选择访问静态成员 (**。** 并**->**) 运算符。 例如：

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

在前面的示例中，不会评估对对象(`Console`) 的引用；返回的值是静态对象 `bytecount` 的值。

静态数据成员遵循类成员访问规则，因此只允许类成员函数和友元拥有对静态数据成员的私有访问权限。 这些规则所述[成员访问控制](../cpp/member-access-control-cpp.md)。 例外情况是，无论静态数据成员的访问限制如何，都必须在文件范围内进行定义。 如果进行显式初始化数据成员，则必须使用定义提供初始值设定项。

静态成员的类型不是由其类名称限定的。 因此，类型`BufferedOutput::bytecount`是**长**。

## <a name="see-also"></a>请参阅

[类和结构](../cpp/classes-and-structs-cpp.md)