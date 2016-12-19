---
title: "如何：在 C++/CLI 中使用跟踪引用 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLR 类型, 按引用传递"
ms.assetid: d91e471c-34ff-4786-9e0d-c6db0494b946
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 C++/CLI 中使用跟踪引用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文演示如何通过引用使用跟踪引用 \(%\)。[!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 会将公共语言运行时 \(CLR\) \(CLR\) 类型。  
  
## 将 CLR 类型引用  
 下面的示例显示如何通过引用传递使用 CLR 类型的跟踪引用。  
  
```  
// tracking_reference_handles.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct City {  
private:  
   Int16 zip_;  
  
public:  
   City (int zip) : zip_(zip) {};  
   property Int16 zip {  
      Int16 get(void) {  
         return zip_;  
      }   // get  
   }   // property  
};  
  
void passByRef (City ^% myCity) {  
   // cast required so this pointer in City struct is "const City"  
   if (myCity->zip == 20100)  
      Console::WriteLine("zip == 20100");  
   else  
      Console::WriteLine("zip != 20100");  
}  
  
ref class G {  
public:  
   int i;  
};  
  
void Test(int % i) {  
   i++;  
}  
  
int main() {  
   G ^ g1 = gcnew G;  
   G ^% g2 = g1;  
   g1 -> i = 12;  
  
   Test(g2->i);   // g2->i will be changed in Test2()  
  
   City ^ Milano = gcnew City(20100);  
   passByRef(Milano);  
}  
```  
  
 **Output**  
  
  **邮政编码 \=\= 20100** 下一个示例演示将跟踪引用返回的地址与 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)的，并显示如何通过修改跟踪引用和访问数据。  
  
```  
// tracking_reference_data.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class R {  
public:  
   R(int i) : m_i(i) {  
      Console::WriteLine("ctor: R(int)");  
   }  
  
   int m_i;  
};  
  
class N {  
public:  
   N(int i) : m_i (i) {  
      Console::WriteLine("ctor: N(int i)");  
   }  
  
   int m_i;  
};  
  
int main() {  
   R ^hr = gcnew R('r');  
   R ^%thr = hr;  
   N n('n');  
   N %tn = n;  
  
   // Declare interior pointers  
   interior_ptr<R^> iphr = &thr;  
   interior_ptr<N> ipn = &tn;  
  
   // Modify data through interior pointer  
   (*iphr)->m_i = 1;   // (*iphr)->m_i == thr->m_i  
   ipn->m_i = 4;   // ipn->m_i == tn.m_i  
  
   ++thr-> m_i;   // hr->m_i == thr->m_i  
   ++tn. m_i;   // n.m_i == tn.m_i  
  
   ++hr-> m_i;   // (*iphr)->m_i == hr->m_i  
   ++n. m_i;   // ipn->m_i == n.m_i  
}  
```  
  
 **Output**  
  
  **ctor:R \(int\)**  
**ctor:N \(int i\)**   
## 跟踪引用和内部指针  
 下面的代码示例演示一，可以转换。跟踪引用和内部指针之间。  
  
```  
// tracking_reference_interior_ptr.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class R {  
public:  
   R(int i) : m_i(i) {  
      Console::WriteLine("ctor: R(int)");  
   }  
  
   int m_i;  
};  
  
class N {  
public:  
   N(int i) : m_i(i) {  
      Console::WriteLine("ctor: N(int i)");  
   }  
  
   int m_i;  
};  
  
int main() {  
   R ^hr = gcnew R('r');  
   N n('n');  
  
   R ^%thr = hr;  
   N %tn = n;  
  
   // Declare interior pointers  
   interior_ptr<R^> iphr = &hr;  
   interior_ptr<N> ipn = &n;  
  
   // Modify data through interior pointer  
   (*iphr)->m_i = 1;   // (*iphr)-> m_i == thr->m_i  
   ipn->m_i = 4;   // ipn->m_i == tn.m_i  
  
   ++thr->m_i;   // hr->m_i == thr->m_i  
   ++tn.m_i;   // n.m_i == tn.m_i  
  
   ++hr->m_i;   // (*iphr)->m_i == hr->m_i  
   ++n.m_i;   // ipn->m_i == n.m_i  
}  
```  
  
 **Output**  
  
  **ctor:R \(int\)**  
