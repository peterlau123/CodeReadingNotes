### 6.1




### 6.2



### 6.3


### 6.4


### 6.5



### 6.6

```c++
//错误的pop_head实现方式
std::unique_ptr<node> threadsafe_queue::pop_head()
    {
        node* const old_tail=get_tail();
        std::lock_guard<std::mutex> head_lock(head_mutex);
        if(head.get()==old_tail)
        {
            return nullptr;
        }
        std::unique_ptr<node> const old_head=std::move(head);
        head=std::move(old_head->next);
        return old_head;
    }
```
假设有A和B两个线程，A和B都会调用try_pop方法，A先于B调用
当A进入pop_head后，由于head_mutex的原因，那么B会卡在head_lock的地方不会在往下进行
A实际上会pop当前头部的元素，若在这个过程中有其他线程获取了tail的mutex并改动了tail，那么B拿到old_tail就不是原来的tail了
比如C线程此时调用push方法，就会修改tail

此时B再去调用head.get()==old_tail 就不会相等，从而进行后面的操作导致head指向了超出queue边界的地方

```mermaid
graph LR
head-->last_node
last_node-->dummy_node
tail-->dummy_node
```
A和B线程调用pop_head的时候，queue的状态如上图

```mermaid
graph LR
head-->dummy_node
tail-->dummy_node
```
A线程执行完后，B准备执行comparison时的queue状态
一旦此时old_tail的值发生改变，那么comparison的不成立，后续操作会导致head指向dummy_node之后

