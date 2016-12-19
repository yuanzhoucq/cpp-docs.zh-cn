---
title: "提示文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cpp.hint"
  - "vc.hint.file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "停止文件"
  - "cpp.hint"
  - "提示文件"
  - "cpp.stop"
  - "类视图, 提示文件"
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 提示文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一个 *提示文件* 可帮助 Visual Studio 集成的开发环境 (IDE) 解释 Visual c + + 标识符，例如，函数和宏的名称。 当您打开一个 Visual c + + 项目，IDE 的 *分析系统* 分析项目中每个源文件中的代码，并收集有关每个标识符的信息。 然后，IDE 使用该信息支持的功能，如 **类视图** 浏览器和 **导航栏**。  
  
 分析系统中引入的 [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)], ，了解 C/c + + 语法，但可以曲解包含宏的语句。 如果宏使要编写语法不正确的源代码会错误地解释该语句。 该语句可能会变得在语法上正确编译的源代码和预处理程序替换时 [宏标识符](../preprocessor/hash-define-directive-c-cpp.md) 利用自己的定义。 分析系统工作而无需生成项目，因为它使用提示文件来解释宏。 因此，如浏览功能 **类视图** 立即可用。  
  
 提示文件包含用户可自定义 *提示*, ，其中具有相同的语法与 C/c + + 宏定义。 Visual c + + 包括内置的提示文件，它足以满足大多数项目，但您可以创建您自己的提示文件来改进 Visual Studio 处理标识符的方式。  
  
> [!IMPORTANT]
>  如果您修改或添加提示文件，则必须删除.sdf 文件和/或 VC.db 文件中所作的更改才会生效的解决方案中。  
  
## <a name="scenario"></a>方案  
 假定下面的代码是在您检查使用的源文件中 **类视图** 浏览器。  `STDMETHOD` 宏声明一个名为方法 `myMethod` ，采用一个参数并返回一个指向 **HRESULT**。  
  
```  
// Source code file.  
STDMETHOD(myMethod)(int parameter1);  
```  
  
 以下宏定义位于单独的头文件。  
  
```  
// Header file.  
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)  
#define STDMETHODCALLTYPE __stdcall  
#define HRESULT void*  
```  
  
 分析系统无法解释的源代码，因为似乎声明，这是一个名为 STDMETHOD 函数和该声明的语法不正确，因为它具有两个形参列表。 分析系统不会打开该标头文件，找到的定义 `STDMETHOD`, ，`STDMETHODCALLTYPE`, ，和 `HRESULT` 宏。 由于分析系统无法解释 `STDMETHOD` 宏，它将忽略整个语句并继续分析。  
  
 分析系统不使用头文件，因为您的项目可能依赖于一个或多个重要的头文件。 如果任何标头文件发生更改，可能需要重新检查的所有标头文件在项目中，从而降低 IDE 的性能分析系统。 相反，分析系统使用提示，以指定如何处理 `STDMETHOD`, ，`STDMETHODCALLTYPE`, ，和 `HRESULT` 宏。  
  
 如何知道需要提示？ 如果您需要一个提示，哪种类型应您创建和？ 一次登录，则需要提示是如果视图中的标识符 **类视图** 不一致的视图中， **编辑器**。 例如， **类视图** 可能不会显示您知道的类成员存在，或该成员的名称不正确。 有关解决常见的问题的提示类型的详细信息，请参阅什么宏需要提示？在本主题后面的部分。  
  
## <a name="architecture"></a>体系结构  
 提示文件属于物理目录，不属于的逻辑目录中所示 **解决方案资源管理器**。 不需要将提示文件添加到你的项目的提示文件产生任何影响。 分析系统提示文件只有当使用分析源文件。  
  
 每个提示文件被命名为 **cpp.hint**。 因此，许多目录可以包含提示文件，但只能有一个提示文件可在特定的目录中出现。  
  
 您的项目可能会影响由零个或多个提示文件。 如果没有提示的文件，分析系统将使用错误恢复技术忽略无法解密的源代码。 否则，分析系统使用以下策略来查找和收集提示。  
  