**ctor:N \(int i\)**   
## 跟踪引用和值类型  
 本示例遍历指向值类型的跟踪引用显示简单的、装箱：  
  
```  
// tracking_reference_valuetypes_1.cpp// compile with: /clrusing namespace System;int main() {   int i = 10;   int % j = i;   Object ^ o = j;   // j is implicitly boxed and assigned to o}  
```  
  
 下面的示例演示，可以跟踪引用和本机引用为值类型。  
  
```  
// tracking_reference_valuetypes_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   int i = 10;  
   int & j = i;  
   int % k = j;  
   i++;   // 11  
   j++;   // 12  
   k++;   // 13  
   Console::WriteLine(i);  
   Console::WriteLine(j);  
   Console::WriteLine(k);  
}  
```  
  
 **Output**  
  
  **13**  
**13**  
**13** 下面的示例表示，则可以将值类型和本机类型。使用跟踪引用。  
  
```  
// tracking_reference_valuetypes_3.cpp  
// compile with: /clr  
value struct G {  
   int i;  
};  
  
struct H {  
   int i;  
};  
  
int main() {  
   G g;  
   G % v = g;  
   v.i = 4;  
   System::Console::WriteLine(v.i);  
   System::Console::WriteLine(g.i);  
  
   H h;  
   H % w = h;  
   w.i = 5;  
   System::Console::WriteLine(w.i);  
   System::Console::WriteLine(h.i);  
}  
```  
  
 **Output**  
  
  **4**  
**4**  
**5**  
**5** 此示例演示，可以绑定到值类型的跟踪引用在垃圾回收堆：  
  
```  
// tracking_reference_valuetypes_4.cpp  
// compile with: /clr  
using namespace System;  
value struct V {  
   int i;  
};  
  
void Test(V^ hV) {   // hv boxes another copy of original V on GC heap  
   Console::WriteLine("Boxed new copy V: {0}", hV->i);  
}  
  
int main() {  
   V v;   // V on the stack  
   v.i = 1;  
   V ^hV1 = v;   // v is boxed and assigned to hV1  
   v.i = 2;  
   V % trV = *hV1;   // trV is bound to boxed v, the v on the gc heap.  
   Console::WriteLine("Original V: {0}, Tracking reference to boxed V: {1}", v.i, trV.i);  
   V ^hV2 = trV;   // hv2 boxes another copy of boxed v on the GC heap  
   hV2->i = 3;  
   Console::WriteLine("Tracking reference to boxed V: {0}", hV2->i);  
   Test(trV);  
   v.i = 4;  
   V ^% trhV = hV1;  // creates tracking reference to boxed type handle  
   Console::WriteLine("Original V: {0}, Reference to handle of originally boxed V: {1}", v.i, trhV->i);  
}  
```  
  
 **Output**  
  
  **原始 Hyper\-V:2，跟踪引用的、装箱：1**  
**跟踪引用的、装箱：3**  
**装箱的新副本 v:1**  
**原始 Hyper\-V:4，给最初装箱的 V 句柄的引用：1**   
## 该模板函数采用本机、值或引用参数  
 通过在模板函数签名的跟踪引用，确保函数只能由类型本机参数，CLR 或 CLR 引用值调用。  
  
```  
// tracking_reference_template.cpp  
// compile with: /clr  
using namespace System;  
  
class Temp {  
public:  
   // template functions  
   template<typename T>  
   static int f1(T% tt) {   // works for object in any location  
      Console::WriteLine("T %");  
      return 0;  
   }  
  
   template<typename T>  
   static int f2(T& rt) {   // won't work for object on the gc heap  
      Console::WriteLine("T &");  
      return 1;  
   }  
};  
  
// Class Defintions  
ref struct R {  
   int i;  
};  
  
int main() {  
   R ^hr = gcnew R;  
   int i = 1;  
  
   Temp::f1(i); // ok  
   Temp::f1(hr->i); // ok  
   Temp::f2(i); // ok  
  
   // error can't track object on gc heap with a native reference  
   // Temp::f2(hr->i);   
}  
```  
  
 **Output**  
  
  **% T**  
**% T**  
**T &**   
## 请参阅  
 [% \(跟踪引用\)](../windows/tracking-reference-operator-cpp-component-extensions.md)