---
title: "extern 存储类说明符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 448a659afaf7a0251d500da3d9878d30550b9180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="extern-storage-class-specifier"></a>extern 存储类说明符
使用 `extern` 存储类说明符声明的变量是对名称与在程序的任何源文件的外部级别定义的名称相同的变量的引用。 内部 `extern` 声明用于使外部级别变量定义在块中可见。 除非在外部级别另有声明，否则使用 `extern` 关键字声明的变量仅在声明它的块中可见。  
  
## <a name="example"></a>示例  
 此示例阐释内部和外部级别的声明：  
  
```  
// extern_StorageClassSpecified.c  
#include <stdio.h>  
  
void other( void );  
  
int main()  
{  
    // Reference to i, defined below:   
    extern int i;  
  
    // Initial value is zero; a is visible only within main:   
    static int a;  
  
    // b is stored in a register, if possible:   
    register int b = 0;  
  
    // Default storage class is auto:   
    int c = 0;  
  
    // Values printed are 1, 0, 0, 0:   
    printf_s( "%d\n%d\n%d\n%d\n", i, a, b, c );  
    other();  
    return;  
}  
  
int i = 1;  
  
void other( void )  
{  
    // Address of global i assigned to pointer variable:  
    static int *external_i = &i;  
  
    // i is redefined; global i no longer visible:   
    int i = 16;  
  
    // This a is visible only within the other function:   
    static int a = 2;  
  
    a += 2;  
    // Values printed are 16, 4, and 1:  
    printf_s( "%d\n%d\n%d\n", i, a, *external_i );  
}  
```  
  
 在此示例中，变量 `i` 是使用初始值 1 在外部级别定义的。 `extern` 函数中的 `main` 声明用于声明对外部级别 `i` 的引用。 由于忽略了初始值设定项，因此默认情况下 static 变量 `a` 将初始化为 0。 对 `printf` 的调用将输出值 1、0、0 和 0。  
  
 在 `other` 函数中，全局变量 `i` 的地址用于初始化 static 指针变量 `external_i`。 此用法之所以有效是因为全局变量具有 static 生存期，这意味着其地址在程序执行期间不会更改。 接下来，变量 `i` 将重新定义为初始值为 16 的局部变量。 此重新定义不会影响外部级别 `i` 的值（通过对局部变量使用该外部级别的名称来隐藏）。 全局 `i` 的值现在只能在此块中通过指针 `external_i` 间接访问。 将 auto 变量 `i` 的地址分配给指针的尝试无效，因为每次输入块时该地址可能都不一样。 变量 `a` 将声明为 static 变量并初始化为 2。 此 `a` 不与 `main` 中的 `a` 冲突，因为内部级别的 static 变量仅在声明它们的块中可见。  
  
 变量 `a` 增加了 2，并给出结果 4。 如果在同一程序中再次调用 `other` 函数，则 `a` 的初始值将为 4。 当程序退出然后重新输入声明内部 static 变量的块时，这些变量将保留其值。  
  
## <a name="see-also"></a>请参阅  
 [内部级别声明的存储类说明符](../c-language/storage-class-specifiers-for-internal-level-declarations.md)