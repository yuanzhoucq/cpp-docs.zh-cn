---
title: "提示文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cpp.hint
- vc.hint.file
dev_langs:
- C++
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 432b5fa5041a7997c9df0593dc511c29854387ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hint-files"></a>提示文件
A*提示文件*可帮助 Visual Studio 集成的开发环境 (IDE) 解释 Visual c + + 标识符，例如的函数和宏的名称。 当你打开的 Visual c + + 项目，IDE 的*分析系统*分析项目中每个源文件中的代码并收集有关每个标识符的信息。 然后，IDE 使用该信息支持功能，如**类视图**浏览器和**导航栏**。  
  
 分析系统，在 Visual c + + 2010年中引入，理解 C/c + + 语法，但可以曲解包含宏的语句。 如果宏导致要编写语法不正确的源代码，该语句可以被错误解释。 在编译的源代码，并预替换时，该语句可能成为语法正确[宏标识符](../preprocessor/hash-define-directive-c-cpp.md)利用自己的定义。 分析系统工作而无需生成项目，因为它使用提示文件来解释宏。 因此，如浏览功能**类视图**立即可用。  
  
 提示文件包含用户可自定义*提示*，它具有与 C/c + + 宏定义相同的语法。 Visual c + + 包括内置提示文件，它足以满足大多数项目，但你可以创建你自己的提示文件以改进 Visual Studio 处理标识符的方式。  
  
> [!IMPORTANT]
>  如果你修改或添加提示文件，则必须删除的.sdf 文件和/或 VC.db 文件中所作的更改才会生效的解决方案中。  
  
## <a name="scenario"></a>方案  
 假定下面的代码中使用检查源文件**类视图**浏览器。 `STDMETHOD`宏声明一个名为方法`myMethod`它接受一个参数并返回指向的指针**HRESULT**。  
  
```  
// Source code file.  
STDMETHOD(myMethod)(int parameter1);  
```  
  
 下面的宏定义位于单独的头文件。  
  
```  
// Header file.  
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)  
#define STDMETHODCALLTYPE __stdcall  
#define HRESULT void*  
```  
  
 分析系统无法解释的源代码，由于一个名为 STDMETHOD 函数看起来声明和该声明的语法不正确的因为它具有两个形参列表。 分析系统不会打开该标头文件，找到的定义`STDMETHOD`， `STDMETHODCALLTYPE`，和`HRESULT`宏。 因为分析系统无法解释`STDMETHOD`宏，它将忽略整个语句，然后继续分析。  
  
 分析系统不使用标头文件，因为你的项目可能依赖于一个或多个重要的标头文件。 如果任何标头文件发生更改，则分析系统可能需要重新检查的所有标头文件在项目中，从而降低 IDE 的性能。 分析系统相反，使用提示，以指定如何处理`STDMETHOD`， `STDMETHODCALLTYPE`，和`HRESULT`宏。  
  
 如何知道需要提示？ 如果你需要一个提示，哪种类型应你创建和？ 一次登录提示，则需要是如果中的标识符的视图**类视图**与中的视图不一致**编辑器**。 例如，**类视图**可能不显示你知道的类成员存在，或成员的名称不正确。 有关解决常见问题的提示的类型的详细信息，请参阅什么宏需要提示？本主题中后面的部分。  
  
## <a name="architecture"></a>体系结构  
 提示文件适用于物理目录，而不是逻辑目录图中所示**解决方案资源管理器**。 无需将提示文件添加到你要影响的提示文件的项目。 仅在分析源文件时，分析系统使用提示文件。  
  
 名为每个提示文件**cpp.hint**。 因此，多个目录可以包含提示文件，但只有一个提示文件可以发生在特定的目录。  
  
 可以通过零个或多个提示文件影响你的项目。 如果没有提示的文件，分析系统将使用错误恢复技术来忽略无法解密的源代码。 否则，分析系统使用以下策略来查找和收集提示。  
  
### <a name="search-order"></a>搜索顺序  
 分析系统按以下顺序搜索提示文件目录。  
  
