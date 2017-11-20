---
title: "pointers_to_members |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
dev_langs: C++
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4fc108f6f4755319d500227d9163dc090847e2ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="pointerstomembers"></a>pointers_to_members
**C + + 专用**  
  
 指定是否可以在类成员关联的类定义之前声明指向类成员的指针，以及类成员是否用于控制指针大小和解释指针所需的代码。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )  
```  
  
## <a name="remarks"></a>备注  
 你可以将放置**pointers_to_members**作为备用使用源文件中的杂注[/vmx](../build/reference/vmb-vmg-representation-method.md)编译器选项或[继承关键字](../cpp/inheritance-keywords.md)。  
  
 *指针声明*自变量指定是否声明指针到成员关联的函数定义之前还是之后。 *指针声明*自变量是下列两个符号之一：  
  
|参数|注释|  
|--------------|--------------|  
|**full_generality**|生成安全的（有时并非最佳）代码。 你使用**full_generality**如果关联的类定义之前声明指向成员的任何指针。 此自变量始终使用由指定的指针表示形式*大多数常规表示*自变量。 等效于 /vmg。|  
|**best_case**|使用指向成员的所有指针的最佳大小写表示形式生成安全的最佳代码。 要求在声明指向类成员的指针之前定义此类。 默认值是**best_case**。|  
  
 *大多数常规表示*参数指定编译器可以安全地用来引用指向翻译单元中的类的成员的任何指针的最小指针表示形式。 自变量可以是下列项之一：  
  
|参数|注释|  
|--------------|--------------|  
|**单继承**|最常规的表示形式为单一继承（指向成员函数的指针）。 如果类定义（已为其声明指向成员的指针）的继承模型为多重继承或虚拟继承，则会导致出现错误。|  
|**多重继承**|最常规的表示形式为多重继承（指向成员函数的指针）。 如果类定义（已为其声明指向成员的指针）的继承模型为虚拟继承，则会导致出现错误。|  
|**virtual_inheritance**|最常规的表示形式为虚拟继承（指向成员函数的指针）。 绝不会导致出现错误。 这是默认自变量时**#pragma pointers_to_members （full_generality)**使用。|  
  
> [!CAUTION]
>  建议您仅将 `pointers_to_members` 杂注放置在要影响的源代码文件中以及所有 `#include` 指令之后。 此做法可以减小杂注影响其他文件以及为同一变量、函数或类名意外指定多个定义的风险。  
  
## <a name="example"></a>示例  
  
```  
//   Specify single-inheritance only  
#pragma pointers_to_members( full_generality, single_inheritance )  
```  
  
## <a name="end-c-specific"></a>结束 C++ 专用  
  
## <a name="see-also"></a>另请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)