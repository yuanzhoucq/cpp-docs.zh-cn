---
title: "如何：在 C++/CLI 中定义和使用枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enum 类, 指定基本类型"
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 C++/CLI 中定义和使用枚举
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题讨论在 C\+\+\/CLI 枚举。  
  
## 指定枚举的基础类型  
 默认情况下，枚举的基础类型为 `int`。但是，可指定类型将签名或 `int`、`short`、`long`、`__int32`或 `__int64`类未签名的窗体。还可以使用 `char`。  
  
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
  
 **Output**  
  
  **The**  
**0**  
**1**  
**2**   
## 如何在托管和标准枚举之间转换  
 不是枚举和整型之间的标准转换；需要转换。  
  
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
  
 **Output**  
  
  **并 day2 是相同的。**   
## 运算符和枚举  
 下列运算符均有效在 C\+\+\/CLI 的枚举：  
  
|运算符|  
|---------|  
|\=\= \!\= \< \> \<\= \>\=|  
|\+ \-|  
|&#124; ^ & ~|  
|\+\+ \-\-|  
|sizeof|  
  
 运算符&#124;^ & &#124; C\/C\+\+\-\-为枚举仅定义与基础整数类型，不包括 bool。两个操作数必须都是枚举类型。  
  
 编译器不执行静态或动态的枚举检查操作的结果；操作可能会导致枚举的枚举数的值不在有效范围内。  
  
> [!NOTE]
>  比在 C\+\+\/CLI 托管枚举类显著的不同 C\+\+11 介绍枚举类输入非托管代码。  具体而言，C\+\+11 枚举类类型不支持与托管枚举类输入 C\+\+\/CLI 的运算符，并且，C\+\+\/CLI 源代码必须提供的枚举声明类的可访问性说明符以与非托管 \(\) 声明类 C\+\+11 枚举区分它们。  有关枚举的更多信息，C\+\+\/CX 在 C\+\+\/CLI 类，而且，C\+\+11，请参见 [enum class](../windows/enum-class-cpp-component-extensions.md)。  
  
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
  
 **Output**  
  
  **4**  
**1**  
**True**   
## 请参阅  
 [enum class](../windows/enum-class-cpp-component-extensions.md)