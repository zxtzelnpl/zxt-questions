### 关于浏览器
1. 浏览器多进程架构，其开启的渲染进程是有上限的，超过上限，浏览器会把相同站的tab的渲染进程合并，那么如果没有相同站点，且开启的tab超过进程上限了，浏览器如何操作。
2. 浏览器渲染进程下compositor线程将lay层分片后发送给raster线程，raster将tile处理成相关信息存进GPU，这些信息称为为draw quwd，compositor线程再将draw quwd合成为compositor frame