### <a name="search-order"></a>搜索顺序  
 分析系统按以下顺序搜索提示文件的目录。  
  
-   Visual c + + 中包含的安装包的目录 (**vcpackages**)。 此目录包含一个内置提示文件，如描述中频繁使用的系统文件的符号 **windows.h**。 因此，您的项目将自动继承大部分其所需的提示。  
  
-   从源代码文件的根目录到包含自身的源文件的目录的路径。 典型的 Visual c + + 项目中，在根目录下包含的解决方案或项目文件。  
  
     此规则的例外是如果 *停止文件* 到源代码文件的路径中。 停止文件提供了更多控制权的搜索顺序，名为任何文件 **cpp.stop**。 而不是从根目录开始，分析系统将从包含停止文件到包含源文件的目录的目录搜索。 在典型项目中，您不需要停止文件。  
  
### <a name="hint-gathering"></a>提示收集  
 提示文件包含零个或多 *提示*。 定义一个提示或将其删除一样 C/c + + 宏。 也就是说， `#define` 预处理器指令创建或重新定义了一个提示，并且 `#undef` 指令删除提示。  
  
 分析系统将每个提示文件打开前面所述的搜索顺序，将每个文件的提示累积到一组 *有效提示*, ，然后使用有效的提示来解释您的代码中的标识符。  
  
 分析系统使用以下规则累积提示。  
  
-   如果新提示指定尚未定义一个名称，新的提示会将名称添加到有效的提示。  
  
-   如果新提示指定已定义的名称，则新提示将重新定义现有的提示。  
  
-   如果新的提示是 `#undef` 指令，指定现有的有效提示、 新的提示将删除现有的提示。  
  
 第一条规则表示有效提示从以前打开的提示文件继承。 最后两个规则意味着更高版本中的搜索顺序出现的提示可以重写前面发生的提示。 如果在包含源文件的目录中创建提示文件，例如，可以重写以前的任何提示。  
  
 描述如何收集提示，请参阅 `Example` 在本主题后面的部分。  
  
