---
title: "chrono 文本 | Microsoft Docs"
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
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
caps.latest.revision: 10
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# chrono 文本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\(C\+\+14\) \<Chrono\> 标头定义 12 个[用户定义的文本](../cpp/user-defined-literals-cpp.md)，以帮助使用表示小时、分钟、秒、毫秒、微秒和纳秒的文本。 每个用户定义的文本都具有一个整型重载和一个浮点重载。 这些文本是在 literals::chrono\_literals 内联命名空间中定义的，当 std::chrono 位于范围内时，该命名空间将被自动置于范围中。  
  
## 语法  
  
```vb  
inline namespace literals {  
    inline namespace chrono_literals {  
  
        // return integral hours  
        constexpr chrono::hours operator "" h(unsigned long long Val);  
  
        // return floating-point hours  
        constexpr chrono::duration<double, ratio<3600> > operator "" h(long double Val);  
  
        // return integral minutes  
        constexpr chrono::minutes(operator "" min)(unsigned long long Val);  
  
        // return floating-point minutes  
        constexpr chrono::duration<double, ratio<60> >(operator "" min)(long double Val);  
  
        // return integral seconds  
        constexpr chrono::seconds operator "" s(unsigned long long Val);  
  
        // return floating-point seconds  
        constexpr chrono::duration<double> operator "" s(long double Val);  
  
        // return integral milliseconds  
        constexpr chrono::milliseconds operator "" ms(unsigned long long Val);  
  
         // return floating-point milliseconds  
        constexpr chrono::duration<double, milli> operator "" ms(long double Val);  
  
        // return integral microseconds      
        constexpr chrono::microseconds operator "" us(unsigned long long Val);  
  
        // return floating-point microseconds  
        inline constexpr chrono::duration<double, micro> operator "" us(long double Val);  
  
        // return integral nanoseconds  
        inline constexpr chrono::nanoseconds operator "" ns(unsigned long long Val);  
  
        // return floating-point nanoseconds  
        constexpr chrono::duration<double, nano> operator "" ns(long double Val);  
    }// inline namespace chrono_literals  
}// inline namespace literals  
```  
  
```c#  
  
```  
  
## 返回值  
 采用 `long long` 参数的文本返回值或相应的类型。 采用浮点参数的文本返回 [duration](../standard-library/duration-class.md)。  
  
## 备注  
  
## 示例  
 下面的示例演示如何使用 chrono 文本。  
  
```  
constexpr auto day = 24h;  
constexpr auto week = 24h * 7;  
constexpr auto my_duration_unit = 108ms;  
```  
  
## 要求  
 **标头**：\<chrono\>  
  
 **命名空间**：std::literals::chrono\_literals  
  
## 请参阅  
 [\< \> chrono](../standard-library/chrono.md)