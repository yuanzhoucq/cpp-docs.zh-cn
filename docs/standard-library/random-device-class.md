---
title: "random_device 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
- random/std::random_device::entropy
- random/std::random_device::operator()
dev_langs:
- C++
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: f4256ac0a58f3cc21322ff84565838d36174a00a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="randomdevice-class"></a>random_device 类
从外部设备生成随机序列。  
  
## <a name="syntax"></a>语法  
  
```
class random_device {  
public:  
   typedef unsigned int result_type;  
   
   // constructor 
   explicit random_device(const std::string& token = "");
   
   // properties 
   static result_type min();
   static result_type max();
   double entropy() const;
   
   // generate 
   result_type operator()();

   // no-copy functions 
   random_device(const random_device&) = delete;  
   void operator=(const random_device&) = delete;  
   };  
```  

## <a name="members"></a>成员  
  
|||  
|-|-|  
|[random_device](#random_device)|[平均信息量](#entropy)|  
|[random_device::operator()](#op_call)||  
  
## <a name="remarks"></a>备注  
该类描述了随机数的源，按 ISO C++ 标准，允许但不要求它为非确定性的或进行安全加密。 在 Visual Studio 实现中，产生的值是非确定性的且进行了安全加密，但是比从引擎和引擎适配器中创建的生成器运行得更慢（例如，对于大多数应用程序而言，会选择高质量且快速的引擎 [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md)）。  
  
`random_device` 结果均匀分布在闭合范围 [`0, 2`<sup>32</sup>) 中。  
  
无法保证 `random_device` 产生非阻止调用。  
  
通常，`random_device` 用于设定使用引擎或引擎适配器创建的其他生成器的种子。 有关详细信息，请参见 [\<random>](../standard-library/random.md)。  
  
## <a name="example"></a>示例  
以下代码演示了此类的基本功能和示例结果。 由于 `random_device` 的非确定性本质，**输出**部分中所示的随机值将不会与你的结果相匹配。 这是正常情况，也是预期的情况。  
  
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
  
```Output  
entropy == 32
min == 0
max == 4294967295
a random value == 2378414971
a random value == 3633694716
a random value == 213725214
```  
  
这是简化的示例，不代表此生成器的一般使用案例。 有关更具代表性的代码示例，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<random>  
  
 **命名空间：** std  
  
##  <a name="random_device"></a>random_device::random_device  
构造生成器。  
  
```  
random_device(const std::string& = "");
```  
  
### <a name="remarks"></a>备注  
构造函数将按需初始化生成器，从而忽略字符串参数。 如果无法初始化 `random_device`，将引发派生自 [exception](../standard-library/exception-class.md) 的实现定义的类型的值。  
  
##  <a name="entropy"></a>random_device::entropy  
估计源的随机性。  
  
```  
double entropy() const noexcept;  
```  
  
### <a name="remarks"></a>备注  
成员函数将返回源的随机性的估计（以位为单位）。  
  
##  <a name="op_call"></a>random_device::operator()  
返回随机值。  
  
```  
result_type operator()();
```  
  
### <a name="remarks"></a>备注  
返回由成员函数 `min()` 和 `max()` 确定的在闭区间 [`min, max`] 中均匀分布的值。 如果无法获取随机数，将引发派生自 [exception](../standard-library/exception-class.md) 的实现定义的类型的值。  
  
## <a name="see-also"></a>另请参阅  
[\<random>](../standard-library/random.md)


