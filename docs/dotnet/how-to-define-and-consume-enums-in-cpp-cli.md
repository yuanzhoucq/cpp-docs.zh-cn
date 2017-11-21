---
title: "如何： 定义和使用枚举在 C + + /cli CLI |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f4243400f20ae30fe1a2bc3826f052eb534297b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>如何：在 C++/CLI 中定义和使用枚举
本主题讨论枚举在 C + + /cli CLI。  
  
## <a name="specifying-the-underlying-type-of-an-enum"></a>指定枚举的基础类型  
 默认情况下，枚举的基础类型是`int`。  但是，可以指定的类型是带符号或无符号形式的`int`， `short`， `long`， `__int32`，或`__int64`。  你还可以使用`char`。  
  
```  
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
  
## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>如何托管和标准枚举之间转换  
 枚举和整型类型; 之间没有标准转换强制转换是必需的。  
  
```  
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
 以下运算符在上都有效枚举在 C + + /cli CLI:  
  
|运算符|  
|--------------|  
|== != \< > \<= >=|  
|+ -|  
|&#124; ^ & ~|  
|++ --|  
|sizeof|  
  
 运算符 &#124;^ & ~ + +-仅为枚举定义与基础类型，不包括 bool 的整型。  两个操作数必须是枚举类型。  
  
 编译器将不对执行静态或动态检查结果的枚举操作;操作可能会导致不中枚举的有效枚举器的范围的值。  
  
> [!NOTE]
>  C + + 11 引入了枚举类类型在非托管代码中的是明显不同于托管的枚举类，在 C + + /cli CLI。 具体而言，C + + 11 枚举类类型不支持与托管的枚举类类型相同的运算符在 C + + /cli CLI 和 C + + /cli CLI 源代码必须提供在托管枚举可访问性说明符类声明以将它们与非托管 （c + + 区分开来11） 枚举类声明。 有关枚举类，在 C + + /cli CLI，C + + /CX 中，以及 C + + 11 中，请参阅[枚举类](../windows/enum-class-cpp-component-extensions.md)。  
  
```  
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
  
```  
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
 [枚举类](../windows/enum-class-cpp-component-extensions.md)