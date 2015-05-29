# matplotlib #

[matplotlib](http://matplotlib.org/downloads.html)

[IPython 3.0](https://github.com/ipython/ipython/releases)

	>>> import matplotlib.pyplot as plt
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	  File "C:\Python27\lib\site-packages\matplotlib\__init__.py", line 105, in <mod
	ule>
	    import six
	ImportError: No module named six

[Python安装时import matplotlib.pyplot as plt报错](http://blog.csdn.net/yang6464158/article/details/18546871)

[scipy](https://pypi.python.org/packages/source/s/scipy/scipy-0.15.1.zip#md5=0bd8aa1133118abc77d0d69cc2777ef3)

[NumPy](http://www.numpy.org/) [NumPy](http://www.scipy.org/scipylib/download.html)

[pyparsing](http://pyparsing.wikispaces.com/Download+and+Installation)

[python使用matplotlib绘图 -- barChart](http://www.cnblogs.com/qianlifeng/archive/2012/02/13/2350086.html)

[Matplotlib 教程](http://liam0205.me/2014/09/11/matplotlib-tutorial-zh-cn/)

[Python-Matplotlib安装及简单使用](http://www.open-open.com/lib/view/open1393488232380.html)

	from pylab import *
	x = np.linspace(5, 60, 12, endpoint = True)
	ours_keygen = [0.1821, 0.32745, 0.47195, 0.6182, 0.7663, 0.9162, 1.06125, 1.20725, 1.35035, 1.494, 1.63985, 1.7804]
	rw13_keygen = [0.1662, 0.30995, 0.4556, 0.5996, 0.7465, 0.89385, 1.0387, 1.183, 1.3248, 1.46955, 1.6155, 1.75975]
	# 设置横轴的上下限
	xlim(0, 60)
	
	# 设置横轴记号
	xticks(np.linspace(0, 60, 13, endpoint=True))
	
	# 设置纵轴的上下限
	ylim(-1.0,1.0)
	
	# 设置纵轴记号
	yticks(np.linspace(-1,1,5,endpoint=True))

	plot(X, ours, linewidth=2.5, linestyle="-", label="Ours")
	scatter([t,],[np.cos(t),], 50, color ='blue')
	plot(X, rw13, linewidth=2.5, linestyle="-", label="RW'13")
	legend(loc='upper left')