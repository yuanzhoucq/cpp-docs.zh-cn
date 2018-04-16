---
title: "编译器选项宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f48abc864133849353aeccf82ea3eb9aab1edb5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-options-macros"></a>编译器选项宏
这些宏控制特定的编译器功能。  
  
|||  
|-|-|  
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|这样在项目中的错误的符号转换从以前版本的 atl。|  
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|如果一个或多个对象使用单元线程处理中定义。|  
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|使某些`CString`显式，阻止任何无意转换构造函数。|  
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|定义此宏，以便使用 c + + 标准合规语法，用于生成 C4867 编译器错误，当使用非标准语法时初始化指向成员函数的指针。|  
|[_ATL_FREE_THREADED](#_atl_free_threaded)|如果一个或多个对象使用免费或非特定线程处理中定义。|  
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|符号指示项目将具有标记为同时，免费或非特定的对象。 宏[_ATL_FREE_THREADED](#_atl_free_threaded)应改为使用。|  
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|这会阻止的命名空间作为 atl。 默认情况下使用符号|  
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|以防止与 COM 相关的代码将与您的项目正在编译的符号。|  
|[ATL_NO_VTABLE](#atl_no_vtable)|正在初始化类的构造函数和析构函数中阻止 vtable 指针符号。|  
|[ATL_NOINLINE](#atl_noinline)|符号指示函数不应为内联。|  
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|如果你的对象的所有使用单个线程处理模型中定义。|  
  
##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS  
 这样在项目中的错误的符号转换从以前版本的 atl。  
  
```
#define _ATL_ALL_WARNINGS
```  
  
### <a name="remarks"></a>备注  
 Visual c + +.NET 2002 中之前, ATL 禁用大量的警告，并保留它们被禁用，这样它们永远不会显示在用户代码。 尤其是在下列情况下：  
  
-   C4127 条件表达式是常量  
  
-   C4786 identifier： 标识符被截断为 number 个字符中的调试信息  
  
-   使用 C4201 非标准扩展： 无名称结构/联合  
  
-   C4103 filename: #pragma 包用于更改对齐方式  
  
-   C4291 declaration： 找到了; 不匹配运算符 delete如果初始化引发异常，不会释放内存  
  
-   C4268 identifier: const 全局静态/数据使用编译器生成默认构造函数初始化填充零的对象  
  
-   C4702 无法访问的代码  
  
 在项目转换从以前版本中，仍通过库标头禁用这些警告。  
  
 通过将以下行添加到 stdafx.h 文件中包括库标头之前，可以更改此行为。  
  
 [!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]  
  
 如果此`#define`添加，ATL 标头非常小心地保留这些警告的状态，以便它们不全局禁用 （或用户显式禁用个别警告，不启用它们）。  
  
 新的项目具有这`#define`在 stdafx.h 中设置默认情况下。  
  
##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED  
 如果一个或多个对象使用单元线程处理中定义。  
  
```
_ATL_APARTMENT_THREADED
```  
  
### <a name="remarks"></a>备注  
 指定单元线程处理。 请参阅[指定项目的线程处理模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)其他线程处理选项，和[选项，ATL 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)有关的说明的线程处理模型可用于 ATL 对象。  
  
##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS  
 使某些`CString`显式，阻止任何无意转换构造函数。  
  
```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```  
  
### <a name="remarks"></a>备注  
 这定义，采用单个参数的所有 CString 构造函数被都编译用 explicit 关键字，这会阻止隐式转换的输入自变量中。 这意味着例如，在定义了 _UNICODE，如果你尝试使用 char * 字符串作为 CString 构造函数自变量，将导致编译器错误。 在你需要防止窄和宽字符串类型之间的隐式转换的情况下使用此宏。  
  
 通过使用 _T 宏上所有构造函数字符串自变量，可以定义 _ATL_CSTRING_EXPLICIT_CONSTRUCTORS 和避免无论是否定义了 _UNICODE 编译错误。  
  
##  <a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING  
 定义此宏，以便强制为指向成员函数使用 ANSI c + + 符合标准的语法。 使用此宏将导致在非标准语法用于初始化指向成员函数的指针时生成 C4867 编译器错误。  
  
```
#define _ATL_ENABLE_PTM_WARNING
```  
  
### <a name="remarks"></a>备注  
 ATL 和 MFC 库已更改以匹配 Visual c + + 编译器改进了标准 c + + 合规性。 根据 ANSI c + + 标准中，指向类成员函数的指针的语法应该`&CMyClass::MyFunc`。  
  
 当[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)未定义 （默认情况下），以便在早期版本中创建的代码可以继续像以前那样生成 ATL/MFC 禁用 （值得注意的是消息映射） 的宏映射中的 C4867 错误。 如果你定义**_ATL_ENABLE_PTM_WARNING**，你的代码应符合 c + + 标准。  
  
 但是，非标准窗体已弃用，因此你需要将现有代码移到 c + + 标准合规语法。 例如，以下内容：  
  
 [!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]  
  
 应更改为：  
  
 [!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]  
  
 请注意，添加 & 字符的映射宏，则不应添加它再次在代码中。  
  
##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED  
 如果一个或多个对象使用免费或非特定线程处理中定义。  
  
```
_ATL_FREE_THREADED
```  
  
### <a name="remarks"></a>备注  
 指定自由线程处理。 自由线程处理相当于多线程单元模型。 请参阅[指定项目的线程处理模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)其他线程处理选项，和[选项，ATL 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)有关的说明的线程处理模型可用于 ATL 对象。  
  
##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED  
 符号指示项目将具有标记为同时，免费或非特定的对象。  
  
```
_ATL_MULTI_THREADED
```  
  
### <a name="remarks"></a>备注  
 如果定义此符号，ATL 会中拉入正确将同步到的全局数据的访问的代码。 新代码应使用等效宏[_ATL_FREE_THREADED](#_atl_free_threaded)相反。  
  
##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE  
 这会阻止的命名空间作为 atl。 默认情况下使用符号  
  
```
_ATL_NO_AUTOMATIC_NAMESPACE
```  
  
### <a name="remarks"></a>备注  
 如果未定义此符号，则将执行包括 atlbase.h**使用命名空间 ATL**默认情况下，这可能会导致命名冲突。 若要防止此情况，定义此符号。  
  
##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT  
 以防止与 COM 相关的代码将与您的项目正在编译的符号。  
  
```
_ATL_NO_COM_SUPPORT```  
  
##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE  
 A symbol that prevents the vtable pointer from being initialized in the class's constructor and destructor.  
  
```
ATL_NO_VTABLE
```  
  
### Remarks  
 If the vtable pointer is prevented from being initialized in the class's constructor and destructor, the linker can eliminate the vtable and all of the functions to which it points. Expands to **__declspec(novtable)**.  
  
### Example  
 [!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]  
  
##  <a name="atl_noinline"></a>  ATL_NOINLINE  
 A symbol that indicates a function should not be inlined.  
  
```
    ATL_NOINLINE inline
    myfunction
 { ... }
```  
  
### Parameters  
 *myfunction*  
 The function that should not be inlined.  
  
### Remarks  
 Use this symbol if you want to ensure a function does not get inlined by the compiler, even though it must be declared as inline so that it can be placed in a header file. Expands to **__declspec(noinline)**.  
  
##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED  
 Define if all of your objects use the single threading model  
  
```
_ATL_SINGLE_THREADED
```  
  
### Remarks  
 Specifies that the object always runs in the primary COM thread. See [Specifying the Project's Threading Model](../../atl/specifying-the-threading-model-for-a-project-atl.md) for other threading options, and [Options, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) for a description of the threading models available for an ATL object.  
  
## See Also  
 [Macros](../../atl/reference/atl-macros.md)