### <a name="syntax"></a>语法  
 创建和删除了与创建和删除宏的预处理器指令相同的语法提示。 实际上，分析系统使用 C + + 预处理器评估提示。 预处理器指令的详细信息，请参阅 [#define 指令 （C/c + +）](../preprocessor/hash-define-directive-c-cpp.md) 和 [#undef 指令 （C/c + +）](../preprocessor/hash-undef-directive-c-cpp.md)。  
  
 唯一不同之语法元素是 `@<`, ，`@=`, ，和 `@>` 替换字符串。 这些是仅与使用的提示文件特定的替换字符串 *映射* 宏。 映射是一组与其他数据、 函数或事件处理程序相关的数据、 函数或事件的宏。 例如， `MFC` 使用映射来创建 [消息映射](../mfc/reference/message-maps-mfc.md), ，和 `ATL` 使用映射来创建 [对象映射](../atl/reference/object-map-macros.md)。 提示文件特定的替换字符串指示映射中的开始、 中间，和结束元素。 只有名称的映射宏很重要。 因此，每个替换字符串有意隐藏宏的实现。  
  
 提示使用以下语法。  
  
|语法|含义|  
|------------|-------------|  
|`#define` *提示名称* *替换字符串*<br /><br /> `#define` *提示名称* `(` *参数*, ，...`)`*替换字符串*|定义新提示或重新定义现有的提示的预处理器指令。 该指令之后，预处理器会将每个匹配项 *提示名称* 在源代码与 *替换字符串*。<br /><br /> 第二种语法形式定义的类似函数的提示。 如果函数类似于提示出现在源代码中，预处理器会首先将出现的每个 *参数* 中 *替换字符串* 替换在源代码中，和替换为对应的实参 *提示名称* 与 *替换字符串*。|  
|`@<`|提示文件特定于 *替换字符串* ，该值指示的地图元素的一组的开头。|  
|`@=`|提示文件特定于 *替换字符串* ，该值指示一个中间映射元素。 一个地图可以具有多个地图元素。|  
|`@>`|提示文件特定于 *替换字符串* ，该值指示一组地图元素的末尾。|  
|`#undef` *提示名称*|预处理器指令，用于删除现有的提示。 提供的提示名称 *提示名称* 标识符。|  
|`//` *注释*|单行注释。|  
|`/*` *注释* `*/`|多行注释。|  
  
## <a name="what-macros-require-a-hint"></a>什么宏需要提示？  
 某些类型的宏可能会干扰分析系统。 本部分介绍类型的宏可能会导致出现了问题，并可以创建用于解决该问题的提示的类型。  
  
### <a name="disruptive-macros"></a>中断宏  
 一些宏，宏会导致错误地解释源代码，则分析系统，但可以忽略不会影响到您的浏览体验。 例如，源代码批注语言 ([SAL](../c-runtime-library/sal-annotations.md)) 宏可以解析为帮助您的 c + + 特性查找编程 bug。 如果您想要忽略 SAL 注释浏览代码时，您可能想要创建隐藏注释的提示文件。  
  
 在下面的源代码中的参数类型为 `FormatWindowClassName()` 函数是 `PXSTR`, ，并且参数名为 `szBuffer`。 但是，分析系统会 `_Pre_notnull_` 和 `_Post_z_` SAL 批注的参数类型或参数名称。  
  
 **源代码︰**  
  
```  
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)  
```  
  
 **策略︰** 定义，则为 Null  
  
 在此情况下策略是将 SAL 注释，就像它们不存在。 若要执行此操作，指定替换字符串为 null 的提示。 因此，分析系统将忽略注释中，与 **类视图** 浏览器不显示它们。 （visual c + + 包括隐藏 SAL 批注的内置提示文件。）  
  
 **提示文件︰**  
  
```  
#define _Pre_notnull_  
```  
  
### <a name="concealed-cc-language-elements"></a>隐匿的 C/c + + 语言元素  
 分析系统对源代码作出错误解释一种常见原因是如果宏会隐藏 C/c + + [标点符号](../cpp/punctuators-cpp.md) 或 [关键字](../cpp/keywords-cpp.md) 令牌。 也就是说，宏可能包含一半一对标点符号，如 `<>`, ，`[]`, ，`{}`, ，和 `()`。  
  
 在下面的源代码， `START_NAMESPACE` 宏将隐藏不成对的左大括号 (`{`)。  
  
 **源代码︰**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
 **策略︰** 直接复制  
  
 如果宏的语义是至关重要的浏览体验，创建一个等同于宏的提示。 分析系统将解析为提示文件中定义的宏。  
  
 请注意，是否宏的源文件中包含其他宏，这些宏会解释已经有效提示集中时才。  
  
 **提示文件︰**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
### <a name="maps"></a>映射  
 映射包含的指定起始元素、 结束元素以及零个或多个中间元素的宏。 分析系统错误地解释地图，因为每个映射宏会隐藏 C/c + + 语言元素，并且是完整的 C/c + + 语句的语法分布在许多单独的宏中。  
  
 下面的源代码定义 `BEGIN_CATEGORY_MAP`, ，`IMPLEMENTED_CATEGORY`, ，和 `END_CATEGORY_MAP` 宏。  
  
 **源代码︰**  
  
```  
#define BEGIN_CATEGORY_MAP(x)\  
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\  
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {  
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },  
#define END_CATEGORY_MAP()\  
   { _ATL_CATMAP_ENTRY_END, NULL } };\  
   return( pMap ); }  
```  
  
 **策略︰** 确定地图元素  
  
 指定提示的开始、 中间 （如果有） 和结束映射的元素。 使用特殊映射替换字符串， `@<`, ，`@=`, ，和 `@>`。 有关详细信息，请参阅 `Syntax` 本主题中的部分。  
  
 **提示文件︰**  
  
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
  
### <a name="composite-macros"></a>组合宏  
 组合宏包含一个或多个扰乱分析系统宏的类型。  
  
 下面的源代码包含 `START_NAMESPACE` 宏，指定命名空间范围的开始位置，并且 `BEGIN_CATEGORY_MAP` 宏，它们分别指定一个映射中的起始位置。  
  
 **源代码︰**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
 **策略︰** 直接复制  
  
 为创建提示 `START_NAMESPACE` 和 `BEGIN_CATEGORY_MAP` 宏，然后创建一个提示 `NSandMAP` 前面所示的源代码的相同的宏。 或者，如果复合宏组成只中断宏和空白区域，您可以定义替换字符串为 null 定义的提示。  
  
 在此示例中，假定 `START_NAMESPACE` 已经有一个提示，在本主题中所述 `Concealed C/C++ Language Elements` 副标题。 并假定 `BEGIN_CATEGORY_MAP` 具有提示中所述 `Maps`。  
  
 **提示文件︰**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
### <a name="inconvenient-macros"></a>不合适的宏  
 分析系统能解释一些宏，但源代码很难读取，因为该宏是长或太复杂。 为了便于阅读，您可以提供一个提示，简化了该宏的显示。  
  
 **源代码︰**  
  
```  
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)  
```  
  
 **策略︰** 简化  
  
 创建一个提示，显示简单的宏定义。  
  
 **提示文件︰**  
  
```  
#define STDMETHOD(methodName) void* methodName  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何提示会累积从提示文件。 在此示例不使用 stop 文件。  
  
 下图描绘了一些在 Visual c + + 项目中的物理目录。 提示文件位于 `vcpackages`, ，`Debug`, ，`A1`, ，和 `A2` 目录。  
  
### <a name="hint-file-directories"></a>提示文件目录  
 ![常见项目 （&) #45; 特定的提示文件目录。](../ide/media/hintfile.png "HintFile")  
  
### <a name="directories-and-hint-file-contents"></a>目录和提示文件内容  
 以下列表显示在此项目包含提示文件，这些提示文件的内容的目录。 只有部分中的多个提示 `vcpackages` 列出目录提示文件。  
  
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
  
### <a name="effective-hints"></a>有效提示  
 下表列出了此项目中的源文件的有效提示。  
  
-   源文件︰ A1_A2_B.cpp  
  
-   有效的提示︰  
  
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
  
 下列注意事项适用于前面的列表。  
  
-   有效的提示是从 `vcpackages`, ，`Debug`, ，`A1`, ，和 `A2` 目录。  
  
-    **#Undef** 指令中 `Debug` 提示文件删除 `#define _In_` 提示在 `vcpackages` 目录提示文件。  
  
-   中的提示文件 `A1` 目录重新定义 `START_NAMESPACE`。  
  
-    `#undef` 提示在 `A2` 目录中删除的提示 `OBRACE` 和 `CBRACE` 中 `Debug` 目录提示文件。  
  
## <a name="see-also"></a>另请参阅  
 [为 Visual c + + 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [创建和控制环境窗口](../Topic/Creating%20and%20Controlling%20Environment%20Windows.md)   
 [#define 指令 （C/c + +）](../preprocessor/hash-define-directive-c-cpp.md)   
 [#undef 指令 （C/c + +）](../preprocessor/hash-undef-directive-c-cpp.md)   
 [SAL 批注](../c-runtime-library/sal-annotations.md)   
 [消息映射](../mfc/reference/message-maps-mfc.md)   
 [消息映射宏](../atl/reference/message-map-macros-atl.md)   
 [对象映射宏](../atl/reference/object-map-macros.md)