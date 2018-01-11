---
title: "bss_seg |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0dd1e24127129ef833cfd4906085eabbf1e5c380
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bssseg"></a>bss_seg
指定其中的未初始化变量存储在 .obj 文件中的段。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>备注  
 可以使用查看 Obj 文件[dumpbin](../build/reference/dumpbin-command-line.md)应用程序。 未初始化数据的 .obj 文件中的默认段为 .bss。 在某些情况下使用的**bss_seg**速度加载时间将未初始化的数据分组到一个部分。  
  
 **bss_seg**不带任何参数将段重置为.bss。  
  
 **推送**（可选）  
 将一个记录置于内部编译器堆栈上。 A**推送**可以*标识符*和*段名称*。  
  
 **pop** （可选）  
 从内部编译器堆栈的顶部移除一个记录。  
  
 *标识符*（可选）  
 如果用于**推送**，将名称分配给内部编译器堆栈上的记录。 如果用于**pop**，从之前的内部堆栈中弹出记录*标识符*被删除; 如果*标识符*找不到在内部堆栈上，会弹出任何内容。  
  
 *标识符*让多个记录有一条弹出**pop**命令。  
  
 *"段名称"*（可选）  
 段的名称。 如果用于**pop**，弹出堆栈和*段名称*会成为活动段名称。  
  
 *"段类"* （可选）  
 包括与 2.0 版之前的 C++ 的兼容性。 它将被忽略。  
  
## <a name="example"></a>示例  
  
```  
// pragma_directive_bss_seg.cpp  
int i;                     // stored in .bss  
#pragma bss_seg(".my_data1")  
int j;                     // stored in "my_data1"  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;                     // stored in "my_data2"  
  
#pragma bss_seg(pop, stack1)   // pop stack1 from stack  
int m;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 你还可以指定为初始化的数据部分 ([data_seg](../preprocessor/data-seg.md))，函数 ([code_seg](../preprocessor/code-seg.md))，和常量变量 ([const_seg](../preprocessor/const-seg.md))。  
  
 使用分配的数据**bss_seg**杂注不会保留有关其位置的任何信息。  
  
 请参阅[/部分](../build/reference/section-specify-section-attributes.md)的创建部分时不应使用的名称列表。  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)