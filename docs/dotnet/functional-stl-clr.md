---
title: "功能 (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <cliext/functional>
dev_langs:
- C++
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8e731767401964045307635a428d7606d628aca8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="functional-stlclr"></a>functional (STL/CLR)
包括 STL/CLR 标头`<cliext/functional>`定义大量的模板类和相关的模板委托和函数。  
  
## <a name="syntax"></a>语法  
  
```  
#include <functional>  
```  
  
## <a name="declarations"></a>声明  
  
|委托|描述|  
|--------------|-----------------|  
|[binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)|两个参数的委托。|  
|[binary_delegate_noreturn (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)|返回两个参数委托`void`。|  
|[unary_delegate (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)|一个参数的委托。|  
|[unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)|返回的单自变量委托`void`。|  
  
|类|描述|  
|-----------|-----------------|  
|[binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)|要求反的两个参数函子的函子。|  
|[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)|若要将第一个自变量绑定到两个参数函子的函子。|  
|[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)|若要将第二个参数绑定到两个参数函子的函子。|  
|[divides (STL/CLR)](../dotnet/divides-stl-clr.md)|将划分函子。|  
|[equal_to (STL/CLR)](../dotnet/equal-to-stl-clr.md)|相等比较函子。|  
|[greater (STL/CLR)](../dotnet/greater-stl-clr.md)|更大的比较函子。|  
|[greater_equal (STL/CLR)](../dotnet/greater-equal-stl-clr.md)|大于或等于比较函子。|  
|[less (STL/CLR)](../dotnet/less-stl-clr.md)|小于比较函子。|  
|[less_equal (STL/CLR)](../dotnet/less-equal-stl-clr.md)|小于或等于比较函子。|  
|[logical_and (STL/CLR)](../dotnet/logical-and-stl-clr.md)|逻辑 AND 函子。|  
|[logical_not (STL/CLR)](../dotnet/logical-not-stl-clr.md)|逻辑不函子。|  
|[logical_or (STL/CLR)](../dotnet/logical-or-stl-clr.md)|逻辑 OR 函子。|  
|[minus (STL/CLR)](../dotnet/minus-stl-clr.md)|减去函子。|  
|[modulus (STL/CLR)](../dotnet/modulus-stl-clr.md)|取模函子。|  
|[multiplies (STL/CLR)](../dotnet/multiplies-stl-clr.md)|乘函子。|  
|[negate (STL/CLR)](../dotnet/negate-stl-clr.md)|返回求反后其自变量的函子。|  
|[not_equal_to (STL/CLR)](../dotnet/not-equal-to-stl-clr.md)|不等于比较函子。|  
|[plus (STL/CLR)](../dotnet/plus-stl-clr.md)|添加函子。|  
|[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)|要求反单自变量函子的函子。|  
  
|函数|描述|  
|--------------|-----------------|  
|[bind1st (STL/CLR)](../dotnet/bind1st-stl-clr.md)|生成自变量和函子的 binder1st。|  
|[bind2nd (STL/CLR)](../dotnet/bind2nd-stl-clr.md)|生成自变量和函子的 binder2nd。|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|生成函子 unary_negate。|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|生成函子 binary_negate。|  
  
## <a name="requirements"></a>惠?  
 **标头：** \<功能 cliext/>  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)