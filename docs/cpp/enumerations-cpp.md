---
title: 枚举 (C++)
ms.date: 06/01/2018
f1_keywords:
- enum_cpp
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
ms.openlocfilehash: caec9ea7ac5482ff23b73676a3fd7b3d25ad293f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423758"
---
# <a name="enumerations-c"></a>枚举 (C++)

枚举是用户定义的类型，其中包含一组称为枚举器的命名的整型常数。

> [!NOTE]
>  本文介绍了 ISO 标准C++语言**枚举**类型以及 c + + 11 中引入的作用域内（或强类型）**枚举类**类型。 有关/Cli 和C++ C++/cx 中**公共 enum 类**或**私有 enum 类**类型的信息，请参阅[enum 类](../extensions/enum-class-cpp-component-extensions.md)。

## <a name="syntax"></a>语法

```
// unscoped enum:
enum [identifier] [: type]
{enum-list};

// scoped enum:
enum [class|struct]
[identifier] [: type]
{enum-list};
```

```cpp
// Forward declaration of enumerations  (C++11):
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```

## <a name="parameters"></a>parameters

*identifier*<br/>
指定给与枚举的类型名称。

type<br/>
枚举器的基础类型；所有枚举器都具有相同的基础类型。 可能是任何整型。

*枚举列表*<br/>
枚举中以逗号分隔的枚举器列表。 范围中的每个枚举器或变量名必须是唯一的。 但是，值可以重复。 在未区分范围的枚举中，范围为环绕范围;在范围枚举中，范围是*枚举列表*本身。  在限定范围的枚举中，该列表可能为空，这实际上定义了一个新的整型类型。

class<br/>
通过在声明中使用此关键字，指定枚举的作用域，并且必须提供*标识符*。 你还可以使用**struct**关键字代替**类**，因为在此上下文中它们在语义上是等效的。

## <a name="enumerator-scope"></a>枚举器范围

枚举提供上下文来描述以命名常数表示的一系列值，这些值也称为枚举器。 在原始 C 和 C++ 枚举类型中，非限定枚举器在声明枚举的整个范围中可见。 在区分范围的枚举中，枚举器名称必须由枚举类型名称限定。 以下示例演示两种枚举之间的基本差异：

```cpp
namespace CardGame_Scoped
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type
        { /*...*/}
    }
}

namespace CardGame_NonScoped
{
    enum Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Clubs) // Enumerator is visible without qualification
        { /*...*/
        }
    }
}
```

将为枚举中的每个名称分配一个整数值，该值与其在枚举中的顺序相对应。 默认情况下，为第一个值分配 0，为下一个值分配 1，以此类推，但你可以显式设置枚举器的值，如下所示：

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

为枚举器 `Diamonds` 分配值 `1`。 后续枚举器接收的值会在前一个枚举器的值的基础上加一（如果没有显式赋值）。 在前面的示例中，`Hearts` 将具有值 2，`Clubs` 将具有值 3，依此类推。

每个枚举器都被视为常量，并且在定义**枚举**的作用域（对于未区分范围的枚举）或**枚举**本身中必须有唯一的名称（用于限定范围的枚举）。 为这些名称指定的值不必是唯一的。 例如，如果一个未区分范围的枚举 `Suit` 的声明如下：

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

`Diamonds`、`Hearts`、`Clubs` 和 `Spades` 的值分别是 5、6、4 和 5。 请注意，5 使用了多次；尽管这并不符合预期，但是允许的。 对于区分范围的枚举来说，这些规则是相同的。

## <a name="casting-rules"></a>强制转换规则

未区分范围的枚举常数可隐式转换为**int**，但**int**绝不会隐式转换为枚举值。 下面的示例显示了如果尝试为 `hand` 分配一个不是 `Suit` 的值可能出现的情况：

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

需要强制转换才能将**int**转换为限定范围或未区分范围的枚举器。 但是，你可以将区分范围的枚举器提升为整数值，而不进行强制转换。

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

按照这种方式使用隐式转换可能导致意外副作用。 若要帮助消除与区分范围的枚举相关的编程错误，区分范围的枚举值必须是强类型值。 区分范围的枚举器必须由枚举类型名称（标识符）限定，并且无法进行隐式转换，如以下示例所示：

```cpp
namespace ScopedEnumConversions
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void AttemptConversions()
    {
        Suit hand;
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier
        hand = Suit::Clubs; //Correct.
        int account_num = 135692;
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!

        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'
        account_num = static_cast<int>(Suit::Hearts); // OK
    }
}
```

注意，`hand = account_num;` 行仍会导致对未区分范围的枚举发生的错误，如前面所示。 它可以与显式强制转换一起使用。 但是，借助区分范围的枚举，不再允许在没有显式强制转换的情况下在下一条语句 `account_num = Suit::Hearts;` 中尝试转换。

## <a name="no_enumerators"></a>没有枚举器的枚举

**Visual Studio 2017 版本15.3 及更高版本**（可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起使用）：通过使用显式基础类型定义枚举（常规或范围），而不使用枚举器，实际上可以引入不包含任何其他类型的隐式转换的新整型类型。 通过使用此类型（而不是其内置基础类型），可以消除无意中的隐式转换导致的细微错误的可能性。

```cpp
enum class byte : unsigned char { };
```

新类型是基础类型的精确副本，因此具有相同的调用约定，这意味着可在 Abi 中使用，而不会造成任何性能损失。 使用直接列表初始化来初始化类型的变量时不需要强制转换。 下面的示例演示如何在不同的上下文中初始化没有枚举器的枚举：

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 };

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
```

## <a name="see-also"></a>另请参阅

[C 枚举声明](../c-language/c-enumeration-declarations.md)<br/>
[关键字](../cpp/keywords-cpp.md)