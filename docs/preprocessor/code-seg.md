---
title: code_seg |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
dev_langs:
- C++
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f958d1652f82f297ae530c1e24bdf331976e0dc0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="codeseg"></a>code_seg
指定 .obj 文件中存储函数的文本段。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>备注  
 `code_seg` 杂注指令不控制为实例化模板生成的对象代码和编译器隐式生成的代码（例如特殊成员函数）的放置位置。 我们建议你使用[__declspec(code_seg(...))](../cpp/code-seg-declspec.md)特性，因为它可控制所有对象代码的放置位置。 其中包括编译器生成的代码。  
  
 A*段*在.obj 文件是命名的数据加载到作为一个单元的内存块。 A*文本段*是包含可执行代码的段。 在本文中，这些条款*段*和*部分*互换使用。  
  
 `code_seg` 杂注指令指示编译器将翻译单元中的所有后续对象代码放入到名为 `segment-name` 的文本段中。 默认情况下，.obj 文件中用于函数的文本段的名称为 .text。  
  
 无参数的 `code_seg` 杂注指令将后续对象代码的文本段名称重置为 .text。  
  
 **推送**（可选）  
 将一个记录置于内部编译器堆栈上。 A**推送**可以`identifier`和`segment-name`。  
  
 **pop** （可选）  
 从内部编译器堆栈的顶部移除一个记录。  
  
 `identifier`（可选）  
 如果用于**推送**，将名称分配给内部编译器堆栈上的记录。 如果用于**pop**，从之前的内部堆栈中弹出记录`identifier`被删除; 如果`identifier`找不到在内部堆栈上，会弹出任何内容。  
  
 `identifier` 让多个记录只用一个弹出**pop**命令。  
  
 “`segment-name`”（可选）  
 段的名称。 如果用于**pop**，弹出堆栈和`segment-name`会成为活动文本段名称。  
  
 “`segment-class`”（可选）  
 忽略但被包含，以便与 2.0 版之前的 C++ 版本兼容。  
  
 你可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)应用程序查看.obj 文件。 用于每个支持的目标体系结构的 DUMPBIN 版本随 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 一起提供。  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 `code_seg` 杂注指令控制对象代码的放置位置：  
  
```  
// pragma_directive_code_seg.cpp  
void func1() {                  // stored in .text  
}  
  
#pragma code_seg(".my_data1")  
void func2() {                  // stored in my_data1  
}  
  
#pragma code_seg(push, r1, ".my_data2")  
void func3() {                  // stored in my_data2  
}  
  
#pragma code_seg(pop, r1)      // stored in my_data1  
void func4() {  
}  
  
int main() {  
}  
```  
  
 不应该用于创建节的名称的列表，请参阅[/部分](../build/reference/section-specify-section-attributes.md)。  
  
 你还可以指定为初始化的数据部分 ([data_seg](../preprocessor/data-seg.md))，未初始化的数据 ([bss_seg](../preprocessor/bss-seg.md))，和常量变量 ([const_seg](../preprocessor/const-seg.md))。  
  
## <a name="see-also"></a>请参阅  
 [code_seg (__declspec)](../cpp/code-seg-declspec.md)   
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)