-   Visual c + + 中包含的安装包的目录 (**vcpackages**)。 此目录包含一个内置提示文件，如描述频繁使用的系统文件中的符号**windows.h**。 因此，你的项目将自动继承大部分它需要的提示。  
  
-   包含本身的源文件的目录中的源文件的根目录路径。 在典型的 Visual c + + 项目中，根目录包含的解决方案或项目文件。  
  
     此规则的例外是如果*停止文件*到源代码文件的路径。 停止文件提供了对搜索顺序的其他控制，是名为任何文件**cpp.stop**。 而不是从根目录开始，分析系统将从包含到包含源文件的目录的停止文件的目录搜索。 在典型项目中，你不需要停止文件。  
  
### <a name="hint-gathering"></a>提示收集  
 提示文件包含零个或多*提示*。 提示删除一样 C/c + + 宏或定义。 也就是说，`#define`预处理器指令创建或重新定义了提示，和`#undef`指令删除提示。  
  
 分析系统中前面所述的搜索顺序打开每个提示的文件、 将每个文件的提示累积到一组*有效提示*，然后使用有效的提示来解释在代码中的标识符。  
  
 分析系统使用以下规则累积提示。  
  
-   如果新提示指定尚未定义一个名称，新的提示会将名称添加到有效的提示。  
  
-   如果新提示指定已定义的名称，新的提示将重新定义现有的提示。  
  
-   如果新的提示是`#undef`指定现有的有效提示的指令，则该新提示将删除现有的提示。  
  
 第一个规则表示有效的提示从以前打开的提示文件继承。 最后两个规则意味着更高版本中的搜索顺序发生的提示可以重写前面发生的提示。 例如，如果在包含源文件的目录中创建提示文件可以重写以前的任何提示。  
  
 描述如何收集提示，请参阅`Example`本主题中后面的部分。  
  
