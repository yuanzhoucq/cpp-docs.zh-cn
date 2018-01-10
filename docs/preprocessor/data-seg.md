---
title: "data_seg |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
dev_langs: C++
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbc581e1237b25404b611e24bf8af46af4a166b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dataseg"></a>data_seg
指定 .obj 文件中用于存储初始化变量的数据段。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>备注  
 这些术语的含义*段*和*部分*是可互换的本主题。  
  
 可以使用查看 OBJ 文件[dumpbin](../build/reference/dumpbin-command-line.md)应用程序。 .obj 文件中用于存储初始化变量的默认段是 .data。 未初始化的变量被视为初始化为零并且存储在 .bss 中。  
  
 **data_seg**不带任何参数将段重置为.data。  
  
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
// pragma_directive_data_seg.cpp  
int h = 1;                     // stored in .data  
int i = 0;                     // stored in .bss  
#pragma data_seg(".my_data1")  
int j = 1;                     // stored in "my_data1"  
  
#pragma data_seg(push, stack1, ".my_data2")     
int l = 2;                     // stored in "my_data2"  
  
#pragma data_seg(pop, stack1)   // pop stack1 off the stack  
int m = 3;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 使用分配的数据**data_seg**不会保留有关其位置的任何信息。  
  
 请参阅[/部分](../build/reference/section-specify-section-attributes.md)的创建部分时不应使用的名称列表。  
  
 你还可以指定为常量变量的部分 ([const_seg](../preprocessor/const-seg.md))，未初始化的数据 ([bss_seg](../preprocessor/bss-seg.md))，和函数 ([code_seg](../preprocessor/code-seg.md))。  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)