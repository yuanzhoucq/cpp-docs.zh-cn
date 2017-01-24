---
title: "__declspec | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__declspec_cpp"
  - "__declspec"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++]"
ms.assetid: 832db681-e8e1-41ca-b78c-cd9d265cdb87
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __declspec
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 用于指定存储类信息的扩展特性语法使用 `__declspec` 关键字，该关键字指定给定类型的实例将与下面所列的 Microsoft 专用存储类特性一起存储。  其他存储类修饰符的示例包括 `static` 和 `extern` 关键字。  但是，这些关键字是 C 和 C\+\+ 语言的 ANSI 规范的一部分，并且本身不包含在扩展特性语法中。  扩展特性语法简化并标准化了 Microsoft 专用的 C 和 C \+\+ 语言扩展。  
  
## 语法  
 *decl\-specifier*:  
 `__declspec (`  *extended\-decl\-modifier\-seq*  `)`  
  
 *extended\-decl\-modifier\-seq*:  
 *extended\-decl\-modifier* opt  
  
 *extended\-decl\-modifier extended\-decl\-modifier\-seq*  
  
 *extended\-decl\-modifier*:  
 `align(` *\#* `)`  
  
 `allocate("` *segname* `")`  
  
 `appdomain`  
  
 `code_seg("` *segname* `")`  
  
 `deprecated`  
  
 `dllimport`  
  
 `dllexport`  
  
 `jitintrinsic`  
  
 `naked`  
  
 `noalias`  
  
 `noinline`  
  
 `noreturn`  
  
 `nothrow`  
  
 `novtable`  
  
 `process`  
  
 `property(`{`get=`*get\_func\_name*&#124;`,put=`*put\_func\_name*}`)`  
  
 `restrict`  
  
 `safebuffers`  
  
 `selectany`  
  
 `thread`  
  
 `uuid("` *ComObjectGUID* `")`  
  
 空格用于分隔声明修饰符序列。  示例显示在后面的部分。  
  
 扩展的特性语法支持以下 Microsoft 专用存储类特性：[align](../cpp/align-cpp.md)、[allocate](../cpp/allocate.md)、[appdomain](../cpp/appdomain.md)、[code\_seg](../cpp/code-seg-declspec.md)、[deprecated](../cpp/deprecated-cpp.md)、[dllexport](../cpp/dllexport-dllimport.md)、[dllimport](../cpp/dllexport-dllimport.md)、[jitintrinsic](../cpp/jitintrinsic.md)、[naked](../cpp/naked-cpp.md)、[noalias](../cpp/noalias.md)、[noinline](../cpp/noinline.md)、[noreturn](../cpp/noreturn.md)、[nothrow](../cpp/nothrow-cpp.md)、[novtable](../cpp/novtable.md)、[process](../cpp/process.md)、[restrict](../cpp/restrict.md)、[safebuffers](../cpp/safebuffers.md)、[selectany](../cpp/selectany.md) 和 [thread](../cpp/thread.md)。  它还支持以下 COM 对象特性：[property](../cpp/property-cpp.md) 和 [uuid](../cpp/uuid-cpp.md)。  
  
 `code_seg`、`dllexport`、`dllimport`、`naked`、`noalias`、`nothrow`、`property`、`restrict`、`selectany`、`thread` 和 `uuid` 存储类特性只是要应用它们的对象或函数的声明的属性。  `thread` 特性仅影响数据和对象。  `naked` 特性仅影响函数。  `dllimport` 和 `dllexport` 特性影响函数、数据和对象。  `property`、`selectany` 和 `uuid` 特性影响 COM 对象。  
  
 应将 `__declspec` 关键字放在简单声明的开头。  编译器将在不发出警告的情况下忽略位于声明中的 \* 或 & 后面以及变量标识符前面的任何 `__declspec` 关键字。  
  
 在用户定义的类型声明的开头指定的 `__declspec` 特性适用于该类型的变量。  例如：  
  
```  
__declspec(dllimport) class X {} varX;  
```  
  
 在本例中，此特性应用于 `varX`。  位于 `class` 或 `struct` 关键字后的 `__declspec` 特性适用于用户定义的类型。  例如：  
  
```  
class __declspec(dllimport) X {};  
```  
  
 在本例中，此特性应用于 `X`。  
  
 关于将 `__declspec` 特性用于简单声明的一般准则如下所示：  
  
```  
  
decl-specifier-seq declarator-list;  
```  
  
 此外，*decl\-specifier\-seq* 还应包含一个基类型（如  `int`、`float`、`typedef` 或类名）、存储类（如  `static` 和 `extern`）或 `__declspec` 扩展。  此外，*init\-declarator\-list* 还应包含声明的指针部分。  例如：  
  
```  
__declspec(selectany) int * pi1 = 0;   //OK, selectany & int both part of decl-specifier  
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier  
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator  
```  
  
 以下代码声明了一个整数线程局部变量，并用一个值对其进行了初始化：  
  
```  
// Example of the __declspec keyword  
__declspec( thread ) int tls_i = 1;  
```  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [C 扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)