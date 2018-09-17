---
title: bss_seg |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c3a80e50bd0b012773a5e5a197674965f73b526
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711147"
---
# <a name="bssseg"></a>bss_seg
指定其中的未初始化变量存储在 .obj 文件中的段。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>备注  

可以使用查看 Obj 文件[dumpbin](../build/reference/dumpbin-command-line.md)应用程序。 未初始化数据的 .obj 文件中的默认段为 .bss。 在某些情况下使用的**bss_seg**可加快通过分组为一个部分未初始化的数据加载时间。  
  
**bss_seg**不带任何参数将段重置为.bss。  
  
**push**<br/>
（可选）将一个记录置于内部编译器堆栈上。 一个*pu*sh * 可以*标识符*并*段名称*。  
  
**pop**<br/>
（可选）从内部编译器堆栈的顶部移除记录。  
  
*identifier*<br/>
（可选）与一起使用时**推送**，将名称分配给内部编译器堆栈上的记录。 与一起使用时**pop**，弹出之前内部堆栈中弹出记录*标识符*被删除; 如果*标识符*中找不到内部堆栈中，会弹出任何内容。  
  
*标识符*使多个记录只用一个**pop**命令。  
  
*"段名称"*<br/>
（可选）段的名称。 与一起使用时**pop**，在堆栈中弹出和*段名称*将成为活动段名称。  
  
*"段类"*<br/>
（可选）包含有关使用 c + + 2.0 版之前的兼容性。 它将被忽略。  
  
## <a name="example"></a>示例  
  
```cpp  
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
  
此外可以指定部分，用于初始化的数据 ([data_seg](../preprocessor/data-seg.md))，函数 ([code_seg](../preprocessor/code-seg.md))，和常量变量 ([const_seg](../preprocessor/const-seg.md))。  
  
使用分配的数据**bss_seg**杂注不会保留有关其位置的任何信息。  
  
请参阅[/section](../build/reference/section-specify-section-attributes.md)的名称创建一个部分时，不应使用的列表。  
  
## <a name="see-also"></a>请参阅  
 
[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)