---
title: "lock::is_locked | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "is_locked"
  - "msclr::lock::is_locked"
  - "lock::is_locked"
  - "msclr::lock.is_locked"
  - "lock.is_locked"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock::is_locked"
ms.assetid: d888827c-8052-47c6-87a2-8c42f60a688d
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# lock::is_locked
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示是否持有锁。  
  
## 语法  
  
```  
bool is_locked();  
```  
  
## 返回值  
 `true`，如果锁保留，则为 `false`。  
  
## 示例  
 此示例使用类的一个实例在多个线程中。类使用自身上的锁将确保对其内部数据的访问权限。每个线程都是一致的。主应用程序线程使用类的同一实例的锁定定期检查任何辅助线程是否仍然存在，并且等待，直到退出所有辅助线程完成它们的任务。  
  
```  
// msl_lock_is_locked.cpp  
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
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't  
      if (l.is_locked()) { // check if we got the lock  
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
**在线程 4，计数器为 0**  
**在线程 4，计数器为 10**  
**在线程 7，计数器为 0**  
**在线程 7，计数器为 10**  
**在线程 6，计数器为 0**  
**在线程 6，计数器为 10**  
**所有线程完成。**   
## 要求  
 **头文件** \<msclr \\ lock.h\>  
  
 **命名空间** msclr  
  
## 请参阅  
 [锁定成员](../dotnet/lock-members.md)   
 [lock::operator bool](../dotnet/lock-operator-bool.md)