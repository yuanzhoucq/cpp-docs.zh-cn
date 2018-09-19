---
title: lock::acquire |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock::acquire
- acquire
- msclr.lock.acquire
- msclr::lock::acquire
- lock.acquire
dev_langs:
- C++
helpviewer_keywords:
- acquire method
ms.assetid: c214274e-7519-4739-82aa-91b04a32d3f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8c0b89b635ec0f0487027d5a90e43c57c39cde34
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042008"
---
# <a name="lockacquire"></a>lock::acquire
获取对象后，可以选择等待下去，为指定的量的时间，或者根本不获取锁的锁。  
  
## <a name="syntax"></a>语法  
  
```  
void acquire();  
void acquire(  
   int _timeout  
);  
void acquire(  
   System::TimeSpan _timeout  
);  
```  
  
#### <a name="parameters"></a>参数  
*超时) (_t*<br/>
超时值以毫秒为单位或作为<xref:System.TimeSpan>。  
  
## <a name="exceptions"></a>异常  
 引发<xref:System.ApplicationException>如果获取锁超时前不会发生。  
  
## <a name="remarks"></a>备注  
 如果未提供超时值，默认超时值是<xref:System.Threading.Timeout.Infinite>。  
  
 如果已获取锁，则此函数没有任何影响。  
  
## <a name="example"></a>示例  
 此示例跨多个线程使用单个类的实例。  类自身上使用锁来确保对其内部数据的访问是为每个线程保持一致。  主应用程序线程的类的同一实例上使用锁来定期检查以查看任何工作线程仍存在，并等待，直到所有工作线程退出已完成其任务。  
  
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
  
```Output  
In thread 3, Counter = 0  
In thread 3, Counter = 10  
In thread 5, Counter = 0  
In thread 5, Counter = 10  
In thread 7, Counter = 0  
In thread 7, Counter = 10  
In thread 4, Counter = 0  
In thread 4, Counter = 10  
In thread 6, Counter = 0  
In thread 6, Counter = 10  
All threads completed.  
```  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>请参阅  
 [锁定成员](../dotnet/lock-members.md)   
 [lock::try_acquire](../dotnet/lock-try-acquire.md)