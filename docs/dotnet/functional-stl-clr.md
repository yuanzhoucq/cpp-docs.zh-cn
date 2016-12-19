---
title: "functional (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "<cliext/functional>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/functional> 标头 [STL/CLR]"
  - "<functional> 标头 [STL/CLR]"
  - "功能性函数 [STL/CLR]"
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# functional (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL\/CLR 包括标头定义许多的模板类的 `<cliext/functional>` 和相关模板函数和委托。  
  
## 语法  
  
```  
#include <functional>  
```  
  
## 声明  
  
|Delegate|说明|  
|--------------|--------|  
|[binary\_delegate](../dotnet/binary-delegate-stl-clr.md)|两个委托参数。|  
|[binary\_delegate\_noreturn](../dotnet/binary-delegate-noreturn-stl-clr.md)|返回 `void`的两参数委托。|  
|[unary\_delegate](../dotnet/unary-delegate-stl-clr.md)|一个委托参数。|  
|[unary\_delegate\_noreturn](../dotnet/unary-delegate-noreturn-stl-clr.md)|返回 `void`的一个参数委托。|  
  
|类|说明|  
|-------|--------|  
|[binary\_negate](../dotnet/binary-negate-stl-clr.md)|消除两个参数 functor 的 Functor。|  
|[binder1st](../dotnet/binder1st-stl-clr.md)|绑定第一个参数的 Functor 为两个参数 functor。|  
|[binder2nd](../dotnet/binder2nd-stl-clr.md)|绑定第二个参数的 Functor 为两个参数 functor。|  
|[divides](../dotnet/divides-stl-clr.md)|除以functor。|  
|[equal\_to](../dotnet/equal-to-stl-clr.md)|相等比较 functor。|  
|[greater](../dotnet/greater-stl-clr.md)|更大比较 functor。|  
|[greater\_equal](../dotnet/greater-equal-stl-clr.md)|更大或等于比较 functor。|  
|[less](../dotnet/less-stl-clr.md)|较低比较 functor。|  
|[less\_equal](../dotnet/less-equal-stl-clr.md)|小于或等于比较 functor。|  
|[logical\_and](../dotnet/logical-and-stl-clr.md)|逻辑和 functor。|  
|[logical\_not](../dotnet/logical-not-stl-clr.md)|逻辑非functor。|  
|[logical\_or](../dotnet/logical-or-stl-clr.md)|逻辑或 functor。|  
|[minus](../dotnet/minus-stl-clr.md)|加 functor。|  
|[modulus](../dotnet/modulus-stl-clr.md)|模数 functor。|  
|[multiplies](../dotnet/multiplies-stl-clr.md)|相乘 functor。|  
|[negate](../dotnet/negate-stl-clr.md)|返回参数的 Functor 求反。|  
|[not\_equal\_to](../dotnet/not-equal-to-stl-clr.md)|不相等比较 functor。|  
|[plus](../dotnet/plus-stl-clr.md)|添加 functor。|  
|[unary\_negate](../dotnet/unary-negate-stl-clr.md)|消除一个参数 functor 的 Functor。|  
  
|功能|说明|  
|--------|--------|  
|[bind1st](../dotnet/bind1st-stl-clr.md)|生成第一个参数和仿函数的。|  
|[bind2nd](../dotnet/bind2nd-stl-clr.md)|生成第二个参数和仿函数的。|  
|[not1](../dotnet/not1-stl-clr.md)|生成 functor 的一 unary\_negate。|  
|[not1](../dotnet/not1-stl-clr.md)|生成 functor 的一 binary\_negate。|  
  
## 要求  
 **头文件:** \<cliext\/functional\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)