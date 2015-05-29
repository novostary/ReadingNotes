# Algorithms, Part I #
## Week 2-0 Stacks and Queues ##
Stacks的两种实现方式：链表和数组。

链表需要额外空间，而数组需要调整大小，这时涉及到复制操作。当overflow时，直接对数组大小进行翻倍，与之类似，当当前大小仅仅为数组大小的1/4时，对数组大小进行减半。

对于Stacks的设计要考虑范型，看看JDK是怎么实现的？

	package java.util;
	public
	class Stack<E> extends Vector<E> { }
	public E push(E item) {
        addElement(item);

        return item;
    }
	public synchronized E pop() {
        E       obj;
        int     len = size();

        obj = peek();
        removeElementAt(len - 1);

        return obj;
    }
	public synchronized E peek() {
        int     len = size();

        if (len == 0)
            throw new EmptyStackException();
        return elementAt(len - 1);
    }
	public synchronized int search(Object o) {
        int i = lastIndexOf(o);

        if (i >= 0) {
            return size() - i;
        }
        return -1;
    }
	/** use serialVersionUID from JDK 1.0.2 for interoperability */
    private static final long serialVersionUID = 1224463164541339165L;
	