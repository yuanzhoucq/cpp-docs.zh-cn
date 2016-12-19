---
title: "转换运算符的更改 | Microsoft Docs"
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
  - "转换运算符"
  - "转换, explicit"
  - "explicit 关键字 [C++]"
  - "运算符 [C++], 显式类型转换"
  - "类型转换, 显式转换"
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 转换运算符的更改
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，转换运算符的语法已发生了更改。  
  
 例如，现在必须使用 `op_Implicit` 来指定转换。  下面是一个从语言规范中获取的 `MyDouble` 的定义：  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 这表示，给定一个整数，将此整数转换为 `MyDouble` 的算法是由 `op_Implicit` 运算符提供的。  而且，此转换将由编译器隐式执行。  类似地，给定一个 `MyDouble` 对象，两个 `op_Explicit` 运算符为将此对象转换为整数或托管 `String` 实体分别提供算法。  不过，除非用户显式要求，否则编译器将不执行转换。  
  
 在 C\# 中，这将如下所示：  
  
```  
class MyDouble {  
   public static implicit operator MyDouble( int i );   
   public static explicit operator int( MyDouble val );  
   public static explicit operator string( MyDouble val );   
};  
```  
  
 C\# 代码比 C\+\+ 托管扩展代码更像 C\+\+。  但在新语法中却不是这样。  
  
 ISO\-C\+\+ 委员会引入了关键字 `explicit`，以减少意外结果。例如，将单个整数参数作为维数的 `Array` 类会将任何整数隐式转换为 `Array` 对象，但您并不需要该对象。  预防此种情况发生的一个设计惯例是为构造函数设置第二个虚拟参数。  
  
 另一方面，在 C\+\+ 中设计类类型时，不应提供转换对。  这方面最好的例子是标准字符串类。  隐式转换是采用 C 样式字符串的单一参数构造函数。  但是，它不提供相应的隐式转换运算符 — 将字符串对象转换为 C 样式字符串的转换运算符，而是要求用户显式调用一个命名函数 — 在这种情况下为 `c_str()`。  
  
 因此，在转换运算符上关联隐式\/显式行为（将转换集封装到单个声明窗体）应该是对原 C\+\+ 中对转换运算符支持的改进，这最终导致了 `explicit` 关键字的产生。  [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 语言对转换运算符的支持如下所示，由于此运算符的默认行为支持转换算法的隐式应用，因此它比 C\# 运算符稍简略一些：  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 另一个更改是将单一参数构造函数视为好像它被声明为 `explicit`。  这意味着为了触发它的调用，要求进行显式强制转换。  不过，请注意，如果定义了显式转换运算符，将调用该显式转换运算符而不是单一参数构造函数。  
  
## 请参阅  
 [类或接口中的成员声明 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)