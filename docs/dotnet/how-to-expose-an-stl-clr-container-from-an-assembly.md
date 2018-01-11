---
title: "如何： 公开从程序集中的 STL/CLR 容器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84505edf0877a5ae20d28906dde7f4c709574034
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>如何：公开程序集中的 STL/CLR 容器
STL/CLR 容器，如`list`和`map`作为模板 ref 类实现。 因为在编译时实例化 c + + 模板，具有相同的签名，但位于不同的程序集的两个模板类将是实际不同类型。 这意味着不能跨程序集边界用于模板类。  
  
 若要使跨程序集共享成为可能，STL/CLR 容器实现泛型接口<xref:System.Collections.Generic.ICollection%601>。 通过使用此泛型接口，支持泛型，包括 c + +、 C# 和 Visual Basic 中的所有语言都可以都访问 STL/CLR 容器。  
  
 本主题演示如何编写在 c + + 程序集中名为的几个 STL/CLR 容器元素显示`StlClrClassLibrary`。 我们显示两个程序集访问`StlClrClassLibrary`。 第一个程序集编写 c + + 和 C# 中的第二个。  
  
 如果两个程序集编写 c + + 中，你可以通过访问容器的泛型接口其`generic_container`typedef。 例如，如果你有类型的容器`cliext::vector<int>`，则其泛型接口是： `cliext::vector<int>::generic_container`。 同样，你可以获取迭代器的泛型接口使用`generic_iterator`typedef，如下所示： `cliext::vector<int>::generic_iterator`。  
  
 由于这些 typedef 声明在 c + + 标头文件中，用其他语言编写的程序集无法使用它们。 因此，若要访问的泛型接口`cliext::vector<int>`在 C# 或任何其他.NET 语言，使用`System.Collections.Generic.ICollection<int>`。 若要循环访问此集合，使用`foreach`循环。  
  
 下表列出了每个 STL/CLR 容器实现的泛型接口：  
  
|STL/CLR 容器|泛型接口|  
|------------------------|-----------------------|  
|e q u e < T\>|ICollection < T\>|  
|hash_map < K，V >|IDictionary < K，V >|  
|hash_multimap < K，V >|IDictionary < K，V >|  
|hash_multiset < T\>|ICollection < T\>|  
|hash_set < T\>|ICollection < T\>|  
|列表 < T\>|ICollection < T\>|  
|映射 < K，V >|IDictionary < K，V >|  
|多重映射 < K，V >|IDictionary < K，V >|  
|multiset < T\>|ICollection < T\>|  
|设置 < T\>|ICollection < T\>|  
|向量 < T\>|ICollection < T\>|  
  
> [!NOTE]
>  因为`queue`， `priority_queue`，和`stack`容器不支持迭代器，它们不实现泛型接口，并且不能访问的跨程序集。  
  
## <a name="example-1"></a>示例 1  
  
### <a name="description"></a>描述  
 在此示例中，我们可以声明包含私有 STL/CLR 成员数据的 c + + 类。 我们然后声明用于授予访问权限的专用集合类的公共方法。 我们执行操作在两种不同方式、 c + + 客户端和其他.NET 客户端。  
  
### <a name="code"></a>代码  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="example-2"></a>示例 2  
  
### <a name="description"></a>描述  
 在此示例中，我们实现示例 1 中声明的类。 为了使客户端使用此类库，我们将使用该清单工具**mt.exe**要嵌入到该 DLL 的清单文件。 有关详细信息，请参阅代码注释。  
  
 清单工具和通过并行程序集的详细信息，请参阅[生成 C/c + + 独立应用程序和通过并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。  
  
### <a name="code"></a>代码  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example-3"></a>示例 3  
  
### <a name="description"></a>描述  
 在此示例中，我们创建了使用在示例 1 和 2 中创建的类库的 c + + 客户端。 此客户端使用`generic_container`STL/CLR 容器循环访问容器以及以显示其内容的 typedef。  
  
### <a name="code"></a>代码  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="output"></a>输出  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## <a name="example-4"></a>示例 4  
  
### <a name="description"></a>描述  
 在此示例中，我们将创建一个 C# 客户端使用在示例 1 和 2 中创建的类库。 此客户端使用<xref:System.Collections.Generic.ICollection%601>STL/CLR 容器循环访问容器以及以显示其内容的方法。  
  
### <a name="code"></a>代码  
  
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
  
### <a name="output"></a>输出  
  
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
  
## <a name="see-also"></a>请参阅  
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)