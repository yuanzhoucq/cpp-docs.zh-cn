---
title: "random_device 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "random_device"
  - "random/std::tr1::random_device"
  - "tr1.random_device"
  - "std::tr1::random_device"
  - "std.tr1.random_device"
  - "tr1::random_device"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "random_device 类"
  - "random_device 类 [TR1]"
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# random_device 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从外部设备生成随机序列。  
  
## 语法  
  
```  
class random_device { public:     typedef unsigned int result_type;     // cosntructor     explicit random_device(const std::string& token = "");     // properties     static result_type min();     static result_type max();     double entropy() const;     // generate     result_type operator()();     // no-copy functions     random_device(const random_device&) = delete;     void operator=(const random_device&) = delete; };  
```  
  
## Members  
  
|||  
|-|-|  
|[random\_device::random\_device](../Topic/random_device::random_device.md)|[random\_device::entropy](../Topic/random_device::entropy.md)|  
|[random\_device::operator\(\)](../Topic/random_device::operator\(\).md)||  
  
## 备注  
 该类描述了随机数的源，按 ISO C\+\+ 标准，允许但不要求它为非确定性的或进行安全加密。  在 Visual Studio 实现中，产生的值是非确定性的且进行了安全加密的，但是比从引擎和引擎适配器中创建的生成器运行得更慢（例如，对于大多数应用程序而言，会选择高质量且快速的引擎 [mersenne\_twister\_engine](../standard-library/mersenne-twister-engine-class.md)）。  
  
 `random_device` 结果均匀分布在闭合范围 \[`0, 2`<sup>32</sup>\) 中。  
  
 无法保证 `random_device` 产生非阻止调用。  
  
 通常，`random_device` 用于设定使用引擎或引擎适配器创建的其他生成器的种子。  有关详细信息，请参阅[\<random\>](../standard-library/random.md)。  
  
## 示例  
 以下代码演示了此类的基本功能和示例结果。  由于 `random_device` 的非确定性本质，**输出**部分中所示的随机值将不会与你的结果相匹配。  这是正常情况，也是预期的情况。  
  
```cpp  
// random_device_engine.cpp   
// cl.exe /W4 /nologo /EHsc /MTd   
#include <random>   
#include <iostream>   
using namespace std;  
  
int main()   
{   
    random_device gen;   
  
    cout << "entropy == " << gen.entropy() << endl;   
    cout << "min == " << gen.min() << endl;   
    cout << "max == " << gen.max() << endl;   
  
    cout << "a random value == " << gen() << endl;   
    cout << "a random value == " << gen() << endl;   
    cout << "a random value == " << gen() << endl;   
}  
```  
  
 **输出：**  
  
  **平均信息量 \=\= 32**  
**最小 \=\= 0**  
**最大 \=\= 4294967295**  
**10 个随机值：**  
**4183829181**  
**1454391608**  
**1176278697**  
**2468830096**  
**3959347222**  
**1803123400**  
**1339590545**  
**1304896877**  
**604088490**  
**2293276253** 这是简化的示例，不代表此生成器的一般使用案例。  有关更具代表性的代码示例，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)