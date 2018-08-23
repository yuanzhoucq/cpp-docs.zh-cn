---
title: code_seg |Microsoft Docs
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
ms.openlocfilehash: 052e9a55d443fa263ecf8443c9e3933baeb1f3b8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539551"
---
# <a name="codeseg"></a>code_seg
指定 .obj 文件中存储函数的文本段。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>备注  
 
**Code_seg**杂注指令不控制为实例化模板生成的对象代码，也不由编译器隐式生成的代码的位置 — 例如，特殊成员函数。 我们建议你使用[__declspec(code_seg(...))](../cpp/code-seg-declspec.md)特性，因为这样可以控制所有对象代码的位置。 其中包括编译器生成的代码。  
  
一个*段*在.obj 文件是加载到内存中作为一个单元的数据的命名的块。 一个*文本段*是包含可执行代码段。 在本文中，术语*段*并*部分*互换使用。  
  
**Code_seg**杂注指令指示编译器将翻译单元中的所有后续对象代码放入名为的文本段*段名称*。 默认情况下，.obj 文件中用于函数的文本段的名称为 .text。  
  
一个**code_seg**不带参数的杂注指令将后续对象代码的文本段名称重置为.text。  
  
*推送*（可选）  
将一个记录置于内部编译器堆栈上。 一个*推送*可以*标识符*并*段名称*。  
  
*pop* （可选）  
从内部编译器堆栈的顶部移除一个记录。  
  
*标识符*（可选）  
与一起使用时*推送*，将名称分配给内部编译器堆栈上的记录。 与一起使用时*pop*，弹出之前内部堆栈中弹出记录*标识符*被删除; 如果*标识符*中找不到内部堆栈中，会弹出任何内容。  
  
*标识符*使多个记录将只用一个*pop*命令。  
  
"*段名称*"（可选）  
段的名称。 与一起使用时*pop*，在堆栈中弹出和*段名称*会成为活动文本段名称。  
  
"*段类*"（可选）  
忽略但被包含，以便与 2.0 版之前的 C++ 版本兼容。  
  
可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)应用程序查看.obj 文件。 使用 Visual Studio 包含适用于每个受支持的目标体系结构的 DUMPBIN 版本。  
  
## <a name="example"></a>示例  

此示例演示如何使用**code_seg**杂注指令控制对象代码的放置位置：  
  
```cpp  
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
  
不应使用可创建节的名称的列表，请参阅[/section](../build/reference/section-specify-section-attributes.md)。  
  
此外可以指定部分，用于初始化的数据 ([data_seg](../preprocessor/data-seg.md))，未初始化的数据 ([bss_seg](../preprocessor/bss-seg.md))，和常量变量 ([const_seg](../preprocessor/const-seg.md))。  
  
## <a name="see-also"></a>请参阅  
 
[code_seg (__declspec)](../cpp/code-seg-declspec.md)   
[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)