---
title: 如何：在 C++/CLI 中定义和使用枚举
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: cf3bb23069b2692c0ca4ce270a5b8060195becf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370174"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>如何：在 C++/CLI 中定义和使用枚举

本主题讨论C++/CLI中的枚举。

## <a name="specifying-the-underlying-type-of-an-enum"></a>指定枚举的基础类型

默认情况下，枚举的基础类型为`int`。  但是，您可以指定要签名的类型或 未`int`签名的窗体`short`、、`long`或`__int32`。 `__int64`  还可以使用 `char`。

```cpp
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**输出**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>如何在托管和标准枚举之间进行转换

枚举和积分类型之间没有标准转换;需要强制转换。

```cpp
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**输出**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>运算符和枚举

以下运算符在 C++/CLI 中的枚举中有效：

|操作员|
|--------------|
|[ ！ \<  >  \<] >*|
|+ -|
|&#124; [ & ]|
|++ --|
|sizeof|

运算符&#124; = & = = - 仅定义为具有积分基础类型的枚举，不包括 bool。  两个操作数都必须为枚举类型。

编译器不静态或动态检查枚举操作的结果;操作可能会导致值不在枚举的有效枚举器范围内。

> [!NOTE]
> C++11 在非托管代码中引入了枚举类类型，这些类型与 C++/CLI 中的托管枚举类明显不同。 特别是，C++11枚举类类型不支持与C++/CLI 中的托管枚举类类型相同的运算符，并且C++/CLI 源代码必须在托管枚举类声明中提供辅助功能指定器，以便将它们与非托管 （C++11） 枚举类声明区分开来。 有关C++/CLI、C++/CX 和 C++11 中的枚举类的详细信息，请参阅[枚举类](../extensions/enum-class-cpp-component-extensions.md)。

```cpp
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```cpp
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**输出**

```Output
4
1
True
```

## <a name="see-also"></a>另请参阅

[枚举类](../extensions/enum-class-cpp-component-extensions.md)
