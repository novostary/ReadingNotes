/etc/hosts

[查看python是32位还是64位](http://blog.csdn.net/liuguobo/article/details/19118277)

	import struct
	struct.calcsize("P")

如果是4，说明是32位的；如果是其他的是，64位的。struct.calcsize用于计算格式字符串所对应的结果长度。