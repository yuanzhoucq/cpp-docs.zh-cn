---
title: "__declspec |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __declspec_cpp
- __declspec
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++]
ms.assetid: 832db681-e8e1-41ca-b78c-cd9d265cdb87
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: b29b6243611f1ca59a579869469c803d3735f9df
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="declspec"></a>__declspec
## <a name="microsoft-specific"></a>Microsoft 专用  
 用于指定存储类信息的扩展特性语法使用 `__declspec` 关键字，该关键字指定给定类型的实例将与下面所列的 Microsoft 专用存储类特性一起存储。 其他存储类修饰符的示例包括 `static` 和 `extern` 关键字。 但是，这些关键字是 C 和 C++ 语言的 ANSI 规范的一部分，并且本身不包含在扩展特性语法中。 扩展特性语法简化并标准化了 Microsoft 专用的 C 和 C ++ 语言扩展。  
  
## <a name="grammar"></a>语法  
 *声明说明符*:  
 `__declspec (`  *扩展声明修饰符 seq*  `)`  
  
 extended-decl-modifier-seq：  
 *extended-decl-modifier*opt  
  
 *扩展声明修饰符扩展-声明-修饰符-seq*  
  
 extended-decl-modifier：  
 `align(` *#* `)`  
  
 `allocate("`*segname*`")`  
  
 `appdomain`  
  
 `code_seg("`*segname*`")`  
  
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
  
 `property(`{`get=`*get_func_name*&#124;`,put=`*put_func_name*}`)`  
  
 `restrict`  
  
 `safebuffers`  
  
 `selectany`  
  
 `thread`  
  
 `uuid("`*ComObjectGUID*`")`  
  
 空格用于分隔声明修饰符序列。 示例显示在后面的部分。  
  
 扩展的特性语法支持这些 Microsoft 专用存储类特性：[对齐](../cpp/align-cpp.md)，[分配](../cpp/allocate.md)， [appdomain](../cpp/appdomain.md)， [code_seg](../cpp/code-seg-declspec.md)，[弃用](../cpp/deprecated-cpp.md)， [dllexport](../cpp/dllexport-dllimport.md)， [dllimport](../cpp/dllexport-dllimport.md)， [jitintrinsic](../cpp/jitintrinsic.md)，[裸](../cpp/naked-cpp.md)， [noalias](../cpp/noalias.md)， [noinline](../cpp/noinline.md)， [noreturn](../cpp/noreturn.md)， [nothrow](../cpp/nothrow-cpp.md)， [novtable](../cpp/novtable.md)[过程](../cpp/process.md)，[限制](../cpp/restrict.md)， [safebuffers](../cpp/safebuffers.md)， [selectany](../cpp/selectany.md)，和[线程](../cpp/thread.md)。 它还支持这些 COM 对象特性：[属性](../cpp/property-cpp.md)和[uuid](../cpp/uuid-cpp.md)。  
  
 `code_seg`、`dllexport`、`dllimport`、`naked`、`noalias`、`nothrow`、`property`、`restrict`、`selectany`、`thread` 和 `uuid` 存储类特性只是要应用它们的对象或函数的声明的属性。 `thread` 特性仅影响数据和对象。 `naked` 特性仅影响函数。 `dllimport` 和 `dllexport` 特性影响函数、数据和对象。 `property`、`selectany` 和 `uuid` 特性影响 COM 对象。  
  
 应将 `__declspec` 关键字放在简单声明的开头。 编译器将在不发出警告的情况下忽略位于声明中的 * 或 & 后面以及变量标识符前面的任何 `__declspec` 关键字。  
  
 在用户定义的类型声明的开头指定的 `__declspec` 特性适用于该类型的变量。 例如：  
  
```  
__declspec(dllimport) class X {} varX;  
```  
  
 在本例中，此特性应用于 `varX`。 位于 `__declspec` 或 `class` 关键字后的 `struct` 特性适用于用户定义的类型。 例如：  
  
```  
class __declspec(dllimport) X {};  
```  
  
 在本例中，此特性应用于 `X`。  
  
 关于将 `__declspec` 特性用于简单声明的一般准则如下所示：  
  
```  
  
decl-specifier-seq  
declarator-list;  
```  
  
 *声明说明符 seq*应包含，除了别的之外的基类型 (例如`int`， `float`、 `typedef`，或类名)，存储类 (例如`static`， `extern`)，或`__declspec`扩展。 *Init 声明符列表*应包含，除了别的之外声明的指针部分。 例如:   
  
```  
__declspec(selectany) int * pi1 = 0;   //OK, selectany & int both part of decl-specifier  
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier  
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator  
```  
  
 以下代码声明了一个整数线程本地变量，并用一个值对其进行了初始化：  
  
```  
// Example of the __declspec keyword  
__declspec( thread ) int tls_i = 1;  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [C 扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)
