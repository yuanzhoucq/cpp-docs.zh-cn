---
title: "Sample Container 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "container 类"
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Sample Container 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主题是作为标准 c + + 库中使用的容器无法正常工作示例的 Visual c + + 文档中。 有关详细信息，请参阅 [STL 容器](../standard-library/stl-containers.md)。  
  
 描述一个对象，用于控制类型的元素，通常变长序列 **Ty**。 序列存储在不同的方式，具体取决于实际的容器。  
  
 容器构造函数或成员函数可能会发现调用的构造函数的场合 **Ty**(**const Ty &**) 或函数 **Ty::operator =**(**const Ty &**)。 如果此类调用将引发异常，以维护其完整性，并重新引发它捕获任何异常，则有义务容器对象。 可以安全地交换，指派给、 擦除或销毁后它将引发这些异常中的一个容器对象。 一般情况下，但是，您无法否则预测控制由容器对象的序列的状态。  
  
 其他注意事项︰  
  
-   如果表达式 **~ Ty** 引发异常，容器对象的结果状态是不确定。  
  
-   如果该容器将存储一个分配器对象 *al*, ，和 *al* 引发到调用的结果以外的其他异常 *al***.allocate**, ，是不确定的结果状态的容器对象。  
  
-   如果该容器将存储的函数对象 *comp*, 来确定如何对受控的序列进行排序和 *comp* 引发的任何类型的异常，容器对象的结果状态是不确定。  
  
 下面几段中所述，定义的 STL 容器类满足一些附加要求。  
  
 容器模板类 [列表](../standard-library/list-class.md) 提供具有确定性，并很有用，即使是出现上面所述的异常的行为。 例如，如果在插入一个过程中引发异常或多个元素，该容器将保持不变并重新引发该异常。  
  
 有关 *所有* 定义 STL，如果在对下面的成员函数调用期间引发异常的容器类︰  
  
```  
<A NAME="vclrfcontainerinsert"></A>insert // single element inserted  
<A NAME="vclrfcontainerpushback"></A>push_back  
<A NAME="vclrfcontainerpushfront"></A>push_front  
```  
  
 容器将保持不变并重新引发该异常。  
  
 有关 *所有* 定义的 STL 容器类，在下面的成员函数调用的过程引发任何异常︰  
  
```  
<A NAME="vclrfcontainerpopback"></A>pop_back  
<A NAME="vclrfcontainerpopfront"></A>pop_front  
```  
  
 成员函数 [擦除](../standard-library/container-class-erase.md) （分配或复制构造） 的复制操作将引发异常时，才会引发异常。  
  
 此外，不会引发异常时复制一个成员函数返回一个迭代器。  
  
 成员函数 [交换](../standard-library/container-class-swap.md) 进行其他承诺 *所有* 定义的 STL 容器类︰  
  
-   成员函数引发了异常，仅当该容器将存储分配器对象 al，和 `al` 复制时会引发异常。  
  
-   引用、 指针和指定的被交换的受控序列的元素的迭代器仍将有效。  
  
 定义的 STL 容器类的对象分配和释放存储类型的存储对象通过它控制的序列 `Alloc`, ，这通常是一个模板参数。 此类分配器对象必须作为类的对象的外部接口相同 **分配器 \< Ty>**。 具体而言， `Alloc` 必须是相同的类型 **Alloc::rebind \< value_type >:: 其他**  
  
 有关 *所有* STL、 成员函数所定义的容器类 **Alloc get_allocator const;** 返回存储的分配器对象的副本。 请注意，存储的分配器对象是 *不* 分配容器对象时，复制。 所有构造函数初始化中存储的值 **分配器**, 到 `Alloc` 如果构造函数不包含任何分配器参数。  
  
 根据 c + + 标准，定义的 STL 容器类可以假设︰  
  
-   类的所有对象 `Alloc` 比较等。  
  
-   类型 **Alloc::const_pointer** 等同于 **const Ty \***。  
  
-   类型 **Alloc::const_reference** 等同于 **const Ty &**。  
  
-   类型 **Alloc::pointer** 等同于 **Ty \***。  
  
-   类型 **Alloc::reference** 等同于 **Ty &**。  
  
 但是，在此实现中，容器不使这种简化假设。 因此，它们正常运行的一些更远大的分配器对象︰  
  
-   类的所有对象 `Alloc` 不需要比较相等。 （您可以维护多个池的存储空间）。  
  
-   类型 **Alloc::const_pointer** 不需要相同 **const Ty \***。 （是 const 指针可以是一个类。）  
  
-   类型 **Alloc::pointer** 不需要相同 **Ty \***。 （一个指针，可以是一个类。）  
  
## <a name="requirements"></a>要求  
 **标头**: \< 示例容器>  
  
## <a name="see-also"></a>另请参阅  
 [\< 示例容器>](../standard-library/sample-container.md)

