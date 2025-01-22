---
title: "[CS Fundamentals] Managing Deadlock in Operating Systems: Prevention and Detection Techniques"
seoTitle: "[CS Fundamentals] Managing Deadlock in Operating Systems"
seoDescription: "Deadlock is a situation in which two or more processes are unable to proceed because each is waiting for the other(s) to release resources, creating a cycle"
datePublished: Wed Jan 22 2025 14:35:20 GMT+0000 (Coordinated Universal Time)
cuid: cm680afft000109lh2fin82yv
slug: deadlock
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1737553547849/e9c7f15f-909b-4cbf-b82a-4e6303e0163c.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1737555159489/9c079319-77d4-4c97-bdd8-2c9add47373a.webp
tags: operating-system, computer-science, fundamentals, deadlock, cs-fundamentals

---

---

## Definition & When it Happens

Deadlock is a situation in which two or more processes are unable to proceed because each is waiting for the other(s) to release resources, creating a cycle of dependency. In real-life, deadlock kinda seems like this situatoin:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737554139436/df6110b2-6907-4eb5-895e-c42a6e151d29.jpeg align="center")

Multiple processes might need the same resource. Let’s say there are Process A, Process B, Resource A and Resource B.

* Process A holds Resource B, and needs Resource A
    
* Process B holds Resource A, and needs Resource B
    

Neither can proceed because Process A is holding the resource that process B needs, and Process B is also holding the resource that process A needs.

Each is waiting on the other to release the resource it needs, resulting in a deadlock.

---

## 4 Key Conditions That Cause Deadlock (Coffman Conditions)

We call these four conditions “Coffman Conditions” in computer science.

1. **Mutual Exclusion**
    
    * Only one process can use the resource at a time.
        
2. **Hold and Wait**
    
    * There must be a process that is holding at least one resource and waiting to acquire additional resources held by other processes.
        
3. **No Preemption**
    
    * Resources that are assigned to a process cannot be forcibly taken away.
        
4. **Circular Wait**
    
    * A set of processes are waiting for resources in such a way that there is a circular chain.
        
    * This diagram explains the circular wait situation.
        

![순환 대기 예](https://media.geeksforgeeks.org/wp-content/uploads/20241003170604/Screenshot-2024-10-03-170601.png align="center")

If **at least one** of these four conditions is not satisifed, the deadlock won’t happen.

---

## How to Handle Deadlock

1. **Prevention**
    
    * It is important to design a system in a such way that those conditions do not occur.
        
    * Eliminate one of Coffman conditions (High cost).
        
        * For example, we can have multiple processes sharing the same resource, which solves mutual exclusion.
            
2. **Avoidance**
    
    1. **Banker’s Alogorithm**
        
        * It is inspired by the way a bank might manage loan requests to avoid bankruptcy.
            
        * When a process requests a resource, check if the system remains in a safe state after allocating the resource.
            
            * A system is in a safe state if it does not cause a deadlock and if there is a sequence of proccesses that can eventually finish, and is able to allow the next sequence to proceed.
                
    2. **Resource-Allocation Graph (RAG) Algorithm**
        
        * A graphical method for modeling resource allocation and detecting deadlock in a system.
            
3. Detection
    
    1. You can detect a deadlock situation using resource-allocation graph (RAG) algorithm.
        
    2. When resources are requested, use a detection algorithm and see if an overhead occurs.
        

---

## **Reference**

[https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Operating%20System/DeadLock.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Operating%20System/DeadLock.md)