---
title: "basic_ostream 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::basic_ostream"
  - "std.basic_ostream"
  - "ostream/std::basic_ostream"
  - "basic_ostream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ostream 类"
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
caps.latest.revision: 24
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_ostream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述一个控制将元素和编码对象插入流缓冲区的对象（其字符特征由类 **Tr** 确定，也称为 [traits\_type](../Topic/basic_ios::traits_type.md)），该流缓冲区具有 **Elem** 类型的元素（也称为 [char\_type](../Topic/basic_ios::char_type.md)）。  
  
## 语法  
  
```  
  
template <class   
_Elem  
, class   
_Tr  
 = char  
_  
traits<Elem> >  
   class basic  
_  
ostream  
       : virtual public basic  
_  
ios<  
_Elem  
,   
_Tr  
>  
  
```  
  
#### 参数  
 `_Elem`  
 `char_type`。  
  
 `_Tr`  
 字符 `traits_type`。  
  
## 备注  
 重载 [operator\<\<](../Topic/basic_ostream::operator%3C%3C.md) 的大部分成员函数是格式化的输出函数。 它们遵循以下模式：  
  
```  
iostate state = goodbit;  
const sentry ok( *this );  
if ( ok )  
   {try  
      {<convert and insert elements  
      accumulate flags in state> }  
   catch ( ... )  
      {try  
        {setstate( badbit ); }  
      catch ( ... )  
        {}  
      if ( ( exceptions( ) & badbit ) != 0 )  
        throw; }}  
width( 0 );    // Except for operator<<(Elem)  
setstate( state );  
return ( *this );  
```  
  
 两个其他成员函数是未格式化的输出函数。 它们遵循以下模式：  
  
```  
iostate state = goodbit;  
const sentry ok( *this );  
if ( !ok )  
   state |= badbit;  
else  
   {try  
      {<obtain and insert elements  
      accumulate flags in state> }  
   catch ( ... )  
      {try  
         {setstate( badbit ); }  
      catch ( ... )  
         {}  
      if ( ( exceptions( ) & badbit ) != 0 )  
         throw; }}  
setstate( state );  
return ( *this );  
```  
  
 如果它们在插入元素时遭遇失败，两组函数都会调用 [setstate](../Topic/basic_ios::setstate.md)**\(badbit\)**。  
  
 类 basic\_istream\<**Elem**, **Tr**\> 的对象仅存储类 [basic\_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr\>** 的虚拟公共基对象。  
  
## 示例  
 请参阅示例 [basic\_ofstream 类](../standard-library/basic-ofstream-class.md) 若要了解有关输出流的详细信息。  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_ostream](../Topic/basic_ostream::basic_ostream.md)|构造 `basic_ostream` 对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[flush](../Topic/basic_ostream::flush.md)|刷新缓冲区。|  
|[put](../Topic/basic_ostream::put.md)|将字符放入流中。|  
|[seekp](../Topic/basic_ostream::seekp.md)|重置在输出流中的位置。|  
|[sentry](../Topic/basic_ostream::sentry.md)|嵌套的类描述一个对象，该对象的声明构造格式化的输出函数和未格式化的输出函数。|  
|[swap](../Topic/basic_ostream::operator=.md)|将此 `basic_ostream` 对象的值与提供的 `basic_ostream` 对象的值进行交换。|  
|[tellp](../Topic/basic_ostream::tellp.md)|报告在输出流中的位置。|  
|[写入](../Topic/basic_ostream::write.md)|将字符放入流中。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\=](../Topic/basic_ostream::operator=.md)|将提供的 `basic_ostream` 对象参数的值赋给此对象。|  
|[operator\<\<](../Topic/basic_ostream::operator%3C%3C.md)|写入流。|  
  
## 要求  
 **标头：**\<ostream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)