### <a name="syntax"></a>语法  
 创建和删除与创建和删除宏的预处理器指令相同的语法与提示。 事实上，分析系统使用 C + + 预处理器评估提示。 有关预处理器指令的详细信息，请参阅[#define 指令 （C/c + +）](../preprocessor/hash-define-directive-c-cpp.md)和[#undef 指令 （C/c + +）](../preprocessor/hash-undef-directive-c-cpp.md)。  
  
 唯一不同之语法元素`@<`， `@=`，和`@>`替换字符串。 这些是提示文件的特定的替换字符串，仅与使用*映射*宏。 映射是一组宏与数据、 函数或事件相关的其他数据、 函数或事件处理程序。 例如，`MFC`使用映射来创建[消息映射](../mfc/reference/message-maps-mfc.md)，和`ATL`使用映射来创建[对象映射](../atl/reference/object-map-macros.md)。 提示文件特定的替换字符串指示映射的起始、 中间，和结束的元素。 只有映射宏名称非常重要。 因此，每个替换字符串有意隐藏宏的实现。  
  
 提示使用以下语法。  
  
|语法|含义|  
|------------|-------------|  
|`#define`*提示名称**替换字符串*<br /><br /> `#define`*提示名称* `(` *参数*，...`)`*替换字符串*|定义新提示或重新定义现有提示的预处理器指令。 该指令之后，预处理器会将每个匹配项*提示名称*源的代码中*替换字符串*。<br /><br /> 第二种语法形式定义类似于函数的提示。 如果在源代码中出现类似于函数的提示，预处理器首先替换的每个匹配项*参数*中*替换字符串*替换源代码，然后替换对应的实参*提示名称*与*替换字符串*。|  
|`@<`|提示文件特定*替换字符串*，该值指示地图元素的一组的开头。|  
|`@=`|提示文件特定*替换字符串*，该值指示一个中间映射元素。 一个地图可以具有多个地图元素。|  
|`@>`|提示文件特定*替换字符串*，该值指示地图元素的集的末尾。|  
|`#undef`*提示名称*|删除现有提示预处理器指令。 提供的提示名*提示名称*标识符。|  
|`//`*注释*|中的单行注释。|  
|`/*`*comment*`*/`|中的多行注释。|  
  
## <a name="what-macros-require-a-hint"></a>什么宏需要提示？  
 某些类型的宏可能会干扰分析系统。 本部分介绍的宏，会导致问题，类型和可以创建用于解决该问题的提示的类型。  
  
### <a name="disruptive-macros"></a>中断宏  
 某些宏会导致错误解释源代码，该分析系统，但可以忽略不会影响到您的浏览体验。 例如，源代码批注语言 ([SAL](../c-runtime-library/sal-annotations.md)) 解析为帮助你的 c + + 特性查找编程 bug 的宏。 如果你想要忽略 SAL 批注，浏览代码时，你可能想要创建隐藏批注的提示文件。  
  
 以下源代码中的参数类型为`FormatWindowClassName()`函数是`PXSTR`，并且参数名称为`szBuffer`。 但是，分析的系统错误`_Pre_notnull_`和`_Post_z_`SAL 批注的参数类型或参数名称。  
  
 **源代码：**  
  
```  
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)  
```  
  
 **策略：** Null 定义  
  
 在此情况下策略是将视为其不存在的 SAL 批注。 若要执行此操作，指定的替换字符串为 null 的提示。 因此，分析系统将忽略的注释，和**类视图**浏览器不会显示它们。 （visual c + + 包括隐藏 SAL 批注的内置提示文件。）  
  
 **提示文件：**  
  
```  
#define _Pre_notnull_  
```  
  
### <a name="concealed-cc-language-elements"></a>隐匿的 C/c + + 语言元素  
 分析系统对源代码作出错误解释的典型原因是如果宏将隐藏 C/c + +[标点符号](../cpp/punctuators-cpp.md)或[关键字](../cpp/keywords-cpp.md)令牌。 也就是说，宏可能包含一半的成对的标点符号，如`<>`， `[]`， `{}`，和`()`。  
  
 在以下源代码中，`START_NAMESPACE`宏隐藏不成对的左大括号 (`{`)。  
  
 **源代码：**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
 **策略：**直接复制  
  
 如果宏的语义是至关重要的浏览体验，创建一个提示，等同于宏。 分析系统可解析为提示文件中定义的宏。  
  
 请注意，是否宏的源文件中包含其他宏，这些宏会解释仅当它们已处于的一套有效的提示。  
  
 **提示文件：**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
### <a name="maps"></a>映射  
 地图包含指定起始元素、 结束元素以及零个或多个中间元素的宏。 分析系统错误地解释地图，因为每个映射宏会隐藏 C/c + + 语言元素，并且完整的 C/c + + 语句的语法分布在许多单独的宏中。  
  
 下面的源代码定义`BEGIN_CATEGORY_MAP`， `IMPLEMENTED_CATEGORY`，和`END_CATEGORY_MAP`宏。  
  
 **源代码：**  
  
```  
#define BEGIN_CATEGORY_MAP(x)\  
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\  
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {  
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },  
#define END_CATEGORY_MAP()\  
   { _ATL_CATMAP_ENTRY_END, NULL } };\  
   return( pMap ); }  
```  
  
 **策略：**标识地图元素  
  
 指定提示的开始、 中间 （如果有） 和结束映射的元素。 使用特殊映射的替换字符串， `@<`， `@=`，和`@>`。 有关详细信息，请参阅`Syntax`本主题中的部分。  
  
 **提示文件：**  
  
```  
// Start of the map.  
#define BEGIN_CATEGORY_MAP(x) @<  
// Intermediate map element.  
#define IMPLEMENTED_CATEGORY( catid ) @=  
// Intermediate map element.  
#define REQUIRED_CATEGORY( catid ) @=  
// End of the map.  
#define END_CATEGORY_MAP() @>  
```  
  
### <a name="composite-macros"></a>复合宏  
 复合宏包含一个或多个混淆分析系统宏的类型。  
  
 下面的源代码包含`START_NAMESPACE`宏，指定命名空间范围的开始位置，和`BEGIN_CATEGORY_MAP`宏，它们分别指定地图的开始。  
  
 **源代码：**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
 **策略：**直接复制  
  
 为创建提示`START_NAMESPACE`和`BEGIN_CATEGORY_MAP`宏，然后创建提示`NSandMAP`有关的源代码前面所示相同的宏。 或者，如果复合宏包含仅发生中断性的宏和空白区域，你可以定义其替换字符串为 null 的定义的提示。  
  
 在此示例中，假定`START_NAMESPACE`已具有提示，如本主题中所述`Concealed C/C++ Language Elements`副标题。 和认为`BEGIN_CATEGORY_MAP`具有提示中所述`Maps`。  
  
 **提示文件：**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
### <a name="inconvenient-macros"></a>不合适的宏  
 可被分析的系统，解释某些宏，但难以阅读因宏太长或者过于复杂的源代码。 以便于阅读，你可以提供一个提示，简化了宏的显示。  
  
 **源代码：**  
  
```  
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)  
```  
  
 **策略：**简化  
  
 创建一个提示，显示简单的宏定义。  
  
 **提示文件：**  
  
```  
#define STDMETHOD(methodName) void* methodName  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何提示会累积从提示文件。 停止文件不在此示例中使用。  
  
 下图描绘了一些在 Visual c + + 项目中的物理目录。 提示文件位于`vcpackages`， `Debug`， `A1`，和`A2`目录。  
  
### <a name="hint-file-directories"></a>提示文件目录  
 ![常见和项目 &#45; 特定的提示文件目录。] (../ide/media/hintfile.png "HintFile")  
  
### <a name="directories-and-hint-file-contents"></a>目录和提示文件内容  
 以下列表显示提示文件，以及这些提示文件的内容包含此项目中的目录。 只有某些中的许多提示`vcpackages`列出目录提示文件。  
  
-   vcpackages  
  
    ```  
    // vcpackages (partial list)  
    #define _In_  
    #define _In_opt_  
    #define _In_z_  
    #define _In_opt_z_  
    #define _In_count_(size)  
    ```  
  
-   调试  
  
    ```  
    // Debug  
    #undef _In_  
    #define OBRACE {  
    #define CBRACE }  
    #define RAISE_EXCEPTION(x) throw (x)  
    #define START_NAMESPACE namespace MyProject {  
    #define END_NAMESPACE }  
    ```  
  
-   A1  
  
    ```  
    // A1  
    #define START_NAMESPACE namespace A1Namespace {  
    ```  
  
-   A2  
  
    ```  
    // A2  
    #undef OBRACE  
    #undef CBRACE  
    ```  
  
### <a name="effective-hints"></a>有效的提示  
 下表列出了此项目中的源文件的有效提示。  
  
-   源文件： A1_A2_B.cpp  
  
-   有效的提示：  
  
    ```  
    // vcpackages (partial list)  
    #define _In_opt_  
    #define _In_z_  
    #define _In_opt_z_  
    #define _In_count_(size)  
    // Debug...  
    #define RAISE_EXCEPTION(x) throw (x)  
    // A1  
    #define START_NAMESPACE namespace A1Namespace {   
    // ...Debug  
    #define END_NAMESPACE }  
    ```  
  
 以下说明适用于上面的列表。  
  
-   有效的提示是从`vcpackages`， `Debug`， `A1`，和`A2`目录。  
  
-   **#Undef**指令`Debug`提示文件删除`#define _In_`提示中`vcpackages`目录提示文件。  
  
-   中的提示文件`A1`目录重新定义了`START_NAMESPACE`。  
  
-   `#undef`提示中`A2`目录中删除的提示`OBRACE`和`CBRACE`中`Debug`目录提示文件。  
  
## <a name="see-also"></a>请参阅  
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)    
 [#define 指令 （C/c + +）](../preprocessor/hash-define-directive-c-cpp.md)   
 [#undef 指令 （C/c + +）](../preprocessor/hash-undef-directive-c-cpp.md)   
 [SAL 批注](../c-runtime-library/sal-annotations.md)   
 [消息映射](../mfc/reference/message-maps-mfc.md)   
 [消息映射宏](../atl/reference/message-map-macros-atl.md)   
 [对象映射宏](../atl/reference/object-map-macros.md)