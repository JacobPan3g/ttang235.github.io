---
layout: post
title: 想在Windows下用Linux的命令？
categories: utility
---
下面是一些软件包：

* [http://unxutils.sourceforge.net/](http://unxutils.sourceforge.net/)
* [http://gnuwin32.sourceforge.net/packages/util-linux-ng.htm](http://gnuwin32.sourceforge.net/packages/util-linux-ng.htm)
* [http://www.cyberciti.biz/faq/unix-command-line-utilities-for-windows/](http://www.cyberciti.biz/faq/unix-command-line-utilities-for-windows/)

我试着实现了两个简单的、常用的命令：head和lc

下面这段代码实现了一个简单的head命令(head.c)
{% highlight c %}
#include <stdio.h>
int main(int argc, const char *argv[])
{
	FILE *fp;
	printf("usage: head n filename, or head filename\n");
	int total = 10;
	if (argc == 3) {
		sscanf(argv[1], "%d", &total);
		fp = fopen(argv[2], "r");
	} else {
		fp = fopen(argv[1], "r");
	}
	if (fp == NULL) {
		printf("error opening file\n");
		return 0;
	}
	char ch;
	unsigned int cnt = 0;
	while ((ch = fgetc(fp)) != EOF) {
		putchar(ch);
		if (ch == '\n') {
			cnt++;
			if (cnt >= total) {
				break;
			}
		}
	}
	fclose(fp);
	return 0;
}
{% endhighlight %}

下面的代码实现了简单的统计文本文件的行数的功能(lc.c)

```c
#include <stdio.h>
int main(int argc, const char *argv[])
{
	FILE *fp;
	if ((fp = fopen(argv[1], "r")) == NULL) {
		printf("error opening file\n");
		return 0;
	}
	char ch;
	unsigned int cnt = 0;
	while ((ch = fgetc(fp)) != EOF) {
		if (ch == '\n') {
			cnt++;
		}
	}
	printf("%u lines\n", cnt);
	return 0;
}
```

编译成exe，然后加到PATH变量里，就可以用了

By the way, linux的mv基本上可以用cmd的move代替，另外，可以为dir定义别名为ls
