## Mat::ptr(y)
作用：返回 Mat 对象第 y 行的指针

源码及解析：
```C++
inline
const uchar* Mat::ptr(int y) const
{
    CV_DbgAssert( y == 0 || (data && dims >= 1 && (unsigned)y < (unsigned)size.p[0]) );
    return data + step.p[0] * y;
}

/*
data是数据的开头地址。
step是一个指向整个矩阵中每行元素所占用字节数的数组。
对于二维矩阵来说，它是一个包含两个元素的数组，第一个元素表示行步长，第二个元素表示列步长。
例如，Mat M(3,3,CV_8UC3, Scalar(0,0,255))
那么，M.step[0] = 9，M.step[1] = 3

为什么结果如此呢？
（1）数据类型是CV_8UC3，那么每个元素占1个字节
（2）M.step[1] = 3 是因为每个元素都三个通道
（3）M.step[0] = 9 是因为每行有3个元素
*/
```
