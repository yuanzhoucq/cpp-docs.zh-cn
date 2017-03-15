---
title: "lock::~lock | Microsoft Docs"
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
  - "~lock"
  - "msclr.lock.~lock"
  - "lock.~lock"
  - "msclr::lock::~lock"
  - "lock::~lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~lock 析构函数"
ms.assetid: 55fa9f6c-d7a6-48ef-9236-ee03342c1d20
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock::~lock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重构 `lock` 对象。  
  
## 语法  
  
```  
~lock();  
```  
  
## 备注  
 析构函数调用 [lock::release](../dotnet/lock-release.md)。  
  
## 示例  
 此示例使用在多个线程中类的一个实例。类使用自身上的锁确保每个线程对其内部数据的访问权限都是一致的。主应用程序线程使用类的同一实例的锁定定期检查任何辅助线程是否仍然存在，并且等待，直到退出所有辅助线程完成它们的任务。  
  
```  
// msl_lock_dtor.cpp  
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
  
  **在线程 3，Counter \= 0**  
**在线程 3，Counter \= 10**  
**在线程 5，Counter \= 0**  
**在线程 5 ，Counter \= 10**  
**在线程 7，Counter \= 0**  
**在线程 7，Counter \= 10**  
**在线程 4，Counter \= 0**  
**在线程 4，Counter \= 10**  
**在线程 6，Counter \= 0**  
**在线程 6，Counter \= 10**  
**所有线程完成。**   
## 要求  
 **Header file** \<msclr\\lock.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [锁定成员](../dotnet/lock-members.md)   
 [lock::lock](../dotnet/lock-lock.md)