---
title: "更改为转换运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- conversion operators
- operators [C++], explicit type conversion
- type conversion, explicit conversions
- conversions, explicit
- explicit keyword [C++]
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8f89c49035e2e48dde8d502b1d61fa33d198f69a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="changes-to-conversion-operators"></a>转换运算符的更改
转换运算符的语法已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 其中一个示例是编写`op_Implicit`来指定转换。 下面是定义的`MyDouble`摘自语言规范：  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 这表示，给定一个整数，用于转换该整数转换算法`MyDouble`由`op_Implicit`运算符。 此外，该转换将隐式执行由编译器。 同样，给定`MyDouble`对象、 两个`op_Explicit`运算符将该对象转换为整数或托管提供各自的算法`String`实体。 但是，编译器将不执行此转换，除非由用户显式请求。  
  
 在 C# 中，这看起来，如下所示：  
  
```  
class MyDouble {  
   public static implicit operator MyDouble( int i );   
   public static explicit operator int( MyDouble val );  
   public static explicit operator string( MyDouble val );   
};  
```  
  
 C# 代码看上去更像 c + + 的 c + + 托管扩展比。 不是这样的新语法中。  
  
 ISO c + + committee 引入了新关键字`explicit`，以缓解意外的后果-例如，`Array`类采用一个整型参数，如维度将隐式转换为任何整数`Array`对象的是你不需要。 防止这种情况的一种方法是一个构造函数的 dummy 第二个参数的一种设计的方法  
  
 另一方面，设计 c + + 中的类类型时，不应提供转换对。 为此的最佳示例是标准字符串类。 隐式转换是单参数构造函数采用 C 样式字符串。 但是，它不提供相应的隐式转换运算符的将字符串转换为 C 样式字符串，对象而又而是要求用户显式调用命名的函数-在这种情况下， `c_str()`。  
  
 因此，将隐式/显式行为在转换运算符 （和封装到单个声明窗体的转换的集合） 相关联似乎是用于转换运算符，最终导致原始的c++支持的改进`explicit`关键字。 转换运算符的 Visual c + + 语言支持如下所示，这是比 C# 稍简略由于支持的转换算法的隐式应用程序的运算符的默认行为：  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 另一变化是处理单个自变量构造函数，如同它被声明为`explicit`。 这意味着，触发它的调用，以便显式强制转换不需要。 但请注意，是否定义显式转换运算符，它并不单参数构造函数，都会调用。  
  
## <a name="see-also"></a>请参阅  
 [类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)