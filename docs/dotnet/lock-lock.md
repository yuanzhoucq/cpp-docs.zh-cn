---
title: "lock::lock | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "lock::lock"
  - "lock.lock"
  - "msclr.lock.lock"
  - "msclr::lock::lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock 构造函数"
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock::lock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造 `lock` 对象，可以选择等待获取锁不总是，在经过指定的时间。  
  
## 语法  
  
```  
template<class T> lock(  
   T ^ _object  
);  
template<class T> lock(  
   T ^ _object,  
   int _timeout  
);  
template<class T> lock(  
   T ^ _object,  
   System::TimeSpan _timeout  
);  
template<class T> lock(  
   T ^ _object,  
   lock_later  
);  
```  
  
#### 参数  
 `_object`  
 要锁定的对象。  
  
 `_timeout`  
 超时值 \(以毫秒为或 <xref:System.TimeSpan>。  
  
## 异常  
 如果锁获取不会超时之前，会引发 <xref:System.ApplicationException>。  
  
## 备注  
 构造函数的第三窗体尝试获取对 `_object` 的锁在指定的超时时间 \(或 <xref:System.Threading.Timeout.Infinite> 中，如果未在中指定\)。  
  
 构造函数的第四窗体不获取对 `_object`的锁。  `lock_later` 是 [lock\_when 枚举](../dotnet/lock-when-enum.md)的成员。  使用 [lock::acquire](../dotnet/lock-acquire.md) 或 [lock::try\_acquire](../dotnet/lock-try-acquire.md) 在这种情况下获取锁。  
  
 当调用析构函数，锁将自动释放。  
  
 `_object` 不能为 <xref:System.Threading.ReaderWriterLock>。如果它为，编译器错误。  
  
## 示例  
 此示例使用类的一个实例在多个线程中。类使用自身上的锁将确保对其内部数据的访问权限。每个线程都是一致的。主应用程序线程使用类的同一实例的锁定定期检查任何辅助线程是否仍然存在，并且等待，直到退出所有辅助线程完成它们的任务。  
  
```  
// msl_lock_lock.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
ref class CounterClass {  
private:  
   int Counter;     
  
public:  
   property int ThreadCount;  
  
   // function called by multiple threads, use lock to keep Counter consistent  
   // for each thread  
   void UseCounter() {  
      try {  
         lock l(this); // wait infinitely  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         for (int i = 0; i < 10; i++) {  
            Counter++;  
            Thread::Sleep(10);  
         }  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         Counter = 0;  
         // lock is automatically released when it goes out of scope and its destructor is called  
      }  
      catch (...) {  
         Console::WriteLine("Couldn't acquire lock!");  
      }  
  
      ThreadCount--;  
   }  
};  
  
int main() {  
   // create a few threads to contend for access to the shared data  
   CounterClass^ cc = gcnew CounterClass;  
   array<Thread^>^ tarr = gcnew array<Thread^>(5);  
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);  
   for (int i = 0; i < tarr->Length; i++) {  
      tarr[i] = gcnew Thread(startDelegate);  
      cc->ThreadCount++;  
      tarr[i]->Start();  
   }  
  
   // keep our main thread alive until all worker threads have completed  
   lock l(cc, lock_later); // don't lock now, just create the object  
   while (true) {  
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't  
         if (0 == cc->ThreadCount) {  
            Console::WriteLine("All threads completed.");  
            break; // all threads are gone, exit while  
         }  
         else {  
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);  
            l.release(); // some threads exist, let them do their work  
         }  
      }  
   }  
}  
```  
  
  **在线程 3，计数器为 0**  
**在线程 3，计数器为 10**  
**在线程 5，计数器为 0**  
**在线程 5，计数器为 10**  
**在线程 7，计数器为 0**  
**在线程 7，计数器为 10**  
**在线程 4，计数器为 0**  
**在线程 4，计数器为 10**  
**在线程 6，计数器为 0**  
**在线程 6，计数器为 10**  
**所有线程完成。**   
## 要求  
 **头文件** \<msclr \\ lock.h\>  
  
 **命名空间** msclr  
  
## 请参阅  
 [锁定成员](../dotnet/lock-members.md)   
 [lock::~lock](../dotnet/lock-tilde-lock.md)   
 [lock::acquire](../dotnet/lock-acquire.md)   
 [lock::try\_acquire](../dotnet/lock-try-acquire.md)