# NGINX配置文件

在后续教程中，如无意外，操作的文件是`/usr/local/nginx/conf/nginx.conf`。

## NGINX配置文件结构

Nginx 由配置文件中指定的指令控制的模块组成。指令分为简单指令（simple directives）和块指令（block directives）。一个简单指令由名称和参数组成，由空格分隔，并以分号（英文分号）结束。块指令具有与简单指令相同的结构，但是它以一组由大括号({和})包围的附加指令结束，而不是以分号结束。如果一个块指令可以在大括号内包含其他指令，则称之为context（例如：events、http、server和location）。

NGINX的配置文件大致类似于：

```nginx
...
events {
    ...
}
mail {
    ...
}
stream {
    ...
}
http {
    server {
        ...
            location ... {
            	...
			}
	}
}
```