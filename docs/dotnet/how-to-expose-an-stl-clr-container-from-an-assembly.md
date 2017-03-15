---
title: "如何：公开程序集中的 STL/CLR 容器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STL/CLR 容器 [STL/CLR]"
  - "STL/CLR, 跨程序集问题"
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：公开程序集中的 STL/CLR 容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL\/CLR 容器 \(如 `list` 和 `map` \) 实现为模板 ref 类。  由于 C\+\+ 模板在编译时实例化，具有相同的签名，但两个模板类在不同的程序集实际是不同的类型。  这意味着一个模板类不能跨程序集边界使用。  
  
 允许跨程序集共享成为可能。STL\/CLR，容器实现泛型 <xref:System.Collections.Generic.ICollection%601>接口。  使用此泛型接口，支持泛型，包括 C\+\+，C\# 和 Visual Basic 的所有语言，可以访问。STL\/CLR 容器  
  
 显示如何显示写入 C\+\+ 程序集的几个 STL\/CLR 容器的元素`StlClrClassLibrary`。  将显示两个程序集访问 `StlClrClassLibrary`。  第一个程序集。C\+\+ 和第二个用 C\# 编写。  
  
 如果两个程序集都用 C\+\+ 编写，使用其 `generic_container` typedef，可以访问容器的泛型接口。  例如，在中，如果已具有容器 `cliext::vector<int>`类型，然后其泛型接口是：`cliext::vector<int>::generic_container`。  同样，使用 `generic_iterator` typedef，如，您可以获取在泛型接口的迭代器：`cliext::vector<int>::generic_iterator`。  
  
 因为这些 C\+\+ typedef 中头文件声明，在其他语言编写的程序集无法使用它们。  因此，若要访问 `cliext::vector<int>` 的泛型接口用 C\# 或其他 .NET 语言，请使用 `System.Collections.Generic.ICollection<int>`。  若要循环内访问集合，请使用 `foreach` 循环。  
  
 下表列出了一个通用接口 STL\/CLR 容器实现：  
  
|STL\/CLR容器|Generic Interface — 泛型接口|  
|----------------|------------------------------|  
|deque\<T\>|ICollection\<T\>|  
|hash\_map\<K, V\>|IDictionary\<K, V\>|  
|hash\_multimap\<K, V\>|IDictionary\<K, V\>|  
|hash\_multiset\<T\>|ICollection\<T\>|  
|hash\_set\<T\>|ICollection\<T\>|  
|list\<T\>|ICollection\<T\>|  
|map\<K, V\>|IDictionary\<K, V\>|  
|multimap\<K, V\>|IDictionary\<K, V\>|  
|multiset\<T\>|ICollection\<T\>|  
|set\<T\>|ICollection\<T\>|  
|vector\<T\>|ICollection\<T\>|  
  
> [!NOTE]
>  由于 `queue`、`priority_queue`和 `stack` 容器不支持迭代器，这些没有实现泛型接口，不能跨程序集的访问。  
  
## 示例 1  
  
### 说明  
 在此示例中，我们要声明包含私有 STL\/CLR 成员数据 .\) 的 C\+\+ 类。  然后我们声明公共方法对类的其他集合的访问权限。  我们以在两种不同的情况下，一 C\+\+ 客户端和一个其他 .NET 客户端的。  
  
### 代码  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## 示例 2  
  
### 说明  
 在此示例中，我们要实现。示例声明类。  为了使客户可以使用此类库，我们使用清单工具 **mt.exe** 嵌入清单文件调入 DLL。  有关详细信息，请参见代码注释。  
  
 有关清单工具和并行程序集的更多信息，请参见 [生成 C\/C\+\+ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。  
  
### 代码  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## 示例 3  
  
### 说明  
 在此示例中，我们要创建您在示例 1 和 2. 使用创建的类库中。. C\+\+ 客户。  此客户使用 STL\/CLR 容器的 `generic_container` typedef 循环访问容器并显示其内容。  
  
### 代码  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### Output  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## 示例 4  
  
### 说明  
 在此示例中，我们要创建您在示例 1 和 2. 使用创建的类库中。. C\# 客户。  此客户使用 STL\/CLR 容器的  <xref:System.Collections.Generic.ICollection%601>方法循环访问容器并显示其内容。  
  
### 代码  
  
```  
// CsConsoleApp.cs  
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll  
  
using System;  
using System.Collections.Generic;  
using StlClrClassLibrary;  
using cliext;  
  
namespace CsConsoleApp  
{  
    class Program  
    {  
        static int Main(string[] args)  
        {  
            StlClrClass theClass = new StlClrClass();  
  
            Console.WriteLine("cliext::deque contents:");  
            ICollection<char> iCollChar = theClass.GetDequeCs();  
            foreach (char c in iCollChar)  
            {  
                Console.WriteLine(c);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::list contents:");  
            ICollection<float> iCollFloat = theClass.GetListCs();  
            foreach (float f in iCollFloat)  
            {  
                Console.WriteLine(f);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::map contents:");  
            IDictionary<int, string> iDict = theClass.GetMapCs();  
            foreach (KeyValuePair<int, string> kvp in iDict)  
            {  
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::set contents:");  
            ICollection<double> iCollDouble = theClass.GetSetCs();  
            foreach (double d in iCollDouble)  
            {  
                Console.WriteLine(d);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::vector contents:");  
            ICollection<int> iCollInt = theClass.GetVectorCs();  
            foreach (int i in iCollInt)  
            {  
                Console.WriteLine(i);  
            }  
            Console.WriteLine();  
  
            return 0;  
        }  
    }  
}  
```  
  
### Output  
  
```  
cliext::deque contents:  
a  
b  
  
cliext::list contents:  
3.14159  
2.71828  
  
cliext::map contents:  
0 Hello  
1 World  
  
cliext::set contents:  
2.71828  
3.14159  
  
cliext::vector contents:  
10  
20  
```  
  
## 请参阅  
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)