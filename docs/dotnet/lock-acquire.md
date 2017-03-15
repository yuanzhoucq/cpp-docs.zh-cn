---
title: "lock::acquire | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "lock::acquire"
  - "acquire"
  - "msclr.lock.acquire"
  - "msclr::lock::acquire"
  - "lock.acquire"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acquire 方法"
ms.assetid: c214274e-7519-4739-82aa-91b04a32d3f9
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# lock::acquire
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取一个锁定对象，可以选择是始终不等待获取锁，经过指定的时间的或。  
  
## 语法  
  
```  
void acquire();  
void acquire(  
   int _timeout  
);  
void acquire(  
   System::TimeSpan _timeout  
);  
```  
  
#### 参数  
 `_timeout`  
 超时值 \(以毫秒为或 <xref:System.TimeSpan>。  
  
## 异常  
 如果锁获取不会超时之前，会引发 <xref:System.ApplicationException>。  
  
## 备注  
 如果未提供超时值，则默认超时值为 <xref:System.Threading.Timeout.Infinite>。  
  
 如果锁已获得的，则该函数不执行任何操作。  
  
## 示例  
 此示例使用类的一个实例在多个线程中。类使用自身上的锁将确保对其内部数据的访问权限。每个线程都是一致的。主应用程序线程使用类的同一实例的锁定定期检查任何辅助线程是否仍然存在，并且等待，直到退出所有辅助线程完成它们的任务。  
  
```  
// msl_lock_acquire.cpp  
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
 [lock::try\_acquire](../dotnet/lock-try-acquire.md)